---
title: My Thoughts on The AI Bill (SB 1047)
published: 2024-09-17
description: Why SB 1047 Might Be the Most Important AI Legislation of 2024.
image: https://d1lamhf6l6yk6d.cloudfront.net/uploads/2024/06/SB-1047-Yoast-FB.png
tags: [COMP390, AI, LLM, Law]
category: COMP390
draft: false
---

> Cover image source: [Source](https://a16z.com/sb-1047-what-you-need-to-know-with-anjney-midha/)

# A Personal Preface

First, I would like to explain my motives for being here. If you're a professor at Dickinson College especially you, Professor Braught, you may wish to skip this paragraph unless you'd like to read about my personal ramblings. I've been wanting to write on this blog for a long time but never felt entirely confident about sharing my thoughts publicly, particularly knowing that I might be surrounded by critics and individuals who are undoubtedly smarter than me. However, I've come to realize that I shouldn't let such fears constrain me. It's time to face the critiques of the internet and express my perspectives.

I recently started my sophomore year at Dickinson College, majoring in Political Science with a minor in Computer Science. I'm currently enrolled in COMP390: Free and Open Source Development Practicum, a one credit computer science course under the guidance of Professor Grant Braught. This course is an amalgamation of COMP190 and COMP290, which collectively teach the Unix command line environment, shell scripting, system administration, debugging tools, version control, and elements of web development.

In addition, the course includes mandatory readings and discussions focusing on FOSS and HFOSS philosophy, licensing, communication tools, project and community organization, and software engineering topics related to large scale software development. It's a comprehensive practicum that touches on software development and the current social, legal, and ethical issues facing computing and technology as a whole.

As part of my agreement with Professor Braught, I'm tasked with writing about a current issue that has social, legal, or ethical implications in technology on a weekly basis. Therefore, I've decided to post all of my weekly write-ups on this blog. For Professor Braught, it's more engaging than a simple Markdown file or PDF. For me, it's an opportunity to enhance my writing skills and contribute my thoughts to the vast ocean of the internet. 


# The Great AI Growth Spurt
To provide context, the evolution of artificial intelligence in recent years has been nothing short of a technological sprint. In just a few years, there has been a monumental leap in large language model capabilities. Outputs have evolved from generating incoherent ramblings to producing essays at a high school level. This rapid growth in AI capabilities has left both technologists and policymakers racing to keep up.

In 2019, OpenAI introduced GPT-2, a language model with 1.5 billion parameters. At the time, this was a significant achievement in natural language processing and large language model development. GPT-2 could generate coherent text, summarize content, and even produce simple poetry. The capabilities of GPT-2 sparked conversations about AI's potential and its ethical implications, but the general consensus was that the technology was manageable and its risks, while present, were relatively contained. 

Then came GPT-3 in 2020, and the landscape changed dramatically. Boasting 175 billion parameters (A 100 fold difference in parameters from GPT-2), GPT-3 wasn't just a step forward, it was a giant leap. Suddenly, AI could perform various complex tasks: writing essays, composing music, generating code, and engaging in rudimentary conversations that while was sometimes incoherent and predictable, began to blur the lines between human generated and machine generated content. Teachers started to catch (and sometimes falsely blame) students using ChatGPT for their assignments. Marketing Companies start using AI in their copywriting. Moral and ethic questions about authorship, authenticity, and the potential for misuse started to run rampant across the web.

By the time GPT-4 arrived boasting over 1 trillion parameters, the advancements had accelerated to a point that was exciting yet unsettling. GPT-4 expanded on the capabilities of GPT-3, with enhanced reasoning abilities, improved context understanding, and the introduction of multimodal processing handling both text and images. It could pass professional exams such as the LSAT and MCAT, assist in medical diagnoses, and interpret nuanced human language with unprecedented accuracy (including sarcasm). GPT-4 was a marker that AI has grown more smarter and more versatile, stepping into domains that were once considered exclusively human territory. To put it simply, it's like a child had skipped adolescence and jumped straight into a Ph.D. program.

![bleh](https://wikiteq.com/storage/app/media/uploaded-files/LLM-Parameter-Growth-Over-the-Years-wikiteq.webp)

The meteoric rise of AI capabilities has clearly exposed a gap in technological innovation and regulatory oversight. We've built a high speed train but haven't yet laid down all the tracks and built all of the crossings. It seems that policymakers are outpaced, attempting to draft laws on technologies that have already outpaced existing frameworks. It's clear that regulations needs to be balanced to accomodate AI development while also facilitating healthy growth. However, I would argue that this is why SB 1047 is so important in 2024. It's a nuanced attempt to create a bill that can adequately scale to meet the growth of these massive LLMs and set clear guidelines and regulatory standards.

# SB 1047: An Abstract Overview

In order to analyze SB 1047, we must first understand what it is. California's Senate Bill 1047, officially known as the "Safe and Secure Innovation for Frontier Artificial Intelligence Models Act," is a significant legislative effort aimed at regulating the development and deployment of large scale artificial intelligence (AI) models. The primary goal of this bill is to prevent these advanced AI systems from causing "critical harms," such as facilitating the creation of weapons of mass destruction or enabling massive cyberattacks that could disrupt society. SB 1047 mandates that developers of these powerful AI models implement comprehensive safety protocols, submit to annual third party audits, and maintain the capability to enact a full shutdown of AI systems if necessary. Specifically, the bill targets AI models that cost over $100 million to train or utilize computational resources exceeding 10^26 floating point operations during training—a staggering amount of computing power. Developers of such models are required to establish a written safety and security protocol that includes detailed risk management procedures, safeguards against unauthorized access, and strategies to prevent the AI from causing critical harm.

To ensure compliance, SB 1047 establishes a new regulatory body, the Board of Frontier Models, which would be housed within the California Government Operations Agency. This nine member board would consist of experts from various fields, including the AI industry, the open source community, academia, and specialists in cybersecurity and weapons of mass destruction. Members are appointed by the Governor and the Legislature. The board's responsibilities include overseeing adherence to the bill's requirements, issuing guidance to AI developers, and advising the state's Attorney General on potential violations. 

# The Meat and Tensor Potato Chips behind SB 1047

While it's hard to condense all of SB 1047 accurately, I've written short paragraphs about what I believe to be the core subtopics of SB 1047. These shouldn't be taken as objective core facets, but they are certainly good stepping stones.

## Safety Protocol Requirements

Developers of powerful AI models are required to take proactive safety measures under SB 1047. They must implement robust cybersecurity protections to guard against hacking, misuse, or unauthorized access, particularly from sophisticated threats. Developers are also mandated to create a comprehensive written safety and security protocol that outlines how they will manage risks throughout the AI's life cycle. This plan should include procedures for risk assessment, mitigation strategies, and incident response plans. Furthermore, senior personnel must be designated to ensure that these safety measures are followed and updated regularly. The intention is to embed safety into the AI development process from the outset, ensuring that potential risks are managed effectively.

## Annual Audits and Reporting

To maintain transparency and accountability, SB 1047 stipulates that developers must undergo annual audits conducted by independent third parties. These audits are designed to verify compliance with the established safety protocols. The resulting audit reports must be submitted to the California Attorney General and made publicly available, with sensitive information redacted to protect proprietary data. In addition to regular audits, developers are required to report any "AI safety incidents" to the Attorney General within 72 hours of discovery. An AI safety incident is defined as any event that significantly increases the risk of critical harm, such as a security breach or an AI behaving dangerously. This prompt reporting ensures that oversight authorities can take immediate action to address potential threats.

## Penalties for Non-Compliance

SB 1047 imposes substantial penalties on developers who fail to comply with its provisions. The California Attorney General has the authority to initiate civil actions against non compliant developers. Financial penalties are significant: up to 10% of the AI model's training cost for a first violation and up to 30% for subsequent violations. For example, if an AI model cost 100 million to train, fines could reach 10 million or 30 million, respectively. Beyond fines, legal actions could include injunctions that halt the development or deployment of the AI model until compliance issues are resolved. These stringent penalties are designed to ensure that developers take their responsibilities seriously and adhere strictly to safety requirements.

## Whistleblower Protections

To encourage ethical practices and the reporting of potential risks, SB 1047 includes strong protections for employees. Developers are prohibited from retaliating against employees who disclose information about unsafe AI practices to authorities such as the Attorney General or the Labor Commissioner. This includes protections for employees who report violations of the bill or express concerns about potential critical harms. Employees are allowed to report concerns anonymously, providing a safe channel for whistleblowers who might fear repercussions. Additionally, developers must inform all employees—including contractors and subcontractors—about their rights under the bill and the procedures for reporting concerns. 

## Regulation of Computing Power

Recognizing that advanced AI models require significant computational resources, SB 1047 addresses the role of computing infrastructure providers. Companies offering large scale computing power (think AWS, Azure, Google Cloud, Oracle) must implement policies to verify the identities of their customers and assess the intended use of the computational resources. This KYC approach helps prevent developers from bypassing regulations by outsourcing AI training to third party computing services without proper oversight. Providers are also required to maintain records of customers and their activities, enhancing accountability throughout the AI development chain. This measure ensures that all parties involved in the creation of powerful AI systems are subject to appropriate scrutiny.

## Scope and Applicability

The bill specifies who is required to comply with its provisions to ensure comprehensive coverage. SB 1047 applies to any developer operating within California or providing AI models for use within the state, even if the model was trained elsewhere. By doing so, it closes potential loopholes where developers might attempt to avoid regulation by conducting activities outside the state but distributing or deploying AI models within California. The legislation focuses on large scale AI models—those costing over $100 million to train or utilizing enormous computing power—so that smaller developers and startups are not unduly burdened. It also extends to open source models if significant additional training or modifications are made. This comprehensive scope ensures that the regulations address AI systems with the greatest potential impact.

## Adjustments for Inflation and Technological Advances

To maintain the bill's relevance over time, SB 1047 includes provisions for adjustments due to inflation and technological progress. Financial thresholds, such as the $100 million training cost, are subject to annual adjustments based on the California Consumer Price Index. This accounts for economic changes and maintains the real value of the thresholds. Additionally, the Government Operations Agency is authorized to update computational power metrics and other technical thresholds. 

# Conclusive Musings + Citations

Whew! That was a lot to digest. I've done a Herculean amount of reading to write this blog post, and I must admit, it's been quite the journey pruning through several articles and .gov websites. SB 1047 is an ambitious piece of legislation that tackles some of the most pressing concerns in AI development today and that comes in walls of text and tape! I would posit that while the bill introduces significant regulatory hurdles that could potentially hinder AI development especially for startups and smaller companies, I'm optimistic that it's a step in the right direction. It's an interesting start toward balancing innovation with responsibility. By proactively addressing potential risks associated with advanced AI models, SB 1047 can foster an environment where technology continues to advance safely, which is a future I look forward too! 

![AdobeStock_214469252](https://github.com/user-attachments/assets/a80472fb-787d-4bed-8085-3d34a88f80b9)


Yes, implementing these measures might feel like Sisyphus rolling a ball up the early stage curve of the Gartner Hype Cycle but if it helps prevent critical harms and ensures that AI technologies benefit society as a whole, then perhaps the effort is well worth it. After all, in the grand scheme of things, it's better to wrestle with complex policy now than to grapple with unintended consequences later. I would say that SB 1047 could be the catalyst that prompts developers, policymakers, and society to collaborate more closely, ensuring that the AI stays on the right track. That's quite optimistic for me to say and I wouldn't blame you for labeling me as a dreamer. However, there is also the question of hindering progression and development on AI. There are some parts of me that also slightly resent SB 1047 for it's hinderance of technological progression through bureaucratic red tape. However, I'd rather err on the side of technological It's not the best bill but I hope it becomes a stepping stone for greater, more nuanced regulation. Personally, I believe that while it does require developers and companies alike to work under strict guidelines, in terms of safety, it's a step in the right direction.


:::note[Citations]

I've listed below some articles that I've cited in understanding SB 1047. For more context, I would highly recommend you peruse through them!

DLA Piper. “California’s SB-1047: Understanding the Safe and Secure Innovation for Frontier Artificial Intelligence Act.” Accessed September 17, 2024. https://www.dlapiper.com/en/insights/publications/2024/02/californias-sb-1047.

Midha, Anjney. “What You Need to Know About SB 1047: A Q&A with Anjney Midha.” Andreessen Horowitz, June 19, 2024. https://a16z.com/sb-1047-what-you-need-to-know-with-anjney-midha/.

SB 1047: Safe and Secure Innovation for Frontier Artificial Intelligence Models Act. | Digital Democracy.” Accessed September 17, 2024. https://digitaldemocracy.calmatters.org/bills/ca_202320240sb1047.

Zeff, Maxwell. “California Weakens Bill to Prevent AI Disasters before Final Vote, Taking Advice from Anthropic.” TechCrunch, August 15, 2024. https://techcrunch.com/2024/08/15/california-weakens-bill-to-prevent-ai-disasters-before-final-vote-taking-advice-from-anthropic/.

Zeff, Maxwell. “California’s Legislature Just Passed AI Bill SB 1047; Here’s Why Some Hope the Governor Won’t Sign It.” TechCrunch, August 30, 2024. https://techcrunch.com/2024/08/30/california-ai-bill-sb-1047-aims-to-prevent-ai-disasters-but-silicon-valley-warns-it-will-cause-one/.

:::











