---
title: My Thoughts on Energy Use in Bitcoin Mining
description: "An alternative perspective on the bitcoin mining sector's energy usage."
date: March 2, 2023
---

> This post was initially drafted and published in July 2022.

A primary goal of mine in writing these posts is to produce educational content that explains the technical processes that underlie the bitcoin network. An earlier [post](https://bitdern.com/posts/priv-pub-key-sigs) dug deep into the details of private and public key pair cryptography, digital signatures, and how those technologies coalesce in bitcoin. This post will explore a prescient, cultural (moral?) topic: the energy used by bitcoin’s proof-of-work mining process.

Proof-of-work mining is an energy-intensive process; specialized hardware devices around the world expend compute resources by executing trillions of data hashes per second, in an attempt to receive a block reward subsidy as compensation for producing the next block (and securing the network, as a by-product). Critics of the system often cite that bitcoin’s global energy usage amounts to roughly 0.5% of total consumption, greater than Finland's yearly consumption. The point missed in these characterizations is that the bitcoin network is agnostic as to what form of electricity is used as an input.

When one abstracts away dogmas in the energy sector, an evaluation scheme for energy sources becomes clear. Three characteristics can be used to evaluate the usefulness of different energy sources: reliability, abundance, and cost.

For example, the wind is abundant, but it is a variable resource in nature and is not suitable for all geographical locations. Solar power is reliable in areas where sunny days are abundant, but the sun does not shine at night — and power grids need a consistent supply of base load. Both technologies mentioned above also require a significant amount of government subsidization to remain profitable enterprises (in the United States).

_What if there were a technology powered by a process that necessitated electricity utilization, regardless of the cost? And what if that process was infinitely flexible and sensitive to the demands of residential power grids?_

This post will cover:

- Recent reports from the Bitcoin Mining Council, juxtaposed against popular criticisms.
- How bitcoin mining can help to “balance” power grids by buying excess supply and having demand flexibility.
- How bitcoin mining has incentivized emission-reducing practices in the Oil and Gas industry.
- The potential for bitcoin mining to add revenue streams to any source of power generation.

## Sunlight as Disinfectant

The [Bitcoin Mining Council](https://bitcoinminingcouncil.com/) is a voluntary and open forum for bitcoin mining companies and other companies in the bitcoin industry. Their mission is to increase the transparency of bitcoin mining while educating the public on the benefits of bitcoin, and bitcoin mining. Darin Feinstein, co-founder of Core Scientific states in the Bitcoin Mining Council’s Q2 report that “sunshine is the best disinfectant,” with that in mind, let’s review some of findings.

Participants in the survey (which informed the [Q2 report](https://bitcoinminingcouncil.com/bitcoin-mining-electricity-mix-increased-to-59-5-sustainable-in-q2-2022/)) accounted for 107.7 exahash (EH) as of the end of June — this represents roughly 50% of the network’s global hashrate. The energy utilized was composed of a 66.8% sustainable power mix, and from those figures, the global sustainable power mix of the bitcoin network is estimated to be ~59.5%. The data indicates a 6% increase in the global sustainable power mix, year-over-year.

Michael Saylor, CEO, and co-founder of Microstrategy, made the following comment as a part of the report:

> In the second quarter of 2022, the hashrate and related security of the Bitcoin Network improved by 137% year-on-year while energy usage only increased 63%. We observed a 46% year-on-year increase in efficiency due to advances in semiconductor technology, the rapid expansion of North American mining, the China Exodus, and the worldwide adoption of sustainable energy and modern bitcoin mining techniques.

The figures noted by Mr. Saylor above reflect positively on the trajectory of the bitcoin mining industry — especially as it relates to the industry’s coexistence with environmental responsibility. Voluntarism is an important factor in the ethos of the bitcoin network: anyone is allowed to use the network to transact, operate their own node to verify data for themselves. The same person is similarly allowed to leave the network if ever they so choose.

Reports published by the Bitcoin Mining Council are an example of how voluntary action — coupled with intentional transparency — can work to change public perception of a seemingly opaque industry.

## Holding the Tension of Opposites

In the way that the sources of our food have been obfuscated in modern times, the average person is unaware of how electricity is available for use, on-demand.

The availability is thanks to [power grids](https://www.cfr.org/backgrounder/how-does-us-power-grid-work): a vast network of power plants, transmission lines, distribution centers, and distribution lines. In order for electricity to be available for use on-demand, there must be a consistent and reliable amount of baseload power on the grid. In the past, when fossil fuels generated the majority of grids’ base load, grid operators had an easier time balancing power demand. This is due to fossil fuel power plants having consistent uptimes — meaning that they are operational the majority of the time.

In recent years, renewable power generation sources have been added to grids as the political appetite increased, and technological advances made such integrations feasible. The proliferation of renewable power generation does, on one hand, reduce emissions. However, an unintended consequence of the trend is that certain generation sources are intermittent by nature, and increased reliance on intermittent sources increases stress on power grids.

The sun doesn’t always shine, and the wind doesn’t always blow; power grids that rely too heavily on renewables are at risk of generating too much and too little electricity, the key is balance. In order to achieve this balance, grids rely on sources of electricity that can be dispatched [on demand](https://twitter.com/level39/status/1548550264218583040), at the request of grid operators.

In practice, these sources are predominantly natural gas plants, with coal and nuclear plants making up a smaller share. All power generation facilities take time to come online, for example, nuclear generation facilities can take between 2 and 10 hours to start up:
![img](/public/powergenstarttime.png)

Consider a situation where, due to a source of renewable generation being unavailable, an operator requests a nuclear or coal plant to be activated: everything functions as intended until the renewable sources are back online. At that point, an excess supply of power exists with no buyers. In areas like West Texas where renewable generation is an increasingly larger proportion of grids, [negative](https://twitter.com/ShaunEnergy/status/1507862059169419267) energy prices have become more prevalent. When there is excess supply on the grid, operators are sometimes incentivized to pay customers to use power. Enter co-located bitcoin mining operations.

Because proof-of-work hashing is energy-intensive, bitcoin mining operations are uniquely positioned to be “buyers of last resort” for any excess power on the grid. As such, mining companies might sell insurance products (demand response programs) to grid operators that ‘hedge’ for [scenarios](https://cryptobriefing.com/bitcoin-miners-shut-down-in-texas-to-help-energy-grid/) where demand for power rises to such a point that miners voluntarily power down their machines, in return for compensation. Bitcoin mining is proving itself to be an effective means of balancing power grids: buying excess supply when no one else will and voluntarily curtailing power usage when demand is elevated.

## Bitcoin Mining’s Industrial Evolution

The Bitcoin mining industry is flexible enough to complement modern power grids by balancing out resource demand on both ends of the spectrum. But enterprise-scale bitcoin mining is a relatively new phenomenon with much yet to be uncovered with respect to the most profitable and societally beneficial business models. Because mining operations can be modular and transportable, possibilities for innovative integrations with existing systems are actively being explored. In this section, we will review some of the business models being pioneered in real time.

[Lifecycle mining](https://www.coindesk.com/policy/2021/10/11/bitcoin-mining-is-reshaping-the-energy-sector-and-no-one-is-talking-about-it/) represents the concept that the newer an operator’s mining devices are, the greater the opportunity cost associated with the device not running. Therefore, the newer a mining device is, the more money an operator will be willing to pay in order to keep it running as often as possible. Conversely, those with [older](https://twitter.com/level39/status/1548550323287064577) machines are likely to be more tolerant of downtime — perhaps from intermittent (renewable) power sources — as these operators tend to optimize for the cheapest total energy cost. Because those operators with older machines are well-positioned to purchase power from renewable sources, such generation facilities are then able to add a reliable monetization avenue for the enterprise, increasing profitability for all involved.

Power grid stability is all about balance; during periods of non-peak demand (excess electricity supply), miners can purchase abundant energy for [reduced rates](https://www.prnewswire.com/news-releases/talen-energy-corporation-announces-zero-carbon-bitcoin-mining-joint-venture-with-terawulf-inc-301347297.html) compared to the grid. This represents one side of a “hybrid model” — and as previously mentioned, this allows renewable (and other) sources of energy generation to remain profitable without relying on consistent demand from a grid. The other side of the model circles back to miners being able to curtail their energy consumption should residential or commercial demand spike unexpectedly.

In the oil and gas industry, a byproduct of pumping natural gas from oil wells is methane — among the most damaging greenhouse gas emissions. Often, these oil wells are located in relatively remote locations where it does not make economic sense to capture, transport, and market the excess methane. So operators engage in a process called “flaring,” whereby the excess methane is burned, as this is less damaging to the atmosphere than releasing raw methane.
![img](/public/flaregas.png)

Where there is a will, there is a way: since 2017, Upstream Data has been developing bitcoin mining products that are portable, modular, and perfectly suited for use cases such as this. Companies like Upstream bring in portable mining equipment, warehoused in shipping container-like enclosures. From there, they capture the excess methane and use that as a fuel source to power portable generators which then power the mining hardware. Utilizing the methane in this way is a more controlled burn, reducing emissions and adding another revenue stream for the oil well.

Proof of work hashing is not going away anytime soon, and those companies with businesses built on and around bitcoin mining will continue to innovate solutions that strike the balance between profit incentives and responsible utilization of natural resources.

## The Motion of the Ocean… Mines Bitcoin?

Over [1.3 billion](https://www.sciencedirect.com/science/article/pii/S0025326X1400366X) people live within 100 kilometers of a tropical coast, where sunlight is abundant and the effects of pollution are intimately known. Solar panels can be an option for those with the means, but as mentioned earlier, the sun does not shine at night.

_But what if there were a way to utilize the ocean’s thermal energy?_

Ocean Thermal Energy Conversion ([OTEC](https://bitcoinmagazine.com/business/bitcoin-unlocks-ocean-energy)) is a straightforward process by which the heat differentials between surface and deep sea water can be [harnessed](https://www.makai.com/ocean-thermal-energy-conversion/) to produce reliable, environmentally friendly electricity.

OTEC works on a [Rankine Cycle](https://www.youtube.com/watch?v=LJV4d4XtHuo): a working fluid — ammonia, in this case — is exposed to two chambers, one is bathed in (cold) deep seawater and the other is bathed in (warm) surface water. The working fluid vaporizes in the latter chamber and powers a turbine, connected to a generator. The fluid then returns to its liquid state after being exposed to the cold chamber, and the cycle continues.

This system is particularly attractive to island nations, or cities along the equator that are relatively isolated from developed power grids. The idea was first proposed by Jaques Arsene d’Arsonval in 1881, who was inspired by Jules Verne’s novel “Twenty Thousand Leagues Under the Sea.” The system has been [attempted](https://www.inventionandtech.com/content/other-renewable-energy-0) at scale only once, by a student of d’Arsonval’s, Georges Claude. Claude attempted to construct an OTEC plant in Rio de Janeiro, Brazil in the 1930s. Unfortunately, he would end up losing his previously amassed fortune as a result of logistical issues, storms, mistakes, and increasing costs.

Mr. Claude ran up against what is known as the [innovation valley of death](https://twitter.com/level39/status/1548550334007726081): this valley is representative of the discrepancy between resources available for basic research (proof of concept) and those available for commercialization. Small (100kW), pre-commercial OTEC facilities are not economically viable, as the electricity generated would cost around $1/kWh — nearly 10x more expensive than power from a conventional grid. These pre-commercial facilities are necessary though, to convince financiers that the risks are manageable and that a market exists.

When these facilities are scaled up, between 100–400 MW, estimates for electricity prices fall somewhere between 3 and 20 cents/kWh — much more viable. Still, most financiers will need a demonstrable proof-of-concept facility that remains operational for 2.5 years, at least. A proof-of-concept facility would need to be medium-sized, or between 5–10 MW. Estimates on the cost of such a facility are somewhere between $200–300 million and are projected to produce electricity at $0.50–1/kWh — which will not be purchased by any grid.

_What if it was possible to optimize a medium-sized facility so as to minimize overhead costs, bring down the price of electricity generated, and mine bitcoin on-site?_

This is exactly what Nathaniel Harmon, CEO of [Blockchain Solutions Hawaii](https://blockchainsolutionshi.com/) and co-founder of OceanBits Energy is working to do. Consider this: in most cases, bitcoin mining operations spend a lot of money on cooling down their machines so that they can be working harder, and longer. Consider too, that the only “waste” product of OTEC is an unlimited supply of cold water, which could be repurposed as a coolant and allow for OTEC co-located miners to run at 30–40% above capacity.

In [this interview](https://www.youtube.com/watch?t=2165&v=djoOA4fP-_I&feature=youtu.be) with Bitcoin Magazine, Harmon explained that since there would be no grid buying electricity at $0.50–1/kWh there would not be a need for the facility to be connected to the land. He estimates that savings on a connector cable (between a floating facility and a power grid) would be between $40–100 million. Plus, if it were not connected to shore, there would not be a need to obtain permits and moor the facility — saving tens of millions more. Finally, since the facility is not moored, it could move dynamically — powered by its own discharge — and graze the waters in search of the greatest temperature differentials.

Harmon and his team believe that with all of their proposed optimizations, they could operate a stranded, medium-sized facility and produce power at around 11 cents/kWh. Selling this power to a co-located bitcoin mining facility would allow this proof of concept facility to turn a profit — a feat that has yet to be accomplished in over 155 years.

## Conclusion

Time will tell if Harmon and company are able to successfully monetize their floating OTEC bitcoin mining facility. But in any case, it is a clear indication of the power that bitcoin mining has with regards to adding revenue streams to power generation projects. Environmentally-friendly energy systems are not yet completely built out, in the sense that they are able to reliably produce a consistent base load of power to supply power grids. By adding co-located mining operations into their projects, those intermittent generators, or those geographically stranded generators will always have a willing buyer of energy.

In the coming years, there is sure to be more disinformation about the amount of energy that bitcoin mining consumes and the damage to the environment associated with that energy usage. There will be more factually incorrect predictions that fail to account for the technological progress and increased efficiency of the mining process, and the strategies that mining companies execute. As of data compiled in 2021, bitcoin mining consumes [0.16%](https://twitter.com/DarinFeinstein/status/1534989327180218392/photo/1) of the world’s energy production and 0.49% of the world’s wasted energy.

None of this is to say that environmental damage resulting from energy production should be ignored — but humans are infinitely creative, and solutions like OTEC are becoming more viable. At the end of the day, bitcoin is a tool. Tools can be used skillfully or poorly, but one ought not get into the habit of assigning blame to tools.

Thank you for reading, I hope this post has provided you with a fresh perspective.
