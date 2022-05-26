# Strategy Workbench
Backtesting:: [[@ TradingView]]
Broker:: [[FTX]]
TradingBots:: [[3Commas]]

---

```
if ZL < close[Day_View]
if ZL < close[4H_View]
	if ZL < close and ZL[1] < ZL[0]   // negative and increasing
		if currentPrice < currentPrice open   // currently red candle
			if (AVSL[LM] crossover(close) or AVSL[LM] > close) and (VWMA crossover(close)  or VWMA > close)    // 
			
if ZL < close[1M] and ZL < VWMA and ZL < SMI_EQ
if ZL < close and ZL[1] < ZL[0]   // negative and increasing
	if currentPrice < currentPrice open   // currently red candle
		if (AVSL[LM] crossover(close) or AVSL[LM] > close) and (VWMA crossover(close)  or VWMA > close)    // 



if ZL > close and ZL[1] < ZL[0]   // positive and increasing




if ZL > close and ZL[1] > ZL[0]   // positive and decreasing




if ZL < close and ZL[1] > ZL[0]   // negative and decreasing
```



For Every Coin Pair
- Every 1H/15M/3M  ? $ $ ?
    - ohcl values
    - values for all of the indicators
- filter out DN and NO trending coins
	- Watch DN Trends that are in Luc ? Bottom-Bottom
- Filter with pivots
	- Floor Trading
	- Zig Zag High Low
	- BB
	- Use database and precompile data
- Remaining coins, check against indicator list
	- Best indicator short list previously compiled 
- Custom Weighted Scoring of Pivot Filters and Indicator Short List
	- Filter Total Score By 3+1 Range split
		- White (Green+) Hot👌 
		- Green () Great 👍 
		- Yellow () Wait ✋️ 
		- Red () Nope 👎

