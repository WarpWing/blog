---
title: How Terraform's Transition from Open Source to Business Source changed FOSS Norms
published: 2024-10-01
description: Discover how Terraform's move to BSL was a game changer for developers
image: https://external-preview.redd.it/terraform-is-no-longer-open-source-v0-4AVX4XaoWk1coa6M71TABOq8n2LvgfUrN554IyGUohw.jpg?width=1080&crop=smart&auto=webp&s=e79658152a4d4309d9b2669b4f97d31ca06cbede
tags: [COMP390, Law, Cloud, DevOps, Licensing]
category: COMP390
draft: false
---

> Cover image source: [Source](https://github.com/hashicorp/terraform/commit/b145fbcaadf0fa7d0e7040eac641d9aef2a26433)

:::tip
All images linked have been verified to be under Fair Use and allowed to be utilized in this blog.
:::

## Introduction

Terraform is an open-source Infrastructure as Code (IaC) tool developed by HashiCorp. It allows users to define and provision infrastructure across various cloud and infrastructure providers like AWS, GCP, and Azure using declarative configuration files, making it easier to automate and manage infrastructure at scale. As a user of Terraform (at the time) for managing AWS test infrastructure and maintaining Kubernetes clusters for open-source projects like SkyCrypt, I was initially concerned about HashiCorp's announcement to transition Terraform from the Mozilla Public License v2.0 (MPL 2.0) to the Business Source License (BSL). This shift raised internal questions about compliance and commercial use, especially for projects like SkyCrypt that receive external funding (Patreon + KoFi). However, after examining HashiCorp's License FAQ, I found some clarity: as long as you don't directly compete with Terraform or offer services that compete with HashiCorp's commercial products, you're generally in the clear. But, the question still remains. What was the reason behind moving from the Mozilla Public License to the Business Source License? How did this impact the surrounding ecosystem around Terraform and it's sister products? 

## Ground Zero: The Shift From MPL v2.0 to BSL v1.1

On August 10, 2023, HashiCorp made a decision that reverberated through the open source community. Armon Dadgar, co-founder and CTO, announced the transition of HashiCorp's popular tools - including Terraform, Vault, Nomad, and others - from the [Mozilla Public License (MPL) v2.0](https://choosealicense.com/licenses/mpl-2.0/) to the [Business Source License (BSL) 1.1](https://www.hashicorp.com/bsl). This move marked the end of these tools' status as fully open source software, a change that would have far-reaching consequences. HashiCorp's justification for this transition centered on concerns about other vendors exploiting their open source model without making substantial contributions. This reasoning isn't unique to HashiCorp; it echoes similar moves made by companies like Elastic, MongoDB, and Redis Labs in recent years. HashiCorp emphasized that they were following a path similar to other respected companies in the industry, including Couchbase, Cockroach Labs, Sentry, and MariaDB (which originally developed the BSL in 2013).

## Mozilla Public License (MPL) v2.0 vs Business Source License (BSL) 1.1

The transition from the Mozilla Public License (MPL) v2.0 to the Business Source License (BSL) 1.1 mostly impacts commercial contributors. The MPL, recognized by the Open Source Initiative (OSI) as a true open source license, allows for free use, modification, and distribution of software for any purpose, including commercial use. It has a weak copyleft nature, requiring modifications to MPL-licensed code to be released under the MPL, but allows linking from code with other licenses. Importantly, the MPL includes an express patent grant from contributors to users and places no restrictions on creating competing products. In contrast, the BSL, originally created by MariaDB in 2013, is not recognized as an open source license by the OSI. While it allows for non-production use and modification, it crucially restricts production use that competes with the licensor's products. This restriction is time-limited, typically expiring after 3-4 years, at which point the software becomes available under a specified open source license. The BSL maintains source code availability, allowing for inspection, modification, and non-competitive use, but unlike the MPL, it does not include an automatic patent grant.

These differences have significant implications for both developers and broader licensing norms in the FOSS ecosystem. While the MPL encourages a fully open contribution model and allows unrestricted commercial use, the BSL may discourage some contributions due to its commercial restrictions. The BSL's design to prevent direct competition using the licensed software stands in stark contrast to the MPL's allowance for the creation of competing products without restriction. Furthermore, the community perception of these licenses differs greatly, with the MPL being widely accepted in the open source community, while the BSL is often viewed as a strict departure from open source principles.

## The FOSS Community's Response: Fiery Disappointment

The announcement of HashiCorp's decision to transition their popular tools from the Mozilla Public License to the Business Source License ignited a huge firestorm within the tech community. This move, which effectively ended the fully open-source status of widely-used tools like Terraform, Vault, and Nomad, was met with strong criticism from various corners of the industry. Many viewed this transition as a betrayal of the core principles that underpin open-source software development, principles that have long been celebrated for fostering innovation, collaboration, and transparency in the tech world.

Among the vocal critics was Joe Duffy, the founder and CEO of Pulumi, a company that competes with HashiCorp in the infrastructure-as-code space. Duffy didn't mince words, characterizing HashiCorp's blog post announcing the change as "disingenuous." His criticism went beyond the license change itself, touching on what he perceived as a longer-term drift away from true open-source values. Duffy pointed to past experiences where attempts to contribute upstream fixes to Terraform providers were met with resistance or indifference from HashiCorp. This, in his view, was indicative of a company that had already begun to distance itself from its open-source roots long before the official license change. His assertion that HashiCorp had "lost their OSS DNA a long time ago" resonated with many in the community who had observed similar patterns.

Adding her voice to the chorus of criticism was Amanda Brock, a prominent figure from OpenUK, an organization dedicated to developing and sustaining UK leadership in Open Technology. Brock's critique centered on what she termed "open washing" - a practice where companies leverage the positive associations of open-source software while gradually moving away from its core principles. Her comments suggested that HashiCorp's decision was driven more by the pressures of generating shareholder value than by a commitment to the open-source community that had played a crucial role in the company's success. This perspective raised important questions about the delicate balance between achieving commercial success and maintaining a genuine commitment to community-driven development.

The disappointment expressed by Duffy and Brock also represented a broader worry within FOSS community about the sustainability of open-source business models in the face of commercial pressures. Many worry that as companies grow and face increasing pressure to monetize their products, the principles of open source may be compromised. Furthermore, this controversy has highlighted the deep emotional and philosophical investment that many in the tech community have in the idea of open-source software. For many developers, contributors, and users, open-source isn't just a licensing model - it's a philosophy that embodies values of transparency, collaboration, and community-driven innovation. 

## The Birth of OpenTofu: A Community-Driven Response

::github{repo="opentofu/opentofu"}

In a direct response to HashiCorp's decision, a coalition of companies and individuals came together to create OpenTofu (initially named OpenTF) under a [manifesto](https://opentofu.org/manifesto/). This community-driven fork of Terraform, led by Omry Hay, co-founder and CTO of env0, aims to preserve the open-source spirit that many felt Terraform was abandoning. Some of OpenTofu's key commitments include adopting a well-known and truly open-source license—[MPL v2.0](https://github.com/opentofu/opentofu/blob/main/LICENSE)—actively welcoming and encouraging community contributions, securing pledges of support from over 100 companies, 10 projects, and 400 individuals (including myself), establishing a steering committee composed of Terraform veterans and active contributors alike, and [joining The Linux Foundation](https://www.linuxfoundation.org/press/announcing-opentofu) with future aspirations to become part of the [Cloud Native Computing Foundation (CNCF)](https://www.cncf.io/).

## My Personal Conclusive Take + Citations

Personally, I understand HashiCorp's position from a business perspective. HashiCorp's shift from MPL to BSL is overall a simple strategic move to protect its commercial interests while still providing source code access. However, this move also raises important questions about the long-term community engagement and contribution model for these projects. The restrictions imposed by BSL may deter some developers and organizations from deeply investing in the ecosystem and can (and has as due to OpenTofu) impact the collaborative spirit that breathes life into these open source projects. However, it's vital to keep nuanced discord about this. As we see evolutions in open source development and long term viability starts playing a bigger role, the tension between commercial interests and open source ideals will always remain a critical point of discussion and debate within the tech community. 

To me, the motive is clear. Companies need to protect their interests to ensure they can continue providing value. However, I can't help but feel a sense of loss for the open-source community. Terraform has been a staple in infrastructure as code, and its open-source nature has been a significant part of its success. However, I'm also proud of the FOSS community for standing up for their values and their strength and resolve is demonstrated through the creation and active maintenance of OpenTofu. It's always good for new entrants to rewrite and fork off existing projects, no matter the motivator because FOSS projects help spur innovation and creativity in solving challenges as a collective.

:::note[Citations]

I've listed below some articles that I've cited. For more context, I would highly recommend you peruse through them!

Dadgar, Armon. “HashiCorp Adopts Business Source License.” HashiCorp. Accessed October 2, 2024. https://www.hashicorp.com/blog/hashicorp-adopts-business-source-license.

Choose a License. “Mozilla Public License 2.0,” September 3, 2024. https://choosealicense.com/licenses/mpl-2.0/.

“Linux Foundation Launches OpenTofu: A New Open Source Alternative to Terraform.” Accessed October 2, 2024. https://www.linuxfoundation.org/press/announcing-opentofu.

HashiCorp. “Business Source License 1.1.” HashiCorp | The Infrastructure Cloud Company. Accessed October 2, 2024. https://www.hashicorp.com/bsl.

Horovits, Dotan. “Terraform Is No Longer Open Source. Is OpenTofu the Successor?” Logz.io, September 21, 2023. https://logz.io/blog/terraform-is-no-longer-open-source-is-opentofu-opentf-the-successor/.

“Manifesto | OpenTofu.” Accessed October 2, 2024. https://opentofu.org/manifesto/.

Proven, Liam. “HashiCorp Changes Its Source Licence to BSL.” Accessed October 2, 2024. https://www.theregister.com/2023/08/11/hashicorp_bsl_licence/.

:::

