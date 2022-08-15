# pooled liquidity on chain betting

## Problems to solve + abstract

The sports betting market is expected to be over $100B in market size by 2025 

Current betters require users to work with bookies or centralized services to deposit
funds, place bets, and recieve payouts with incredible amounts of trust. Bringing this
on-chain is incredibly logical, and will mitgate need for trusted third parties

To bring this on-chain, three key features need to be solved for:

### outcome-based oracles

This has been solved for. Optimistic oracles like UMA can provide cost-effective solutions
for on-chain betting, which has been seen in projects such as Polymarket 

### determining spreads

on-chain spreads are most frequently done through parimutel betting parameters for individual markets.
this is incredibly inneficient that leads to very low liqudity, since bets "of size" are not profitable since
there aren't counterparties to assume the other side. (There are also usually significant arb opportunites
between on-chain lines and vegas odds). Given vegas sportsbooks have been largely profitable, I propose 
a consensus mechanism that takes the average line of the top `n` major vegas sportsbooks 
(or even to just base line off of one provider, such through leveraging Fanduel's api)

While this sounds intuitive, most crypto-native players have chosen not to implement this due to increased
negative exposure within the book. This risk can be significantly mitigated through "risk dispersion," as
described below
 
### sufficient liquidity mechanisms across books

perhaps the biggest issue plaguing on-chain betting currently is insufficient liquidity.
Users currently are not incentivized to place sizeable bets, given spreads change significantly
with the placement of the bet (most polymarket bets have liqudity < $100k liqudity). This is because
market makers only LP for individual markets / lines. 

The notable "change" to this mechanism would be allowing users to LP across all lines at the same time.
This would allow users to place "bets of size" on low liquidity markets, as parties would place many
-EV bets across all markets.

*Mechanism thoughts*:
- enforce a "max bet" size equal to 1/100th of current LP exposure. This would ensure lines are never adjusted
- it is worth pointing out LP exposure != total assets in pool, since counterparties could place bets on other
side of the same spread

*Incentives*:
- all lines are -108 rather than -110, LPers still take massive profits bc 1600 BP spread, users get the best
odds in town
- if users bet w token there is no spread (higher risk for LPs but we make more money bc buying our token)


