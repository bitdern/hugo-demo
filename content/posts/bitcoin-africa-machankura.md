---
title: Bringing Bitcoin Adoption to Africa
description: "An overview of the SMS-based bitcoin transmission protocol, Machankura."
date: February 28, 2023
---

Every now and then, I stumble across an idea or protocol that is so exciting — revolutionary, even — that I stop what I’m doing and make sure to cover it.

This post will cover just such a protocol.

Speaking as someone who lives in a relatively developed country, it is clear that the importance of a decentralized money, and a peer-to-peer payment network is taken for granted.

In the developed world, we are fortunate enough to have experienced a proliferation of internet-connected devices, well-maintained internet infrastructure, and many pseudo-bank applications built on top of the internet stack. These aspects democratize finance, in a sense. One need not trust that their bank teller is giving them the correct balance information — we have countless solutions for this.

Consider those developing nations though, where currencies are prone to hyperinflation, internet infrastructure is poor or nonexistent, and the proliferation of smart devices has not nearly reached a critical mass. For these nations, bitcoin is an obvious solution to many of their problems, but bitcoin being an “internet-native” form of money creates a seemingly insurmountable obstacle to those who wish to use the network.

That is, until recently…

## Bitcoin for Africa

Bitcoin is a fantastic tool for individuals interested in creating more sovereignty in their financial lives, but again, without an internet-connected device, progress along that path is greatly hindered.

Apart from South Africa, Pew Research [estimates](https://www.pewresearch.org/global/2018/10/09/majorities-in-sub-saharan-africa-own-mobile-phones-but-smartphone-adoption-is-modest/) indicate that a vast majority of sub-Saharan Africans own basic, [feature phones](https://en.wikipedia.org/wiki/Feature_phone) — as opposed to smartphones, or internet-connected devices of any kind. Feature phones are so ubiquitous that most Africans use [USSD](https://theexchange.africa/tech-business/ussd-driving-digital-and-financial-inclusion-in-africa/) and SMS portal services (text message-based services) in order to access finances, remit money, and purchase goods and services.

According to Caribou Digital, a South African research group, approximately 94% of financial transactions on the African continent are processed via SMS-based services, compared to the remaining 6% which are executed in-app. The user behavior is well-understood and practiced daily, and savvy developers have taken note.

[Machankura8333](https://8333.mobi/) is an SMS-based bitcoin service built by South African developer [Kgothatso Ngako](https://twitter.com/440UrPp) “KG.”

This project represents, to my knowledge, the first cogent attempt to enable access to bitcoin via feature phones.

**Fun fact: ‘machankura’ is South African slang for ‘money.’**

This [article](https://cointelegraph.com/news/bitcoin-without-internet-sms-service-allows-sending-btc-with-a-text) from Cointelegraph provides excellent context to this innovation: while the number of feature phones in Africa is nearly double the number of people, smartphone proliferation is not sufficient for a protocol to bank on its users having internet access. In addition, Machankura’s founder KG realized that in order for Africans to appropriately utilize the bitcoin network, they must be provided with the resources to learn about it.

With this in mind, KG created the [Exonumia](https://exonumia.africa/int/en/) project, an open-source, African language translation project in which dozens of articles, books, and other educational bitcoin content are translated. There are translations for 28 languages at the time of writing.

As the project gained momentum, KG decided that he would tackle the fundamental issue: how to access the bitcoin network without internet access.

## Making Machankura

Enabling feature phones to connect to the bitcoin network might seem an insurmountable task, but the bitcoin network is relatively malleable and can be made to fit a variety of use cases, some of which are extremely complex and involved. However, at its base, the bitcoin network is a decentralized ledger system — it is humans who assign a monetary value to data ownership of varying degrees on the bitcoin network.

KG has designed the protocol to function as simply as possible.

1. First, a user begins by dialing a string of numbers, which varies depending on the country they are located in.

At the moment, Machankura is available in 8 countries (Ghana, Kenya, Malawi, Namibia, Nigeria, South Africa, Uganda and Zambia) — and enabling the service in more countries is a top priority.

2. After the user makes the initial dial, they will be prompted with a menu of options where they can learn more about bitcoin (linking to Exonumia), or register an account.
3. All that is required to register an account is a user-generated, 5-digit pin.
4. Once registered, another menu is presented: Send Bitcoin or Receive Bitcoin.

_How does Machankura work, from a technical perspective?_

Once registered, the user’s phone number is registered, Machankura automatically assigns the user a lightning address based on their phone number (e.g. 27123456789@8333.mobi).

For privacy-conscious users who would prefer not to expose their phone number in their lightning address, customizable usernames are available (e.g. bitdern@8333.mobi). This feature is enabled through the USSD menu, the selected username will be cross-referenced against a database of established usernames — if the proposed name is not being used, it becomes the user’s pseudonym.

The Machankura protocol is built on the lightning network, and comes “out of the box” with connections to any other lightning-enabled transaction service. This means that users of [Blixt Wallet](https://blixtwallet.github.io/) in Sweden, or [Bitcoin Beach](https://galoy.io/bitcoin-beach-wallet/) Wallet in El Salvador are able to send and receive bitcoin from Africans using Machankura from their feature phones.

## Integrations and Implications

Machankura has integrated with [Bitrefill](https://www.bitrefill.com/), a company that allows users to spend their bitcoin on gift cards, groceries, entertainment experiences, prepaid phones, and mobile phone top-ups (which Machankura users are likely quite familiar with). Along with this partnership, Machankura has also [integrated](https://twitter.com/Machankura8333/status/1557290245330198528?ref_src=twsrc%5Etfw%7Ctwcamp%5Etweetembed%7Ctwterm%5E1557290245330198528%7Ctwgr%5E4e81970cfc9d9b3f3fcd3e3c18b37baa33a21aad%7Ctwcon%5Es1_&ref_url=https%3A%2F%2Fcointelegraph.com%2Fnews%2Fbitcoin-without-internet-sms-service-allows-sending-btc-with-a-text) with mobile voucher services [1voucher](https://www.1voucher.co.za/) and [Azte.co](https://azte.co/#about).

Users can exchange their local currency for Bitcoin by purchasing a voucher from either of these vendors (in stores that carry them). Once the voucher is paid for and in their possession, the user simply enters the specified code on the voucher into the “Receive Bitcoin” prompt of their Machankura wallet, and presto! Additional funds have been credited to their lightning wallet.

The implications for Machankura and the integrations established thus far are boundless. This protocol represents an incredible step forward for bitcoin — no longer does a user need to be connected to the internet to benefit from the network.

In this twitter [thread](https://twitter.com/Machankura8333/status/1564570890578296837), Machankura founder KG walks through an afternoon’s quest to purchase as many bearer vouchers as possible in the small village of Moloto, South Africa. KG successfully exchanged local fiat currency for bitcoin bearer vouchers at 7 of the 8 stores he tried — a successful proof of concept!

## Conclusion

Too often, I find that criticisms of the bitcoin network’s utility are unfounded: bitcoin does not need to be utilized in highly complicated, risky financial schemes and structures. Bitcoin is a straightforward, decentralized ledger system that can be used as a form of money.

From the perspective of the developing world, and with respect to bitcoin’s monetary properties, if users are able to send and receive bitcoin, and use that bitcoin to pay for goods and services, then the network is functioning as designed.

This piece was intended to highlight an exciting application of bitcoin software, one that I believe democratizes the network, and is truly representative of “grass-roots adoption.”

I hope that this content has piqued your interest, and I encourage readers to follow KG and the [Machankura](https://twitter.com/Machankura8333) team as they continue to build.
