# Strategy Workbench
Backtesting:: [[@ TradingView]]
Broker:: [[FTX]]
TradingBots:: [[3Commas]]

---

```js
//@version=5
indicator("while")
// This is a simple example of calculating a factorial using a while loop.
int i_n = input.int(10, "Factorial Size", minval=0)
int counter   = i_n
int factorial = 1
while counter > 0
	factorial := factorial * counter
	counter   := counter - 1

plot(factorial)
```

```js
var a = close
var b = 0.0
var c = 0.0
var green_bars_count = 0
if close > open
	var x = close
	b := x
	green_bars_count := green_bars_count + 1
	if green_bars_count >= 10
		var y = close
		c := y
plot(a)
plot(b)
plot(c)
```

```js
//@version=5
indicator("for")
// Here, we count the quantity of bars in a given 'lookback' length which closed above the current bar's close
qtyOfHigherCloses(lookback) =>
	int result = 0
	for i = 1 to lookback
		if close[i] > close
			result += 1
	result
plot(qtyOfHigherCloses(14))
```

```js
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

