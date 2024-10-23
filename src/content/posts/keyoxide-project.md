---
title: Verifying Digital Identities in a Decentralized Landscape with Keyoxide
published: 2024-10-22
description: Discover how Keyoxide is changing the way we verify.
image: https://github.com/user-attachments/assets/35b21fff-48b7-4b71-9df9-3d0733bf3d0a
tags: [COMP390, FOSS, Fediverse, Decentralization]
category: COMP390
draft: false
---

> Cover image source: [Source](https://vijayprema.com/actually-get-verified-online-identity-proofs/)

:::tip
All images linked have been verified to be under Fair Use and allowed to be utilized in this blog.
:::

# Introduction 
In today's vast digital world, verifying your digital identity is more important than ever. Every day, we navigate through the seas of online platforms, sharing information and building our digital presence. From confirming your identity on social media to validating the sender of an email, **trust** forms the basis of all our interactions online. But our current methods of managing these identities are broken. They are often confusing, fragmented, and depend heavily on centralized authorities that may not always act in our best interest (take Twitter's Blue Checkmark System as an example).

Enter Keyoxide! Keyoxide is an open and decentralized identity verification tool that changes the way we prove who we are online. Unlike traditional systems of authentication, Keyoxide offers a way to manage digital identities that is simple, secure, and respects your privacy. Instead of relying on a company (SSO as an example) to validate your identity or waiting for permission to verify your own online presence, Keyoxide puts the control back in your hands.

With Keyoxide, you can link your online profiles across different platforms, creating a unified identity without sacrificing privacy or autonomy. Keyoxide is built on transparency in that anyone can verify your identity claims, and it removes the need for a central authority, ensuring that you remain in control. Imagine an internet where your identity is not something you rent from a corporation but something you own entirely. That's the promise of Keyoxide: a decentralized, verifiable digital identity that you have complete control over

# What exactly does Keyoxide do? How does it tackle the identity problem?
Keyoxide is a decentralized service designed to verify your digital identity across various platforms by leveraging cryptographic keys, such as OpenPGP keys. It allows you to link different parts of your online presence (like social media accounts, personal websites, and email addresses) without relying on a centralized authority to validate your claims. Instead, you create proofs by embedding cryptographic signatures in a way that is easily discoverable and verifiable by anyone. Check out my [Keyoxide](https://keyoxide.org/aspe:keyoxide.org:AMMRNOSW5TSSAU3HDPLANKICWQ) here as an example!

![image](https://github.com/user-attachments/assets/bd6dbbc2-4638-459c-84aa-7b1e5e9e0d98)

One of the main problems Keyoxide solves is the lack of trustable, decentralized identity verification. Currently, many identity systems are centralized—think of Twitter's blue checkmark, which only a select few can get, or traditional Certificate Authorities, which introduce vulnerabilities like single points of failure, high costs, or susceptibility to misuse. Keyoxide offers an alternative: a system where you remain in control of your digital identity, ensuring transparency, privacy, and interoperability. Importantly, this system requires no fees, no centralized authority, and no gatekeepers.

Another major issue Keyoxide addresses is the fragmented nature of online identities. Today, many individuals have their digital presence spread across platforms like GitHub, Mastodon, personal websites, or email. Without a unified and user-friendly system, verifying that all these accounts truly belong to the same individual becomes a complex and often untrustworthy process. Keyoxide solves this by providing a seamless method for users to securely link and verify all these different identities—making it easier to establish trust with others online.

Keyoxide also helps tackle privacy concerns inherent in centralized verification systems. Many traditional verification methods collect and store personal data, which can then be used for targeted advertising or shared with third parties. By contrast, Keyoxide respects privacy: it allows users to create a decentralized, secure identity that they control entirely, without disclosing unnecessary personal data.

# How Does Keyoxide Work?
Keyoxide works by using OpenPGP keys, a public-key cryptography standard commonly used for encryption and identity verification. Here's a brief overview of the process:

1. You start by generating an OpenPGP key, which is effectively a pair of cryptographic keys—one public, one private. You then add identity claims, called proofs, to this key. Proofs might include links to your social media profiles, websites, or even an email address.

2. You need to add verifiable information, like a special string of text or link that only you could post on your account (like a tweet or a public note on your website). This string links the identity to your OpenPGP key in a verifiable way.

3. You then upload your OpenPGP public key to a key server—a distributed database that anyone can query. Keyoxide will use this key server to find your key and associated identity proofs.

4. Anyone can then verify your identity by checking your OpenPGP key, confirming that the proofs match and that each linked account contains the correct verification string. This allows anyone to confidently confirm your ownership of all linked accounts, without relying on third parties or central authorities.

# Conclusion + Citations

Personally, I LOVE Keyoxide and I subscribe to the premise, especially as the world becomes more decentralized. I also like it's emphasis on decentralization makes it resistant to censorship and control by any single entity, allowing users the freedom to claim and prove their identities without corporate oversight. It also respects privacy, as users decide which aspects of their identity they want to link and share publicly. For anyone tired of relying on a multitude of centralized services for identity verification, I would conclude that Keyoxide offers a refreshing and empowering alternative where your identity is truly yours to manage and verify. 

:::note[Citations]

I've listed below some articles that I've cited. For more context, I would highly recommend you peruse through them!

“Create a Profile — Keyoxide Docs.” Accessed October 23, 2024. https://docs.keyoxide.org/getting-started/creating-profile/.

OpenPGP. “About.” OpenPGP, October 11, 2024. https://www.openpgp.org/about/. - (I had to quickly remember how OpenPGP worked)

“Ty Chermsirivatana - Keyoxide.” Accessed October 23, 2024. https://keyoxide.org/aspe:keyoxide.org:AMMRNOSW5TSSAU3HDPLANKICWQ. 

Vijay Prema - The Mindful Technologist. “Actually Get ‘verified’ ☑️ - Decentralized Identity Proofs,” January 2, 2023. https://vijayprema.com/actually-get-verified-online-identity-proofs/.

:::

