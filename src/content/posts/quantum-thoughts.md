---
title: A Brief Thought Salad on Quantum Computing's Effect on Encryption
published: 2024-09-24
description: Is Our Current Encryption Ready for the Quantum Computing Revolution?
image: https://wp.technologyreview.com/wp-content/uploads/2019/07/quantumexplainer3.2-01-10.jpg
tags: [COMP390, AI, Cybersecurity, Encryption]
category: COMP390
draft: false
---

> Cover image source: [MIT Technology Review](https://www.technologyreview.com/2019/07/12/134211/explainer-what-is-post-quantum-cryptography/)

:::warning 
I'm not an Quantum Computing or Cybersecurity expert, so some information may not be entirely accurate. If you would like to suggest corrections, please email me at chermsit@dickinson.edu.
:::

# A Brief Historical Overview of Encryption
Encryption has been essential for secure communication throughout history. Early methods like the Caesar cipher, used by Julius Caesar, shifted letters by a fixed number to encode messages—for example, shifting "HELLO" three places yields "KHOOR." As cryptography evolved, the 16th-century Vigenère cipher introduced keyword-based shifts, making frequency analysis less effective. Using a keyword like "LEMON" to encrypt "ATTACK AT DAWN" created a more secure message.

During World War II, the German Enigma machine significantly advanced encryption complexity. This electromechanical device used rotors and plugboards to generate trillions of encryption combinations. Allied codebreakers, including Alan Turing, developed techniques and machines (which are known as Turing Machines) to decrypt Enigma messages, influencing the war's outcome and laying the foundation for modern computing.

:::note 
Are you at Dickinson College and want to learn more about theories of computations and learn about finita automata and P v NP? Take COMP314: Computability and Complexity! Please note that Ty Chermsirivatana '27 does not take any legal or ethical responsibility for the purchase of any caffeinated beverages or tears shed during homework.
:::

In the digital age, robust encryption became crucial. The Data Encryption Standard (DES), introduced in 1977, used a 56-bit symmetric key and was widely adopted for securing electronic data in financial transactions and government communications. However, increasing computational power eventually made DES vulnerable to brute-force attacks; the Electronic Frontier Foundation's Deep Crack machine could decrypt DES messages in about 56 hours.

To address this vulnerability, the Advanced Encryption Standard (AES) was adopted in 2001, supporting key sizes of 128, 192, and 256 bits. AES is widely used today in securing wireless networks (WPA2), encrypting files and disks (BitLocker, FileVault), and protecting data in messaging apps like WhatsApp and Signal.

![Timeline-of-quantum-cryptography](https://github.com/user-attachments/assets/83c038a1-efc8-472d-8255-797555221a2f)

At the same time, public-key cryptography revolutionized secure communications. Introduced by Whitfield Diffie and Martin Hellman (yes, now known Diffie-Hellman Exchange), and expanded by Ronald Rivest, Adi Shamir, and Leonard Adleman with the RSA algorithm, this method uses a pair of keys—public for encryption and private for decryption. Public-key cryptography enables secure internet traffic via HTTPS, secure email through PGP, and digital signatures for verifying software updates.

# How Quantum Computing Challenges the Classical Status Quo

Now that the historical lecture part of this post is over (with no mention of Alice or Bob yet, criminal I know), I'd like to turn from the past to the present. You see, quantum computing introduces a fundamentally different approach to computation and shakes up the status quo. Unlike classical computers that use bits representing either a 0 or a 1, quantum computers utilize quantum bits, or qubits, which can exist in a state of superposition—representing both 0 and 1 simultaneously. This property enables quantum computers to process a vast number of possibilities concurrently, dramatically increasing computational power for specific tasks. 

Additionally, quantum computers leverage phenomena such as entanglement and quantum interference. Entanglement allows qubits that are spatially separated to be correlated in such a way that the state of one qubit instantaneously influences the state of another. Quantum interference can be used to amplify correct computation paths while canceling out incorrect ones (allowing it to quickly eliminate inefficent subproblems). Together, these properties allow quantum algorithms to solve certain complex problems much more efficiently than classical algorithms.

![reddit_image](https://preview.redd.it/a-cool-guide-to-quantum-computing-v0-xxhpycan5jwb1.jpg?auto=webp&s=02ec02da70d43c499ecb8980f9ccc62260c30b20)

A great example of quantum computing in action is Shor's Algorithm. In 1994, mathematician Peter Shor introduced this algorithm, which can factor large integers and compute discrete logarithms exponentially faster than the best classical algorithms. This poses a significant threat to cryptographic schemes like RSA and Elliptic Curve Cryptography (ECC), both of which rely on the difficulty of factoring large numbers or solving discrete logarithm problems. The security of RSA hinges on the fact that while it's easy to multiply two large prime numbers, factoring their large composite product is computationally infeasible for classical computers. Shor's algorithm exploits quantum properties like superposition and quantum parallelism to perform efficient factorization, effectively breaking RSA encryption when run on a sufficiently powerful quantum computer. But, don't take my word for it. Check out this incredibly cool poster by NASA!

![SOARS2021_Fedele_2-1](https://github.com/user-attachments/assets/8c21ef21-496a-4625-a5ff-ae76960acb96)

While practical quantum computers capable of executing Shor's algorithm on encryption-strength numbers are not yet available, ongoing advancements suggest this could become feasible. This looming threat has accelerated research in post-quantum cryptography, aiming to develop new algorithms resistant to quantum attacks and secure against both classical and quantum computers. 

# Is Encryption Over? Will Quantum Computing force me to delete my browser history?

Rest assured, encryption isn't doomed, and you won't need to frantically clear your browser history anytime soon. While quantum computing presents new challenges, it doesn't spell the end of all cryptographic security.

![image](https://github.com/user-attachments/assets/13e06717-5d6f-4784-9588-5c5fed2e4afa)

I recently had a lovely chat with Professor Matthew Ferland (I believe he prefers just Matt. Personally, I'd like to call him Matt-ematics) about the notorious P vs NP problem. I'd paraphrase him in saying that someone ever proves P equals NP, we might all need to find new careers or at least some new puzzles to keep ourselves entertained. However, I would say that understanding P vs. NP is crucial because it highlights why some problems are easy to verify but hard to solve a - a concept that's key to how quantum computing can impact encryption.

You see, Classical encryption algorithms like RSA rely on NP-hard problems, which are mathematical challenges that are easy to verify but extremely difficult to solve without the key. Quantum computers can tackle some of these problems more efficiently. For instance, Shor's algorithm enables a quantum computer to factor large numbers exponentially faster than classical algorithms, posing a threat to RSA encryption. However, while quantum hardware is powerful in theory, it's not the end-all be-all solution or at least not yet.

Despite the impressive potential of quantum computing, current quantum hardware faces significant limitations. Building a quantum computer capable of running Shor's algorithm on encryption-strength numbers (like those used in RSA keys) is an immense technical challenge. Present-day quantum computers have a limited number of qubits, and these qubits are prone to errors due to decoherence, where quantum states lose their quantum properties through interaction with the environment (such as loss of temperature). Furthermore, error rates in quantum computations are still high. For instance, to factor a 2048-bit RSA key-a common key size in secure communications would require millions of high-quality, error-corrected qubits. Currently, the most advanced quantum computers have qubit counts in the hundreds, and they struggle with maintaining coherence long enough to perform complex calculations.

Moreover, quantum computers are not universally faster than classical computers for all types of problems. They excel at specific tasks where quantum algorithms offer advantages, such as factoring and unstructured search (via Grover's algorithm, very cool to run on AWS Braket using Qiskit), but they don't provide speed-ups for all computational problems. Classical computers remain more efficient for a wide array of tasks and are continuously improving.

I would also like to note that the cryptographic community (such as organizations like the NSA and NIST) is actively preparing for the quantum era. Researchers are developing and standardizing post-quantum cryptographic algorithms that are resistant to quantum attacks. These new algorithms are based on mathematical problems that are currently believed to be hard for both classical and quantum computers, such as lattice-based, code-based, and hash-based cryptography.

![CryptographyChart](https://github.com/user-attachments/assets/41a46625-9143-4c7b-bd1f-f5221e41fb9c)

# Musings & Citations

I hope that I didn't bore my professor as much as I did with my AI Bill post. You know, in the grand scheme of things, encryption isn't over; it's evolving. The advent of quantum computing doesn't signal the demise of data security but I would say that it's a new chapter in our quest to protect information. It's a reminder that technology is always changing (thanks Moore's Law) and that adaptability is key. Now, I won't bore readers with many more platitudes but the question still remains. Should you start panicking about the security of your encrypted data? Not quite. While it's wise to stay informed and prepared for what quantum computing may bring, there's no need to delete your browser history just yet. The collaborative efforts of mathematicians, computer scientists, and cryptographers continue to keep us safe. Really, we should hope that AI doesn't come for grant funding first!

:::note[Citations]

I've listed below some articles that I've cited in understanding Quantum Computing. For more context, I would highly recommend you peruse through them!

Asst. Professor of Computer Science, Ferland, Matt "Matt-ematics". Personal Conversation at Dickinson College on Tome 2nd Floor. 16 Sept. 2024. https://www.dickinson.edu/site/custom_scripts/dc_faculty_profile_index.php?fac=ferlandm

American Scientist. “Is Quantum Computing a Cybersecurity Threat?,” January 30, 2019. https://www.americanscientist.org/article/is-quantum-computing-a-cybersecurity-threat.

MIT Technology Review. “Explainer: What Is Post-Quantum Cryptography?” Accessed September 24, 2024. https://www.technologyreview.com/2019/07/12/134211/explainer-what-is-post-quantum-cryptography/.

Security, HP Wolf. “Anticipating the Quantum Threat to Cryptography.” HP Wolf Security (blog), February 21, 2024. https://threatresearch.ext.hp.com/anticipating-the-quantum-threat-to-cryptography/.

ReHack, Zac Amos. “‘Harvest Now, Decrypt Later’: Why Hackers Are Waiting for Quantum Computing.” VentureBeat (blog), September 21, 2024. https://venturebeat.com/security/harvest-now-decrypt-later-why-hackers-are-waiting-for-quantum-computing/. 

Shor’s Algorithm: How Quantum Computing Affects Cybersecurity – SOARS 2021. Accessed September 24, 2024. https://unfsoars.domains.unf.edu/2021/posters/shors-algorithm-how-quantum-computing-affects-cybersecurity/.

Wolchover, Natalie. “A Tricky Path to Quantum-Safe Encryption.” Quanta Magazine, September 8, 2015. https://www.quantamagazine.org/quantum-secure-cryptography-crosses-red-line-20150908/.
:::
