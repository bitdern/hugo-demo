---
title: Hashrate in Bitcoin and Network Decentralization
description: "What hashrate is, why it is important to the network, and facts highlighting the state of global hashrate."
date: December 20, 2022
---

Previous posts sought to establish a foundation for understanding the bitcoin protocol by examining the structure of [transactions](https://bitdern.com/posts/inputs-outputs-utxo-model) and underlying [cryptography](https://bitdern.com/posts/priv-pub-key-sigs). This post will focus on bitcoin’s hashrate and the implications associated with network centralization.

Generally, the hashrate of a Proof-of-Work(PoW) network is an indicator of that network’s health. This is because miners on PoW networks compete with each other to produce a block hash that is beneath a specified threshold; the more miners that are competing, the more hashes are produced. The more hashes produced, the harder it is for malicious entities to undermine the integrity of a PoW network’s consensus rules -- e.g. by reorganizing transactions inside blocks to financially benefit themselves.

Therefore, the higher a PoW network’s hashrate, the more secure the network (and associated funds).

This post will cover:

- ‘Hashing’ and ‘Hashrates’
- The bitcoin mining process
- Mining targets, difficulty adjustments — and how these components influence the network
- The importance of a robust hashrate in a PoW network
- Current trends in the global hashrate, complications, and potential solutions

## Setting the Foundation

A ‘hash’ is a fixed-length, alphanumeric code used to represent words, messages, and data of any length. Think of hashing as a sort of data compression mechanism. The bitcoin network uses the SHA-256 (secure hashing algorithm — 256 bits). ‘Hashrate’ refers to the number of hashes that a network — or individual mining operation — can make on a per-second basis. For example, if a network has a hashrate of 10 Th/s, this means that [10 trillion](https://www.coindesk.com/tech/2021/02/05/what-does-hashrate-mean-and-why-does-it-matter/) calculations can be made every second.

Miners on the bitcoin network compete for the right to create the next block, they are incentivized to do so by a reward of new bitcoin and transaction fees. These miners utilize specialized hardware devices called ASICs [(Application-Specific Integrated Circuits)](https://compassmining.io/education/differences-between-asic-gpu-mining-cryptocurrency/) — this is because these devices are specifically designed to produce as many hashes as possible. Nearly all miners use these devices today, and as a result the bitcoin network’s overall hashrate has been steadily trending upward.

Consistent, positive growth in hashrate is vitally important to the security of the network: the more miners’ machines produce hashes, the harder and more expensive it is for bad actors to attempt to undermine the network.

The observed trend is for more miners to join the network over time, which would imply that there are more miners producing more hashes than brefore. Given more hashes on the network, one could expect that new blocks would be produced more frequently than every 10 minutes, on average.

However, as we will see in the following sections, bitcoin’s creator(s) designed an elegant mechanism that maintains bitcoin’s every-ten-minute metronome.

## Bitcoin's Structural Stability

Bitcoin was designed to prioritize security and stability within the core functionality of the protocol: produce new blocks of censorship-resistant transactions every 10 minutes, on average. There have been attempts to increase the network’s throughput — the number of transactions able to be processed — by increasing the frequency that new blocks are added to the chain. Although increasing network throughput may seem like a good idea, it can lead to the unintended consequence of miners building competing chains, composed of different blocks, this amounts to wasting processing resources and splintering global hashrate.

The creator(s) of the network, Satoshi Nakamoto, possessed an astounding level of forethought. Bitcoin’s Proof-of-Work consensus model is supported by a dynamic block hash mining [target](https://learnmeabitcoin.com/technical/target), which represents the hexadecimal threshold that a miner (or mining pool’s) proposed block hash must fall beneath to be added to the chain.

A [block hash](https://learnmeabitcoin.com/technical/block-hash) is basically a reference number for a block in the blockchain. The mining target is adjusted every 2016 block (~2 weeks) in a process known as the difficulty adjustment.

> To compensate for increasing hardware speed and varying interest in running nodes over time, the proof-of-work difficulty is determined by a moving average targeting an average number of blocks per hour. If they’re generated too fast, the difficulty increases.
> — [Satoshi Nakamoto](https://nakamotoinstitute.org/bitcoin/)

The initial target value is hard-coded into the source code of every node and was likely Satoshi’s best guess as to what difficulty level would produce blocks in ~10-minute intervals. Today, each node calculates its own target by simply dividing the actual time between blocks by the expected time between blocks, both within a 2016 block period.

For example, say that the total time between blocks was 21,160 minutes — each node would divide that by the expected value of 20,160 minutes and end up with a difficulty adjustment value of 1.04.

In the above example, blocks were being produced **less frequently** than every 10 minutes on average, therefore the difficulty adjustment would move the **target upward** to make it easier for miners to get below the target during the next period of 2016 blocks. Conversely, if new blocks are being produced **more frequently** than roughly every 10 minutes, the difficulty adjustment would move the **target downward** and make it harder to mine new blocks.

Again, miners’ specialized devices are producing a staggering amount of hashes per second in an effort to produce a block hash with a value beneath the period’s mining target threshold.

## Rising Tide Lifts All Boats

These systems are in place to ensure that the amount of time between blocks is approximately 10 minutes, on average. This length of time was intentionally chosen by the creator(s) of bitcoin in order to maintain a consistent interval between blocks, and the consistency has two main advantages.

As previously mentioned, 10 minutes gives blocks enough time to be propagated across the network, thus minimizing the risk of miners building competing chains and wasting resources. Second, the consistent time between blocks amounts to a consistent issuance of new bitcoin via the block reward paid to the miner (or mining pool) responsible for constructing the latest block.

A relatively fixed rate of new bitcoin issuance adds stability to the network — which is especially important from the perspective of bitcoin as a monetary good. 10 minutes has so far stood the test of time, sufficiently balancing a new block’s propagation along the network, with not having users wait too long for a new transaction to be added to the chain.

Bitcoin is a dynamic and complex system, and the creator(s) understood that as the system grew in popularity, miners would likely become more sophisticated and grow in number. This trend is generally positive, as the network is more secure, and it is more expensive for malicious entities to execute a [51% attack](https://learnmeabitcoin.com/technical/51-attack). But the trend does pose an ongoing challenge to a system that is designed to be predictable.

> If broadcasts turn out to be slower in practice than expected, the target time between blocks may have to be increased to avoid wasting resources. We want blocks to usually propagate in much less time than it takes to generate them, otherwise nodes would spend too much time working on obsolete blocks.
> — [Satoshi Nakamoto](https://satoshi.nakamotoinstitute.org/emails/cryptography/12/#selection-63.209-63.512)

Ultimately, the dynamic processes of mining block hash targets and predictable difficulty adjustments, a balance in trade-offs has been reached. Thus far, the bitcoin network has been demonstrably anti-fragile. But bitcoin is a living process that constantly evolves; new challenges arise that threaten the network’s security and demand action from stakeholders.

The next section will examine current trends in the mining industry and extrapolate on the implications of “hashrate centralization.”

## Network Centralization

Until the Chinese government’s 2021 actions to restrict and outright ban bitcoin mining in certain regions, China was a massive contributor to the global hashrate. According to [data](https://ccaf.io/cbeci/mining_map) from the University of Cambridge’s Bitcoin Electricity Consumption Index, mainland China accounted for approximately 65% of the network’s global hashrate — with the Xinjiang and Sichuan provinces accounting for about 30%, globally as of April 2020.

The Block [reported](https://www.theblock.co/post/109315/bitcoin-hashrate-declines-50-percent-china-mining-crackdown) that in the month that followed the Chinese government’s decision, bitcoin experienced a nearly 50% decline in global hashrate. Network hashrate quickly recovered due to countries like the United States and Kazakhstan producing more hash, but the events of 2021 illustrate a legitimate threat to the ongoing success of bitcoin: hashrate centralization.

Bitcoin’s global hashrate has experienced a dramatic increase since 2019, due to the rise in popularity and profitability of enterprise-scale mining operations. As previously discussed, a rising hashrate is a net benefit for the network, as users’ transactions and funds are more secure.

However, if this increase in hashrate is concentrated in the operations of a handful of large players — the network’s security is at risk via a handful of points of failure. A [blog post](https://medium.com/lumerin-blog/a-look-into-the-critical-vectors-of-hashrate-centralization-f6d3a49da771) from Lumerin Protocol lays out distinct centralization vectors that could be damaging to the bitcoin network if not adequately addressed.

### Geographic Centralization

The most prevalent form of hashrate centralization in the mining industryis the concentration of hashrate in specific geographic locations. This is to be expected given miners’ preferences to secure cheap electricity, stable infrastructure, and locate in favorable regulatory environments.

Roughly 50% of hashrate produced by the United States is concentrated in three states: Georgia, Texas, and Kentucky. All three of these states have the appropriate infrastructure, entrepreneur-friendly regulatory climates, and most importantly — cheap electricity, all paying between [11–12](https://paylesspower.com/blog/electric-rates-by-state/) cents per kilowatt hour. As evidenced by the Chinese government’s 2021 actions, the geographic concentration of miners is inherently risky, as a regulatory environment can change faster than miners can move their physical infrastructure, generally speaking.

### Power Generation Centralization

Similarly, if all miners in a certain location are drawing power from the same generation source, the generation source is a centralization risk. This risk is tangential to geographic centralization, as it is likely that those in the same physical location would be accessing the same power grid.

Generally, power grids themselves are centralizing forces: between [8-15%](https://chintglobal.com/blog/how-much-power-loss-in-transmission-lines/) of power is lost in transmitting from generation source to consumer. Transmission of electricity necessitates investments in infrastructure, which are at risk of being disrupted by single players — generation plants or grid operators. Certain mining operations have recognized this potential threat, and are seeking to innovate solutions by harnessing “stranded” energy products, like flared [natural gas](https://www.reuters.com/business/sustainable-business/oil-drillers-bitcoin-miners-bond-over-natural-gas-2021-05-21/), to generate power for their operations.

Miners are primarily concerned with the profitability of their operation and are effectively “short” their local currency (via electricity and infrastructure costs) and “long” bitcoin. While a sense of network-based altruism could exist, most miners are acting in their best interests.

### Mining Pool Centralization

The majority of miners today direct their hashrate at a mining pool for enhanced profitability and stable payouts. The [top three](https://mempool.space/graphs/mining/pools) mining pools account for roughly 50% of the global hashrate, while the top 10 pools produce more than 98%. Unfortunately, the price paid for this pooling of hash resources is an undeniably centralized block construction process.

Miners who point their hash at a pool do not construct the new blocks; the operator of the pool alone has that privilege. Even under the assumption that the pool operator is acting in good faith, there is still a risk of coercion, forced or otherwise, by malicious entities.

## Conclusion

The bitcoin network was thoughtfully and intentionally designed to reflect the dynamic world that it inhabits. Processes that maintain the stability of a payments network with settlement every 10 minutes, on average, continue to work as intended.

The seamlessness with which the network moves forward can be attributed in part to the periodic mining difficulty adjustments made to the block hash target. The protocol was always meant to be anti-fragile; adaptable to ever-changing conditions across several surfaces.

But the risk of hashrate centralization should not be overlooked as it poses an ongoing threat to the security of the network.

Synergistic operations, such as those miners utilizing stranded energy resources (flare gas), will need to be continually developed in order to sustain the consistent growth of global hashrate.

Thus far, the bitcoin protocol has correctly aligned the incentives of users, miners, and developers to at once work for their own interests and the interests of the system as a whole. But complacency kills — and the work has just begun.
