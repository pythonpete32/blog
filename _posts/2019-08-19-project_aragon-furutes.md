---
title: "Project: Aragon Futures Exchange"
published: true
---

Aragon futures Exchange allows users to speculate long or short on the future price of ANT with leverage and without any counterparty risk. Shorting ERC20 assets is very difficult at the moment. Further more, the few exchanges that offer the option are centralized and expose both party's to counterparty risk.

Giving market makers the ability to go short on an asset allows them to hedge there risk, earn fixed income and thus offer more liquidity to ANT. Futures contracts also allow speculators to gain leverage and exposure to more volatility.

<br>

## [](#header-2) How does it work?

**Alice** is a market maker providing liquidity for ANT on 0x protocol. She uses her inventory of ANT to earn the bid-ask spread. Alice has no opinion on the future price of ANT she simply wants to remain delta neutral on her inventory of ANT (i.e. she wants the value of her ANT to remain the same in relation to DAI)

**Bob** is a trader, he believes ANT is undervalued and is about to start a massive bull run. He has an inventory of DAI he uses to make speculative trades

1. On the 1st of July, **Alice** buys 1,000 ANT at 10 DAI per token
2. She immediately places a sell order for 1,000 ANT at 11 DAI (expiring on the 1st of August) on the Aragon futures exchange. depositing 500 ANT as collateral
3. **Bob** sees the futures order, even though the price is 10% higher than the spot price (today's price), he thinks the price will be much higher by 1st August, he doesn't want to lock up all his DAI buying at spot, so he is happy to buy the futures contract.
4. **Bob** buys the 1,000 ANT futures contracts depositing 5,500 DAI as collateral
5. At this point, **Alice** has locked in 1,000 DAI profit and she has 500 ANT inventory to trade with. **Bob** has locked in a price of 11 DAI and has 5,500 DAI to trade with \*\*
6. On the 1st of August, the spot price of ANT is 14 DAI. The value of the **Alice** ANT is now 14,000 DAI however she has promised to sell it to **Bob** at 11,000 DAI. She now has 12 hours to send the rest of the ANT to futures exchange contract or she will forfeit the collateral and the claim on the DAI. She sends the remaining 500 ANT.
7. **Bob** sends 5,500 DAI to fulfil his obligation. During the month he made an additional 3,000 DAI trading with the this 5,500 DAI which offset the 1,000 DAI premium he paid for the futures contract
8. Both **Alice** and **Bob** withdraw their purchases from the exchange
9. **Alice** is happy. She made a profit and hedged her risk
10. **Bob** is happy he made a bigger profit than he would have simply bought at spot

<br>
## [](#header-2) Deploy to rinkeby

<br>

_**DO NOT DEPLOY TO MAINNET, THIS CODE HAS NOT BEEN AUDITED**_

<br>

### [](#header-3) Pre-requisits


- nodejs
- trufflesuite
- git


### [](#header-3) 1. download the repository

```bash
git clone https://github.com/pythonpete32/aragon-futures.git
```

<br>

then install the dependencies

```bash
npm install
```

<br>

### [](#header-3) 2. setup truffle config
