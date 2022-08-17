# on-chain, aggregated liquidity for predictions markets

## Problems to solve + abstract

Current sports books require bettors to work with bookies/centralized services to deposit
funds, place bets, and recieve payouts, requiring an incredible amount of trust. For an industry
expected to reach $100B in market size by 2025, bringing this on-chain mitgates the need for trusted
third parties, and provides lucrative opportunites for market makers.

*Note:* while this primarily focuses on sports betting, in practice this could be abstracted
to other markets (GMX explores similar pooled liqudity concepts in the derivitives space, 
for example)

To bring this on-chain, three key features need to be solved for:

### 1) outcome-based oracles

This has been solved for. Optimistic oracles like UMA can provide cost-effective solutions
for determining results of on-chain markets, and has been seen in production in applications
such as Polymarket 

### 2) determining spreads / payouts

on-chain spreads are most frequently done through parimutel betting parameters for individual markets.
This disincentivizes users to place bets, since bets "of size" are not profitable when
there aren't counterparties involved in the market. There are also usually significant arb opportunites
between on-chain lines of this style and vegas odds. Instead, we propose 
a consensus mechanism that takes the average line of the top `n` major vegas sportsbooks to
determine spreads. (or even easier , one could determine the spread off of one provider, 
such through leveraging Fanduel's api)

While this sounds intuitive, most crypto-native platforms have chosen not to implement in this fashion
due to increased negative exposure within the book. However, this risk can be significantly mitigated through 
"risk amortization," as described below
 
### 3) aggregating liquidity across markets + lines 

Perhaps the biggest issue hurting on-chain markets currently is insufficient liquidity. This is
due to users only LPing for individual markets. 

The notable "change" to this mechanism would be in allowing users to LP across all lines at the same time.
This would allow users to place "bets of size" on low liquidity markets, which would be paid out through
a centralized pool. Since parties would place many -EV bets across all markets, risk would be distributed across
the sum of all lines.

*Mechanism thoughts*:
- enforce a "max bet" size equal to 1/100th of `total_liquidity - LP exposure`. This would ensure lines are never adjusted
- it is worth pointing out `total_liquidity - LP exposure >= total_bets_placed` since counterparties could place bets on other side of the same spread
- book would never be at risk of losing more money than provided under these parameters

*Incentives*:
- all lines are -108 rather than -110, LPers still take massive profits bc 1600 BP spread, users get the best
odds in town
- could implement fairly basic tokenomics where users get better lines if betting w our token

#### The "generalized protocol" + use additional cases

We can abstract the three features above into a more generalized expression:
Leveraging oracles and aggregated liquidity across markets to eliminate slippage for long-tail + exotic assets

Examples:
- GMX, uses chainlink oracles + pooled liquidity across markets for 0 slippage derivatives
- Morpho, by building a p2p market on top of a liquidity pool, users get better rates while not guarunteeing counterparties 
