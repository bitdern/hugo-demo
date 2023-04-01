---
title: Into the Weeds - Bitcoin HD Wallets, Keys and Seeds
description: "An analysis of modern bitcoin wallet protocols."
date: March 5, 2023
---

Following a brief stint battling misconceptions around [energy usage](https://bitdern.com/posts/bitcoin-mining-energy-usage) on the bitcoin network, this post will shift gears and expand upon bitcoin’s cryptographic fundamentals first explored [here](https://bitdern.com/posts/priv-pub-key-sigs).

To those who have used any popular software protocols, the phrases “wallet” and “seed” are likely familiar. But before venturing into the forest of complexity, let us first take a moment to define those terms in the context of bitcoin.

Generally speaking, a [wallet](https://river.com/learn/terms/w/wallet-bitcoin/) is a software application that displays a “balance” of coins associated with a user’s public keys (addresses) and additionally secures a user’s private keys — with which one can access and spend coins.

A [seed](https://river.com/learn/terms/s/seed-bitcoin/), on the other hand, is just a piece of data. Specifically, a seed is a randomly generated 64-byte piece of data from which all subsequent private and public keys will be derived.

The content of this post will be focused on examining the concepts and features of Hierarchical Deterministic [(HD)](https://river.com/learn/terms/h/hd-wallet/) wallets, and why these types of wallets are so prevalent in the bitcoin landscape today. Because of the technical nature of this content, we will proceed in as methodical a manner as possible.

This post will cover:

- Different iterations of wallet seeds and their associated uses
- What an HD wallet is, and why they are used
- How HD wallets work
- Master and Extended keys
- Child keys, what they are and how they're generated

## Randomly Generated Security

As previously stated, a “seed” is a randomly generated 64-bit number represented in hexadecimal format — this is the base from which all of a wallet’s private / public key pairs and addresses are derived. In modern wallets, the seed is represented by a [mnemonic sentence](https://learnmeabitcoin.com/technical/mnemonic): a series of 12 to 24 words containing the sequence of randomly generated numbers (seed) within them.

Through most wallets do not display the series of steps to create the mnemonic sentence, it is beneficial to understand the process.

1. The first step is to generate entropy — the source of randomness. This can be thought of as a very large number that has not been generated before, and will never be generated again. It’s best to consider entropy as a series of bits (e.g. 001010101110101) as this is how computers store data.
2. The second step is to translate that entropy into our mnemonic sentence; the exact (technical) method of this conversion falls outside the scope of this piece, but interested readers can review the standard outlined by the [BIP-39](https://github.com/bitcoin/bips/blob/master/bip-0039.mediawiki) proposal.
3. The final step would then be to convert the mnemonic sentence into the 64-byte hexadecimal seed.

This is done by putting the mnemonic sentence with an _optional_ passphrase through the Password-Based Key Derivation Function 2 (PBKDF2). Essentially this function hashes the two inputs multiple times until it produces the final 64-byte (512-bit) seed.

## Hierarchical Deterministic Bitcoin Wallets

A [hierarchical deterministic](https://learnmeabitcoin.com/technical/hd-wallets) wallet is a wallet that generates all of its keys and addresses from a single source. "Deterministic" in that it generates keys and addresses the same way each time, and is "hierarchical" because those keys and addresses can be organized into a tree called the [derivation path](https://river.com/learn/terms/d/derivation-path/).

A benefit of using an HD wallet is that only a single source of backup is required for security. A basic wallet would generate a new private / public key pair independently, each time you received a new payment. HD wallets enable the creation of master private keys which can then generate billions of “child” private / public key pairs. In that case, one would need only to back up the single seed, as the master private key would then be able to deterministically generate all child keys.

Each child key in the wallet can generate its own keys, meaning that users can organize their keys into hierarchical trees. One use case for this could be to utilize different parts of the tree to differentiate between accounts.

Master private keys have a corresponding master public key, this key can generate the exact same child public keys without any knowledge of the associate private key. One could therefore send a master public key to a different computer / server stack to generate new receiving addresses, without fear that the private keys would be compromised in the event of a server hack.

This is useful for applications like hardware wallets, which store private keys on a dedicated device but do not sacrifice the convenience of being able to generate receiving addresses on separate devices.

## How do HD Bitcoin Wallets Work?

It begins with the seed: the randomly generated 64-byte hexadecimal value. In modern wallets, this value is most commonly represented as a mnemonic sentence — also known as a “seed phrase.” A wallet needs a large, randomly generated number from which to derive all subsequent keys and addresses, and storing that number as a mnemonic sentence is a convenient way of doing so.

The next step is to create the wallet’s master private key. This is done by putting the seed through a hash function called a “hash-based message authentication code” (HMAC) to generate another set of 64 bytes.

Within the new set of 64 bytes, the first 32 bytes are the private key and the last 32 bytes are the chain code. A [chain code](https://btcinformation.org/en/glossary/chain-code) is an extra 32 bytes that we couple with the private key — this then creates what is known as an extended key. Said differently, a chain code is a “secret” piece of data that is not broadcasted on the network. This concept will be important for later discussion on child keys.

Back to [extended keys](https://learnmeabitcoin.com/technical/extended-keys): these are private or public keys that can be used to derive new keys (child keys) in an HD wallet. A single extended private key can be used as a source for all subsequent child private / public key pairs in a wallet. Additionally, an extended public key will be able to generate the exact same child public keys (as the extended private key), without any knowledge of the associated private keys. The private key that makes up half of the extended key can still be used to create a corresponding public key.

### Child Keys and Nuances

In an HD wallet, new keys and addresses are derived from the same source (seed) and those subsequent outputs can be organized into a tree — they are hierarchical. In this way, we can take our master extended private key (private key + chain code) and run it through the [HMAC](https://www.geeksforgeeks.org/what-is-hmachash-based-message-authentication-code/) function and thus generate child keys.

An index number is also hashed with the master extended private key in this step. This is included so that multiple child keys can be created from a single master extended private key, as each time the index number changes, the hashing output is different. **A single extended key can generate 2,147,483,648 child keys.**

It is possible to create an extended public key that can generate the same child public keys as would be generated by an extended private key — in the resulting private / public key pairs. To construct the extended public key, one would need the public key from the extended private key, and couple that with the same chain code used to create the extended private key.

The master extended private key creates child private keys by running the contents of the corresponding extended public key through the HMAC function and adding the result to the original private key. Similarly, the master extended public key creates new child public keys by putting its contents through the HMAC function, and adding the result to the original public key. And so, because the original private key and public key have been adjusted by the same amount (chain code and index number), the new child private keys and public keys will correspond.

### Why extend keys with a chain code?

The code is added to keys because it delineates the subsequent child keys generated from the original key — as they are not solely derived from the preceding key.

For example, say that we used one of the public keys to receive some bitcoin, this public key would then be visible on the blockchain. If chain codes were not used to derive the child key that we used, someone would be able to take that public key and derive all the children for it.

But by using chain codes, which are secret pieces of data that are not broadcasted to the network, any would-be malicious entities are unable to derive the children. And to reiterate: when we couple a normal key with that piece of chain code, we refer to that output as an extended key.

Moreover, it is not possible to tell that two public keys (or addresses) in a tree are part of the same wallet — i.e. that they were derived from the same master extended key. Although the child keys are derived from the extended key in a specific manner, the actual public keys themselves do not share any resemblance; it should appear that they were generated completely independently.

One should take great care to properly secure the extended keys, as anyone who can access them would be able to derive all of their children.

For example, if someone’s extended master public key was leaked, anyone willing to would be able to derive all children and thus find all addresses associated with those child public keys. Now, because those are public keys, the funds are not at risk of being stolen, but the would-be malicious entity could see exactly how much bitcoin is owned in that wallet.

In the event that an extended public key and any child private key were leaked, a malicious entity would be able to take those two extended keys and calculate the master extended private key. In such a case, the entity would be able to generate all private / public key pairs and therefore steal all funds owned by the wallet. Something to keep in mind with regard to security protocols.

## Conclusion

The bitcoin network continues to benefit from advances made in public key cryptography. While these concepts are more technical than other aspects of the network’s technology stack, they are nonetheless important to understand.

Because the majority of wallets today abstract away the processes described in this piece, most users are completely unaware of what goes on “behind the scenes.”

Speaking from experience, increasing one’s general knowledge of the technological systems that underlie the bitcoin network is a surefire way to become more comfortable with transacting on the network.

I hope this piece has helped expand your technical knowledge, thank you for reading!
