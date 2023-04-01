---
title: Private Keys, Public Keys, and Digital Signatures on Bitcoin
description: "An overview of fundamental technologies used by the bitcoin protocol."
date: January 12, 2023
---

In a [previous](https://bitdern.com/posts/inputs-outputs-utxo-model) blog post, we examined the bitcoin network from the perspective of the building blocks of transactions: inputs and outputs. This post will refocus on the basics and expand upon important concepts like digital signatures, and private and public key pairs.

Before diving into applications of these concepts in bitcoin, it is worth reviewing the historical context of public and private key cryptography's [genesis](https://history-computer.com/public-key-cryptography-complete-guide/). Generally, Public Key Cryptography is a system of encryption that utilizes a public and private key pair in order to encrypt (public) and decrypt (private) messages that one peer sends to another. An advantage of this system is that the public key can be known to all participants on the network, but without a mathematical decryption mechanism (private key / digital signature), messages are safely encrypted and are only parsable by the intended recipient.

The system can otherwise be referred to as one-way authentication or asymmetric cryptography. Public Key cryptography was developed in 1976 by Marin Hellman, Ralph Merkle, and Whitfield Diffie. The three men met at Stanford University and were attempting to devise a more secure solution than private key cryptography — wherein two peers both possess private keys.

A drawback in private key cryptography is that if one of the keys falls into the wrong hands, the encryption can be broken. So, by reducing the number of private keys (to one) and introducing publicly known keys, public key cryptography radically increased the security of encryption.

This piece will cover the implementation of public key cryptography in bitcoin:

- What a private key is, and how it is derived.
- What a public key is, and associated functions.
- The importance of the elliptic curve in public key cryptography.
- What constitutes a digital signature, and how they are utilized in bitcoin.

## Large, Random Numbers

The simplest definition of a private key is that it is a large, random number. In the bitcoin network, it is a 256-bit number — this is because bitcoin utilizes the SHA-256 hashing algorithm (Secure Hashing Algorithm 256 bits).

256-bit numbers can be represented in a variety of formats; binary is likely familiar to readers — 0101001011010. There is also the decimal format (e.g. 18061531356) and the hexadecimal format (e.g. ef235aacf90d9f4aadd8) — bitcoin utilizes hexadecimal to represent data in the system.

Essentially, a [256-bit](https://learnmeabitcoin.com/beginners/private_keys) number is a number that can be stored inside 256 bits of data — where a bit is the smallest unit of data inside a computer. A bit is capable of storing only values of “0” or “1”, however, bits can be used to represent everyday numbers. For example, the number five, stored in a bit would look like this: 101. Therefore, a 256-bit number is represented by using 256 of these bits (at most), and the total amount of 256-bit numbers is equal to 2<sup>256</sup>.

A bitcoin private key, similarly, a randomly generated, 256-bit number. A private key can be generated by flipping a coin 256 times (binary format), using one’s favorite programming language to generate the number (decimal), or running a piece of data through the SHA-256 hashing function (hexadecimal). All of these generation strategies will work, so long as one is able to ensure that the output is _actually_ random. If a nefarious actor is familiar with the pattern or generator used to create the random number, the private key is potentially exploitable — and in that case, any bitcoin locked to an address associated with that private key is at risk of being stolen.

Flipping a coin 256 times is a serviceable approach, as it is highly unlikely that anyone would get the exact same results from running a similar procedure. The fact that anyone can create their own “bitcoin account” by generating a random number (private key) is a fantastic feature of the protocol. This feature democratizes bitcoin, in the sense that there are no central authorities in charge of issuing new accounts. Plus, since there are 2^256 possible iterations of private keys, taking the time to randomly generate one provides users with a robust amount of security from the onset.

## Math and Graphs

A public key is similarly represented as a large, 256-bit number in the hexadecimal format. However, a public key is actually generated from a private key. This is done by inserting the private key into a mathematical function, specifically, the [elliptic curve](https://learnmeabitcoin.com/beginners/public_keys) as represented by the equation y<sup>2</sup> = <sup>3</sup> + ax + 7 (where a = 0), and the following image:

![](/public/generatorpoint.png)

> Image Source: http://learnmeabitcoin.com/publickey

Visual representations allow for a more thorough description of the process by which public keys are generated from private keys. The mathematical function is called _elliptic curve multiplication_, though this term is slightly misleading, as it is not multiplication in the sense that most readers will have learned.

Elliptic curve multiplication is a process more akin to “bouncing around the curve” on the graph shown to the left until reaching a final coordinate — the numbers associated with this coordinate represent the public key.

![](/public/multiplication.png)

> Image Source: http://learnmeabitcoin.com/publickey

The above graph approximates the process previously described. We would first “multiply” point #1 by our private key: bouncing around the curve — shown above as taking the intersection point of the tangent line. Finally, we would take the inverse point on the curve from points #2 — #3, thus we would have our public key.

More specifically, we would have an (x,y) coordinate of our public key — this would be represented by the x and y coordinates put together in hexadecimal format.

Our public key, represented by a hexadecimal can be further optimized. In the bitcoin network today, [compressed public](https://gist.github.com/TheTrunk/30ff5ef59d3063f465cc766a4a64a397) keys are commonly used as a space-saving tool. This is because the elliptic curve is based on a bivariate equation, meaning that if you have a value for one variable — x, in this case — you can solve for the other.

Recall that in the equation y<sup>2</sup> = x<sup>2</sup> + ax + 7, y is squared, meaning that its value could be positive or negative. Due to the way that elliptic curves work, if y is even, the coordinate is above the x-axis, whereas an odd y-value means that the coordinate is below the x-axis. In bitcoin, compressed public keys are composed of a prepending value, 02 or 03, denoting whether the y value is even or odd, respectively, plus the full x coordinate. Bitcoin developer Greg Walker puts it this way “[it] seems like a lot of effort for a little less text, but because public keys are used within transaction data, it does end up saving a lot of space in the blockchain over time.”

## Why the Elliptic Curve?

This function has two distinct qualities that make it suitable for private/public key pairing. First, elliptic curve multiplication is a [trapdoor](https://en.wikipedia.org/wiki/Trapdoor_function) function, meaning that it is incredibly difficult to “go backwards” — i.e. divide the coordinates of the public key in order to find the private key. A trapdoor function is a function that is easy to compute in one direction, yet difficult to compute in the opposite direction (finding its inverse) without special information, called the “trapdoor.”

The second property is that the public key is still mathematically connected to the private key, and as a result, one can prove ownership of the private key without actually revealing it. This is especially important for the bitcoin network; when making transactions, public keys are used in the transaction data and one party must prove ownership of private key associated with the public key.

Broadly speaking, the proof is based upon a mathematical connection between the private and public key pair; the private key can be put through the elliptic curve function and return a new value. The public key can be put through the elliptic curve function and return another new value.

These two values will have a small amount of overlap, which proves the connection between the public and private key pair.

## Sign on the Dotted Line

Similar to keys, digital signatures are large numbers represented in hexadecimal format that are used to prove ownership of a private key. Thankfully, proof of ownership does not compell one their private key. As with the other facets of public and private key pairs, math is all that is necessary to prove the connection between the digital signature and the public key.

A [digital signature](http://learnmeabitcoin.com/beginners/digital_signatures) has two components: a random portion, and a signature portion. The first (random) portion is created by generating a random number and multiplying it with the generator point on the elliptic curve — that same point used to generate the public key in the “Math and Graphs” section of this piece.

The random portion of the digital signature will be the coordinates of the point at which we end up, point **“r”** for short. The second portion is the signature — take the private key and multiply it with the random point **“r.”** Next, include the thing to be signed, the message.

In the context of bitcoin, the message is a hash of the entire transaction data, which contains the output to be unlocked and spent in a particular transaction. Including a transaction hash ties the signature to one specific transaction so that it cannot be re-used (or tampered with at some point in the future).

Finally, divide the product **[ (r * private key) + message ]** by the initial random number. Thus, we have the signature portion, which called **“s”**. To prove ownership of a private key (for an associated public key), all that is needed is the digital signature **(r,s)**.

### _Why does bitcoin use digital signatures?_

The reason for this is that when constructing a bitcoin transaction, all UTXOs [(unspent transaction outputs)](https://river.com/learn/bitcoins-utxo-model/) intended to be inputs, must be unlocked. This is accomplished by proving that one “owns” the UTXO, which is itself accomplished by demonstrating ownership of the private key that the output is locked to.

Simply inputting a private key into a transaction reveals it to the entire network — if a malicious entity were to gain knowledge of a private key, they would be able to unlock any other UTXOs that were locked to that address. Enter digital signatures: this tool allow us to demonstrate ownership of a private key, without revealing the key itself.

### _Could someone re-use a signature to unlock other outputs at my address?_

Each digital signature contains within it the _specific_ transaction hash for which it is signing. Because the original transaction data is used in the construction of the digital signature, it can be thought of as a one-use piece of cryptography. If someone attempted to re-use the signature to sign for another transaction, the transaction data within the signature would conflict with the transaction data that it is intended to sign for. Nodes along the network will immediately recognize this discrepancy and reject the transaction. Because each digital signature contains the specific transaction hash, it protects against the possibility of someone retroactively tampering with the transaction.

## Conclusion

Breakthroughs in cryptography made by a handful of young men in Northern California in the 1970s have provided mankind with the capability to push the boundaries of what money is, and can be. Where there were initially weaknesses in private key cryptography, a more secure public key system was developed; that development is no anomaly.

Whether it be a digital signature to scalably and securely prove ownership of a private key, or something else, humans continue to innovate. The purpose of this particular piece is not to suggest that these innovations came out of bitcoin — as this is clearly not the case. The purpose is to highlight the intricate details and building blocks which bitcoin is built upon.

In order to fully grasp the value propositions that bitcoin offers, one must take the time to understand the fundamental elements from which it is built.