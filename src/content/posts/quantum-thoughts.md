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
I'm not an Quantum Computing or Cybersecurity expert, so some information may not be entirely accurate. If you would like to suggest corrections, please email me at [chermsit\@dickinson.edu](mailto:chermsit\@dickinson.edu)
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

A great example of quantum computing in action is Shor's Algorithm. In 1994, mathematician Peter Shor introduced this algorithm, which can factor large integers and compute discrete logarithms exponentially faster than the best classical algorithms. This poses a significant threat to cryptographic schemes like RSA and Elliptic Curve Cryptography (ECC), both of which rely on the difficulty of factoring large numbers or solving discrete logarithm problems. The security of RSA hinges on the fact that while it's easy to multiply two large prime numbers, factoring their large composite product is computationally infeasible for classical computers. Shor's algorithm exploits quantum properties like superposition and quantum parallelism to perform efficient factorization, effectively breaking RSA encryption when run on a sufficiently powerful quantum computer.

While practical quantum computers capable of executing Shor's algorithm on encryption-strength numbers are not yet available, ongoing advancements suggest this could become feasible. This looming threat has accelerated research in post-quantum cryptography, aiming to develop new algorithms resistant to quantum attacks and secure against both classical and quantum computers. 
