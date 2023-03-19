---
title: "Bitcoin Basics Blocks Blockchain"
date: 2023-03-19T11:48:27-05:00
draft: false
---

It is worthwile to push oneself to learn about the complex, more technical aspects of bitcoin -- but only insofar as one has properly grasped the basics. Whereas other posts covered topics like [hierarchical deterministic wallets](https://bitdern.com/posts/hdwallets-keys-seeds), [cryptographic primatives](https://bitdern.com/posts/priv-pub-key-sigs), and [specific](https://bitdern.com/posts/bitcoin-africa-machankura) use-cases for bitcoin, this post is meant to refocus on the basics.

Since this is a bitcoin-focused blog, this post will examine the anatomy of blocks and blockchains by using the bitcoin blockchain as our reference. This is because bitcoin has demonstrated qualities of robustness and anti-fragility. Unfortunately for most "blockchain" or "web3" investors who have yet to put in the requisite amount of study, the industry is a hotbed of grifters and rent-seekers who seek to extract value through morally-questionable methods.

Therefore, in order to build a resilient 'tower' of bitcoin knowledge, one must take care in ensuring that the foundation is properly built -- so to speak. As such, this post will address a series of commonly asked questions in the hopes of providing a sufficient amount of foundation-building materials.

The following topics will be covered:

- What blockchains are
- What a 'block' is, and what it is composed of
- How users can acquire and maintain copies of the blockchain
- The process by which new blocks are added to the chain
- Additional nuances of the bitcoin blockchain system

## What is a Blockchain?

Fundamentally, a blockchain is a file of data — bitcoin transactions, in this case. From a structural perspective, blockchains like bitcoin can be conceptualized as global ledgers of accounts. The caveat is that bitcoin does not have “accounts”, rather, the bitcoin network is built upon a series of [inputs and outputs](https://bitdern.com/posts/inputs-outputs-utxo-model). Those “unspent transaction outputs” (UTXOs) are essentially dollar bills in a user’s chosen wallet.

Further, the wallet is not a physical device, it is an easily accessible software interface that manages the user’s private keys — which enables them to spend their funds. Therefore, on the bitcoin blockchain, the global ledger structure maintains an immutable record of the existing set of UTXOs and the public keys (addresses) associated with specific amounts of bitcoin.

Another useful metaphor to help visualize the bitcoin blockchain is that of a series of [storage lockers](https://learnmeabitcoin.com/technical/blockchain). In this example, each locker is represented by a public key (address), and the contents inside each locker are represented by the UTXO associated with the address. Thus, the only user who would be able to access the contents of the locker would be that person (or entity) who owns the private keys.

A blockchain is called a “blockchain” because new transactions are added to the existing file in “blocks,” and new blocks are built _on top_ of each other to create a chain of blocks. This is why, from a nomenclature perspective, when referring to the total number of blocks in a chain, we refer to this metric as “block height.”

All metaphors aside, the bitcoin blockchain is an immutable, permanent record of bitcoin transactions.

## What is a Bitcoin Block?

There are many components that make up a block of bitcoin transactions, many of which necessitate technical explainations which fall outside the scope of this post.

However, it will be useful for readers to gain a baseline understanding of the information contained in a [“block header.”](https://learnmeabitcoin.com/technical/block-header) A block header is, essentially, the metadata associated with a particular block’s transactions. The fields within the block header provide a unique summary of the transactions of the entire block.

1. The first field is the version number, this allows anyone validating transactions on the network (node-runners) to see if the block has been changed in its composition.

2. The second field contains the previous block’s [block hash](https://learnmeabitcoin.com/technical/block-hash). A block hash is a reference number for a block in a blockchain and it is created by hashing the block header through SHA256 twice. By including the previous block hash into the new block’s header, an unbreakable (encrypted) tie is formed between the two blocks.

3. The third field contains the [Merkle Root](https://learnmeabitcoin.com/technical/merkle-root) — this piece of data can be thought of as all of the transactions in the block, hashed together. The Merkle Root provides a single-line summary of all the transactions in a particular block.

4. Following that field is Time: when a miner attempts to mine this current block, the Unix time at which the block header is being hashed is noted within the block header.

5. After Time comes the [Bits](https://learnmeabitcoin.com/technical/bits) field, a shortened version of the “mining target,” which is itself a measure of how difficult it is for a miner to mine the next block (a topic explored in [this](https://bitdern.com/posts/hashrate-network-decentralization) post).

6. The final field in a block header is the [nonce](https://learnmeabitcoin.com/technical/nonce), the field that miners change in order to try and get a hash of the block header (Block Hash) that is below the target. Nonce is an abbreviation of “number used once” — changing just one digit in an input completely changes the output of a SHA256 algorithm.

All six of the fields that comprise the block header are run through the SHA256 algorithm twice in order to produce the block hash of a particular block. Because this (current) block hash is used in the field of the block built on top of it, each block is cryptographically “chained” to its immediate predecessor, who is tied to _its_ immediate predecessor, and so on.

Satoshi certainly devised an elegant and simple solution to the question of how to relate blocks to one another.

### How does one get a copy of the Bitcoin Blockchain?

Let’s assume that the user in question has a functional [node](https://river.com/learn/why-should-i-run-a-bitcoin-node/) running.

_A (bitcoin) node is simply a computer device that runs a version of the bitcoin software — this could be an old laptop, desktop, or dedicated micro-computing device._

When a user runs a version of the bitcoin software for the first time, their node will begin to download blocks from other nodes in a process known as the Initial Block Download (IBD). Depending on the user’s internet speed, the IBD can take several hours to complete. At the time of writing, the bitcoin network’s [block height](https://mempool.space/) is sitting at 780,017; there are many blocks to download.

The interaction between peer nodes on the network begins with a comparison of their respective block heights, literally, “how many blocks do you know of?” If the peer node knows of more blocks than the user’s, the user’s node will request these blocks from its peers until it has an up-to-date copy of the chain.

As a result of this behavior, nodes on the network are constantly in communication, propagating new blocks so that each node on the network maintains a complete blockchain. Much like there is no “single version” of the bitcoin software, there is no “single version” of the bitcoin blockchain; each node maintains its own local copy which can vary from node to node.

### How are new Blocks added to the Bitcoin Blockchain?

This feat is accomplished by the process of [mining](https://learnmeabitcoin.com/beginners/mining), where pending transactions sit in a queue (mempool) until a miner moves them into a “candidate block.” Transactions are only confirmed at the time a miner successfully mines a block by using their processing power to produce a block hash that is below a specific target value. **A detailed exploration of the bitcoin mining process will be published later this month expanding upon this summary.**

Technically, any node on the network can attempt to mine a block, but with technological advancements made in mining protocols — specifically the use of ASICs (Application-Specific Integrated Circuit), the days of mining bitcoin from one’s laptop are over. That said, the differentiation in processing power between ASICs and standard computing devices (nodes) presents distinct roles: ASICs mine blocks, and node devices validate and maintain globally distributed copies of those blocks.

When a mining node successfully proposes and mines a block, it will share the new block with other nodes on the network. Other nodes add the new block to their chain, and miners begin the process of building the next block on top of the most recent one. The system is supported by periodic mining difficulty adjustments: every 2016 blocks the average time it took for a new block to be produced is calculated. If that average time is _greater than_ 10 minutes, mining difficulty increases, and conversely, if the average time is _less than_ 10 minutes, mining difficulty decreases.

These difficulty adjustments ensure that no matter how many miners voluntarily enter (or leave) the network, new blocks are produced approximately every 10 minutes.

### Can two blocks be mined simultaneously?

Yes, this is possible and not as uncommon as one might imagine. In the case where two blocks are mined simultaneously, each node will consider the first block it received as a part of its blockchain but will keep the second block _just in case_. That second block (and the transactions that compose it) will not be considered a part of the “active” blockchain.

Consequently, nodes on the network will be in disagreement about which of the two blocks belongs at the top of the chain. The issue is resolved once the next block is mined — that next block will be built on one of the blocks, creating a new longest chain. Bitcoin nodes are programmed to adopt the longest known chain of blocks as their active blockchain. Thus, those nodes who received the “incorrect” block first will perform a chain reorganization to remove old blocks from their active chain in favor of the blocks that make up the new longest chain.

Therefore, although disagreements between nodes do exist, the conflicts are relatively short-lived, as the combination of new blocks being mined and nodes’ longest chain preference typically resolves disagreements quickly.

### So blocks in the blockchain can be replaced?

As discussed in the previous section, there are routine circumstances in which a node will reorganize its local copy of the blockchain. In fact, chain reorganization is one of the major protocol-level threats to the sustainability of the bitcoin network. If a nefarious actor was able to reorg the chain, they could effectively undo, redo or remove any transactions they wished.

However, it is important to consider the feasibility of such an attack. All miners are incentivized to build on the longest chain: if they successfully mine the next block, they are rewarded with transaction fees plus a “block reward” — 6.25 BTC at the time of writing. It stands to reason that if all miners are incentivized to build on the longest chain, that means that the combined processing power of the entire population of miners on the network is focused on building one chain.

Therefore, while it is certainly possible for a nefarious actor to attempt to build a new chain — one that is more favorable to them from reorganizing and censoring transactions — it would take a staggering amount of processing power to accomplish. This scenario is what is known as a “51% Attack,” meaning that the attack can only be successful if the nefarious actor was in control of > 51% of all processing power on the network. A tall order, to be sure.

## Conclusion

In a general sense, blockchains are a data storage solution implemented as a distributed network of interconnected computer systems that independently validate the movement of data across the network. The bitcoin network is a great educational reference when learning about blockchains because of the simplistic elegance with which the system was constructed.

Nodes are programmed to share block data they maintain with other nodes who may not have those blocks, and since they are also programmed to adopt the longest-known chain of blocks as their active blockchain, any discrepancies between peers are quickly resolved.

Concurrently, the process of mining incentivizes miners to build on the most recent block, and to use their processing power to participate in the creation of new blocks every 10 minutes on average. The coalescence of these and other incentive structures on the bitcoin network have provided the protocol with a remarkably strong base from which to build higher.

In a similar manner, when we as humans take the time to truly understand the foundational principles of our areas of study, we find that all subsequent knowledge built on top is much more cohesive and stands the test of time.

Thanks for reading, I hope this post helped you broaden your knowledge base!
