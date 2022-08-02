# on-chain-betting

## Problems to solve + abstract

The sports betting market is expected to be over $100B in market size by 2025

Current betters require users to work with bookies or centralized services to deposit
funds, place bets, and recieve payouts with incredible amounts of trust. Bringing this
on-chain is incredibly logical, and will mitgate need for trusted third parties

To bring this on-chain, two key features need to be solved for:

#### outcome-based oracles

This has been solved for. Optimistic oracles like UMA can provide cost-effective solutions
for on-chain betting, which has been seen in projects such as Polymarket 

#### determining spreads

on-chian payouts are currently done in parimutel setting this is bad and leads to low liqudity
lines and if not, there is usually significant arb opportunites between on-chain lines and vegas
odds. Given vegas sportsbooks have been largely profitable, I propose a consensus mechanism that takes
the average line of the top n major vegas sportsbooks to determine lines 
 
#### sufficient liquidity mechanisms across books

perhaps the biggest issue plaguing on-chain betting currently is insufficient liquidity.
Users currently are not incentivized to place sizeable bets (most polymarket bets
liqudity < $100k liqudity).

Users should be able to LP across all bets / lines at the same time


