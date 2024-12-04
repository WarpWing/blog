---
title: Exploring the Potential of DPUs for Data Centric Infrastructure
published: 2024-11-19
description: Could DPUs change the way we handle data at scale?
image: https://techcommunity.microsoft.com/t5/s/gxcuf89792/images/bS00Mjk4OTAxLUZjY0g1RQ?revision=11
tags: [COMP390, AI, Cloud, Hardware]
category: COMP390
draft: false
---

> Cover image source: [Source](https://techcommunity.microsoft.com/blog/azureinfrastructureblog/enhancing-infrastructure-efficiency-with-azure-boost-dpu/4298901)

:::tip 
All images linked have been verified to be under Fair Use and allowed to be utilized in this blog. 
:::

:::note
This blogpost has been edited on December 4th 2024 at 1:04 AM EST to provide more clarity to the reader on the use case of DPUs.
:::

## Introduction

As the demand for efficient and high-performance cloud infrastructure grows, data centers face increasingly complex challenges. Managing vast quantities of data across networks, ensuring secure transmission, and optimizing workloads have become critical priorities for providers. To address these issues, the **Data Processing Unit (DPU)** has emerged as a transformative technology. With the ability to offload specialized data-centric tasks from traditional processors, DPUs promise to revolutionize the way data is handled in large-scale cloud environments. In this post, I'll do an overview into what DPUs are, why they matter, and their potential to redefine cloud computing.

## What’s a DPU? Why are DPUs Important?

A Data Processing Unit (DPU) is a specialized processor designed to handle tasks related to networking, storage, and security, which are often a source of bottlenecks in traditional server architectures. Unlike Central Processing Units (CPUs), which excel at general-purpose tasks, or Graphics Processing Units (GPUs), which are optimized for computationally intensive operations like AI and machine learning, DPUs are purpose-built to manage data movement and processing. They integrate features such as high-speed Ethernet interfaces, data acceleration engines, and robust encryption modules into a single programmable chip. 

![nvidia-gtc-dpu-bluefield-2x](https://github.com/user-attachments/assets/4814e23c-ef3b-4873-a178-a69326a7467a)

> Source: NVIDIA (Note: It's literally just a SmartNIC with compute power)

The rise of DPUs addresses three critical challenges in modern data center operations: performance bottlenecks, energy consumption, and data security. First, DPUs significantly enhance performance by offloading specific tasks from CPUs. This reduces the strain on traditional processors, enabling data to flow at line rate while freeing up resources for other workloads. Microsoft’s Azure Boost DPU, for instance, promises to run storage workloads at four times the performance of existing systems, all while consuming three times less power. Energy efficiency is a second key driver. With data centers consuming billions of dollars in electricity annually, technologies like DPUs are essential for reducing operational costs and environmental impact. By processing tasks more efficiently, DPUs help hyperscalers like Microsoft and Amazon Web Services lower their carbon footprint while meeting growing demand. Finally, DPUs enhance security by integrating hardware-based encryption and secure key management directly into their architecture. This ensures that sensitive data remains protected without introducing additional latency or complexity.

DPUs usually find their homes in enterprise data centers (not for your average consumer unless you have very large data needs) where they serve as specialized traffic controllers, managing the intense flow of data between storage, networking, and computing resources. This role has become increasingly crucial as organizations process larger amounts of data and run more complex workloads. For instance, in cloud environments, Nvidia's Bluefield DPUs handle tasks such as network packet processing at rates up to 400Gb/s (Not 3rd party tested*), storage acceleration, and real-time encryption, allowing CPUs to focus exclusively on application processing.

# The Case for DPUs: Technical Challenges @ Netflix 

:::note[Technical Vocabulary]
I've provided some technical vocabulary terms just to clarify some of the "jargon" I'm using. Most of this is recall from self study for Cisco Networking Exams + reading "Reverse Engineering For Everyone!" by OxInfection.

- Advanced Vector Extensions (AVX): CPU instructions that process 256 bits (32 bytes) of data in parallel. When these operations don't align with the CPU's 512-bit (64 byte) cache line size, they trigger inefficient read-modify-write operations that consume additional memory bandwidth as mentioned*.
- Large Receive Offload (LRO): Combines multiple incoming packets from the same TCP stream into a single larger packet before passing it to the network stack, reducing CPU overhead by minimizing the number of packets that need to be processed.
- Memory Buffers (mbufs): Kernel data structures in FreeBSD that encapsulate network data for processing through the network stack. Each mbuf contains metadata about the packet and can either store small amounts of data directly or reference larger external storage like memory pages.
- Open Connect Appliance (OCA): Netflix's purpose-built content delivery servers designed to efficiently deliver streaming content at high throughput rates while managing network processing, encryption, and storage operations.
- Pages: 4KB blocks of memory that serve as the fundamental unit of data transfer in the system, used for efficient memory management and data processing.
Receive Side Scaling (RSS): Directs network traffic across multiple CPU cores by hashing packet header information to distribute processing load, enabling efficient parallel packet processing in multi-core systems.
- TCP Large Receive Offload (LRO): Reduces overhead by reassembling incoming network packets into larger buffers and transferring the resulting larger but fewer packets to the network stack of the host.
- TCP Segmentation Offload (TSO): Allows the network interface to split large data segments into appropriately-sized packets, offloading this task from the CPU and reducing processing overhead for high-throughput transmissions.
- TLS Metadata: Additional information required for Transport Layer Security encryption, including headers, authentication tags, and cryptographic parameters, which must be processed alongside the main data stream in encrypted communications.
:::

I recently read a technical blog by Netflix that provides a good example of why Data Processing Units (DPUs) have become essential in modern computing environments. As detailed in Netflix's [technical blog](https://netflixtechblog.com/serving-100-gbps-from-an-open-connect-appliance-cdb51dda3b99), their Open Connect Appliances (OCAs which are just high performance servers specifically designed for delivering streaming video content) face significant performance limitations when handling high-bandwidth content delivery, particularly when serving encrypted traffic at scale. 

One significant problem emerged in their TCP processing pipeline. At high packet rates, the system struggled with TCP Large Receive Offload (LRO) aggregation. Their default LRO implementation could only manage 8 packet aggregations simultaneously, which proved insufficient for servers handling tens of thousands of active TCP connections. This resulted in poor aggregation rates of merely 1.1 packets per aggregation, far below optimal efficiency. In addition, their memory bandwidth constraints created another severe bottleneck. 

As systems approached 58Gbps, CPU utilization increased exponentially despite no apparent processing hotspots. Analysis revealed that encryption operations were consuming excessive memory bandwidth - the ISA-L encryption library was triggering unnecessary read-modify-write operations due to misalignment between AVX instructions (256-bit) and cache line sizes (512-bit). This isn't also mentioning that their network buffer (mbuf) system presented additional challenges on top . At 100Gbps, the system needed to process approximately 12.5 GB/s of 4K pages unencrypted, doubling to 25 GB/s with encryption. This translated to roughly 6.25 million mbufs per second for basic operations, plus an additional 1.6 million mbufs for TLS metadata, totaling 8 million mbufs per second. With each mbuf requiring multiple cache line accesses, this generated approximately 1 GB/s of additional memory traffic just for buffer management.

In short, Netflix had a bottlenecking problem scaling their data and networking infrastructure. This is where DPUs can demonstrate their value through sophisticated handling of network traffic, particularly in high-throughput environments. Consider the typical flow of a network packet through a traditional CPU-based system versus a DPU-enabled architecture. In a conventional system, each packet triggers CPU interrupts, requiring the processor to context switch and manage the entire network stack processing, from TCP/IP handling to application layer delivery. For DPUs (Using NVIDIA's BlueField DPUs as an example)  implement TCP/IP offload engines that can handle packet processing at line rate without CPU intervention. When a packet arrives, the DPU's network processing unit can parse headers, perform checksum verification, and manage TCP stream reassembly entirely in hardware. For a typical 100Gbps network stream, a system must process approximately 148.8 million packets per second (assuming standard 64-byte packets). Traditional CPU architectures struggle with this load, as each packet requires multiple memory accesses and CPU cycles for processing. DPUs address this through specialized packet processing engines that can handle multiple operations in parallel, including RSS (Receive Side Scaling), TSO (TCP Segmentation Offload), and LRO (Large Receive Offload).

Network virtualization presents another layer of complexity that DPUs excel at managing. When implementing VXLAN or Geneve overlays, each packet requires additional processing for encapsulation and decapsulation. DPUs can perform these operations at line rate through dedicated hardware acceleration engines. For example, in a virtualized environment with thousands of concurrent connections, a DPU can maintain separate hardware queues for different virtual networks while managing the associated overhead of overlay networking without impacting the main system performance.

![timeline-description-automatically-generated](https://github.com/user-attachments/assets/bf1f6b34-4eb2-49b0-a65b-09fcdd9dd5a4)

>Source: https://blogs.vmware.com/networkvirtualization/2022/08/announcing-dpu-based-acceleration-for-nsx.html/ (This shows how a DPU would be used in an example env)

The point here is that the efficiency of DPU packet processing becomes particularly apparent in cases like Netflix's content delivery infrastructure. Their systems must handle not just raw throughput, but also encryption and complex TCP session management. A single 100Gbps stream of encrypted traffic requires the DPU to manage approximately 8 million encryption operations per second (rough guess assuming 12.5GB/s on a 16 KB TLS record size, factoring in key management and intergrity checks), while simultaneously handling TCP flow control, congestion management, and packet scheduling. The DPU accomplishes this through dedicated hardware engines that can process these operations in parallel, maintaining line rate performance even under complex workloads. 

## Conclusion + Citations

I think DPUs are interesting and do add some interesting questions in addressing performance, efficiency, and security challenges that have long constrained data centers. Their ability to complement existing CPUs and GPUs positions them as an essential component in the future of computing. I also like the idea of DPUs as a means for offloading massive operations requiring high bandwidth to a separate device (although there is the question of cost to efficiency. We should consider the nuance of if this is "worth it" or just another marketing tool). I will say (and I didn't mention it) of their intergration with Microsoft Azure Integrated Hardware Security Module (HSM) with these new DPUs also calls into questions security. I'm curious to read the in depth system design on how they plan to secure these DPUs, especially as they're at risk of Side-Channel and Fault Injection Attacks. Apple's T2 SoC Chip, if I recall, had a similiar [fault](https://www.wired.com/story/apple-t2-chip-unfixable-flaw-jailbreak-mac/) with the Checkm8 vulnerability in 2020. However, that's just some musings from me. Overall, an interesting SoC system for handling workloads for both enterprise and consumer grade hardware.

:::note[Citations]

I've listed below some articles that I've cited. For more context, I would highly recommend you peruse through them!

Enhancing infrastructure efficiency with azure boost dpu | microsoft community hub. (n.d.). TECHCOMMUNITY.MICROSOFT.COM. Retrieved November 20, 2024, from https://techcommunity.microsoft.com/blog/azureinfrastructureblog/enhancing-infrastructure-efficiency-with-azure-boost-dpu/4298901

Deierling, K. (2020, May 21). What is a dpu? NVIDIA Blog. https://34.214.249.23.nip.io/blog/whats-a-dpu-data-processing-unit/

Blog, N. T. (2017, October 1). Serving 100 gbps from an open connect appliance. Medium. https://netflixtechblog.com/serving-100-gbps-from-an-open-connect-appliance-cdb51dda3b99

Wiggers, K. (2024, November 19). Microsoft to launch new custom chips for data processing, security. TechCrunch. https://techcrunch.com/2024/11/19/new-in-house-chips-round-out-microsofts-portfolio/

:::
