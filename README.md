# Jane Street ETC - October 14, 2023

Jane Street's Electronic Trading Challenge (ETC) is a day-long programming contest where participants compete for cash prizes in a simulated market scenario. In the first competition, our team placed 5th, and in the second competition, we achieved 3rd place out of 20 teams.

## Team: Yeouido Street

- Jeounghui Nah ([@justiceHui](https://github.com/justiceHui))
- Serin Kim ([@dsstar-codes](https://github.com/dsstar-codes))
- Sion Kang ([@Yaminyam](https://github.com/Yaminyam))
- Wookyung Jeong ([@manoflearning](https://github.com/manoflearning))

## Preparation

Our team had no experience with quantitative trading but possessed strong skills in algorithmic problem solving and software development. 
To prepare, we researched past competition records, referencing the following sources:
- [JaneStreetETC22](https://github.com/EnriqueKhai/JaneStreetETC22)
- [Jane Street - NUS Virtual Electronic Trading Challenge (ETC)](https://github.com/college-ave-east/jane-street-etc)
- [A Technical Deep Dive Into the Jane Street ETC](https://medium.com/@benhubsch/a-technical-deep-dive-into-the-jane-street-etc-5fbcdddc20db)

## During the Competition

### Bond Strategy

The fair price of a bond was fixed at $1000. Initially, we attempted a strategy of buying all bonds priced below $1000 and selling them at $1001. Due to short selling, it was also possible to sell bonds at $1001 without purchasing them. This Bond Strategy earned dozens of dollars for each round.

### Main Strategy

We purchased all assets at a price ‘slightly’ below the fair price and sold them at a price ‘slightly’ higher.
To predict the fair price, we relied on the last trade price.

However, determining the exact buy and sell thresholds, i.e., finding the optimal delta, was a challenge. 
Initially, following [JaneStreetETC22](https://github.com/EnriqueKhai/JaneStreetETC22), we placed a buy order at ```fair_price - 1``` and a sell order at ```fair_price + 1```. However, this delta resulted in losses. Next, we set the delta at ```+/- 2```, resulting in earnings ranging from $3000 to $12000 per round.

We experimented with different delta values on the test server, but we couldn't identify a more efficient delta before "The Final Hour".

### Smarter Market

About 3 hours after starting, there was a significant market shift, causing our strategy to incur immediate losses of $10000 per round.

To mitigate losses when market conditions deviated from our strategy, we hypothesized that holding or shorting assets too aggressively led to losses. According to our strategy, if the market continually rose, we kept selling short, and if it continually fell, we continued to buy. We addressed this by imposing a strong limit on the number of assets we held for each asset, preventing them from exceeding 30 or going below -30. As a result, we avoided large losses but also missed out on large profits.

### The Final Hour

During "The Final Hour", we removed the count limit and set the delta to ```+/- (fair_price // 300)```. This allowed us to earn about $8000 per round once again. 

One interesting discovery was that in the last few rounds, we maximized our profits by alternating between ```+/- (fair_price // 300)``` and ```+/- 2```. When the profit of ```+/- (fair_price // 300)``` was not substantial, we manually switched to ```+/- 2```, resulting in immediate profit, and vice versa.