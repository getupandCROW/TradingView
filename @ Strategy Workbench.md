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




