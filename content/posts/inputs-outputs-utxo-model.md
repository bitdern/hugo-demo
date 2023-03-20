---
title: Bitcoin Transactions - Inputs, Outputs, and the UTXO Model
description: "Exploring the building blocks of bitcoin transactions."
date: December 12, 2022
---

Bitcoin is a global, permissionless, peer-to-peer network that allows users to construct transactions in order to send value anywhere on the planet. If one wishes to understand the bitcoin network, it is important to understand the individual ledger entries which make up blocks: transactions.

This piece will cover:

- Transactions on the bitcoin network — what are they, and how do they work?
- The significance of transaction outputs, in bitcoin.
- An overview of the “UTXO” model and why it is important for bitcoin.
- Output locks as a means to safeguard against double-spending.

## Bitcoin Transaction Flows

A transaction on the bitcoin network is a single line of data that contains information on the amount being sent, the account it is being sent from and the account it is being sent to. When a user makes a transaction, the transaction data is transmitted to the bitcoin network — via a node — which then relays the transaction to peer nodes until it has proliferated the entire network.

A few points before going further:

1. In bitcoin parlance, [node](https://learnmeabitcoin.com/beginners/nodes) is a concise way of referring to a computer that is running a version of the bitcoin software and relaying information around the network.

2. Nodes are connected to other computers running the same program, creating a network.

3. Before relaying data across the network, nodes validate that a particular transaction, or group of transactions (block), complies with a programmed set of rules to establish transaction validity.

4. Anyone can run a node on the bitcoin network; it can be done with an old laptop, desktop, or dedicated hardware device. All that is required is an internet connection and sufficient storage capacity to maintain a copy of the blockchain.

In summary, nodes have three main functions: follow rules, share information and keep a copy of confirmed transactions (the blockchain).

Once a node has validated and propagated the transaction throughout the network, the transaction sits in a queue called a Memory Pool, or [mempool](https://mempool.space/). These queues serve as waiting areas for transactions yet to be added to the newest block. Note that even though the transaction has been deemed valid by nodes, it has yet to be added to a block, and thus, the transaction’s status is ‘pending’ at this point.

This is where the mining process comes in — miners have specialized nodes whose purpose is to batch pending transactions into blocks, following a resource-intensive data compression process. While miners (or pools of miners) receive a reward for mining the latest block, they are also incentivized by transaction fees — miners tend to give preference to transactions with higher fees.

At the point when a transaction is mined into a block, its status moves from ‘pending’ to ‘confirmed.’ Three confirmations are generally viewed as the minimum threshold for a bitcoin transaction to be considered ‘settled’.

## How do Bitcoin Transactions Work?

Functionally, a bitcoin address can be conceptualized as an account number that holds a certain amount of bitcoin and keeps track of each transaction that the address participates in. However, the process of a [transaction](https://learnmeabitcoin.com/beginners/transactions) is not the same as taking a handful of coins and moving them from one jar to another. When you want to send bitcoin, you are taking whole amounts (that you’ve previously received) and using them to send a new amount to a new address.

So in effect, you receive bitcoin in batches and then use those batches to create new batches to send to other people. Those batches are called outputs.

In a situation where the total of the batch you are sending is more than the amount you wish to spend: in this scenario, you would create an additional output in the transaction — called “change” — and send this output back to yourself. Once an address has been used as a transaction input, that input address is effectively dead, as the bitcoin has been sent to a new address (output).

While it is technically possible to re-use a bitcoin address, the practice is highly discouraged as doing so will tend to associate a user’s personal information with a set of transactions, addresses, etc.

Each output is locked by an output lock, which prevents others on the network from spending funds they do not control. These locks can only be unlocked by a private key, which is associated with ownership of a bitcoin address. Nodes will only validate transactions with inputs that are unlocked; any locked inputs will result in a rejected transaction.

## The Significance of Bitcoin Transaction Outputs

Bitcoin’s transaction system involves sending and receiving batches of bitcoin, called outputs.

Some examples:

1. Say that you are a bitcoin miner, have successfully managed to mine a block, and have received a block reward of 25 bitcoin (sent to an address you’d previously specified). Later that day, you wish to spend 1 bitcoin on a car, at a dealership that accepts bitcoin as payment. In order to make that spend, you would use the _entire_ 25 bitcoin output as an input and create two new outputs: a 1 bitcoin output to an address controlled by the dealership, and a 24 bitcoin output to a new address that you control (disregarding transaction fees).

2. This time let’s say that you have been saving up different amounts of bitcoin in outputs ranging from 0.3–to 0.001. Now, in order to make a 1 bitcoin transaction, you would have to gather up as many smaller outputs as necessary to equal or be larger than 1 bitcoin. And again, if the amount of inputs is greater than your intended spend, you would create an additional output (change) and send that back to yourself.

Bitcoin developer and educator [Greg Walker](https://twitter.com/in3rsha) puts it this way:

> The reason why transactions work this way is because it’s an easier and more secure way of doing it from a programming perspective.

What is unique about the bitcoin transaction model is that it places a high significance on transaction [outputs](https://learnmeabitcoin.com/beginners/outputs), as opposed to inputs. The reason for this is that the address of output represents the potential to spend in the future; outputs that have yet to be spent are referred to as [UTXOs](https://learnmeabitcoin.com/technical/utxo) — unspent transaction outputs. When a wallet displays a bitcoin balance, you are seeing the sum of all UTXOs that your wallet controls (via private keys).

A critical factor not covered in either example are transaction fees. Without a transaction fee, the intended transaction would likely sit idle in a mempool for quite some time before getting mined into a block.

This is because transaction fees give a transaction priority: the larger the transaction fee, the greater a miner’s willingness to include it in the next block.

Miners are incentivized by the block reward AND transaction fees. Any amount that’s left over in a transaction (inputs minus outputs) gets picked up by a miner — so if you constructed a transaction and forgot to create a change output for yourself, the miner would pick up the difference regardless of the amount.

## Bitcoin Output Locks

Output locks are the mechanisms that protect funds from being spent by any party that does not control the addresses where those funds are located. An [output lock](https://learnmeabitcoin.com/beginners/output_locks) is a set of requirements placed on output, these requirements must be met/satisfied before that output can be used in a transaction. Output locks are unlocked by private keys, which can only be accessed by the owner of a particular address.

Back to the above examples, when you “send” bitcoin to the car dealership, you are creating two new outputs: one of which is the change that will be locked to an address that you control, and the other locked to an address that only the dealership has private keys to unlock. Because the dealership controls the private keys for this address, they effectively own that new bitcoin output.

When making transactions, one never really “sends” bitcoin anywhere; in reality, constructing a transaction creates new outputs (with new locks), and sends that transaction data into the network, where it sits and waits to get mined into a block.

Practically, the bitcoin blockchain can be visualized as a storage unit system for transaction outputs. When you send bitcoin, you reference the outputs in the blockchain that you have private keys to unlock — once the transaction gets mined into a block, the outputs you used as inputs will be unusable from then on, as new outputs (UTXOs) have been created.

Within the global bitcoin ledger, there exists a query-able [UTXO set](https://river.com/learn/terms/u/utxo-set/), which tracks the addresses and amounts of each UTXO in existence. The sum of the amounts of each UTXO equates to the total supply of existing bitcoin at that point in time.

## Conclusion

Bitcoin was designed to be reliable, secure, and trust-minimized — the transaction system of inputs, outputs, output locks, and UTXOs is an elegant way to maximize the performance of the global ledger while minimizing operational complexities.

To summarize:

- When “sending” bitcoin, the bitcoin doesn’t “go” anywhere else: the UTXOs used as inputs in the transaction create new outputs, which are locked to an address that the user on the other side of the transaction controls.

- Outputs (UTXOs) are locked by output locks, which restrict funds being spent — unless a user possesses the private keys, which prove ownership of the particular address.

Lastly, avoid [address reuse](https://en.bitcoin.it/wiki/Address_reuse) as it reduces the privacy and security of both parties, as well as the future holders of those funds.
