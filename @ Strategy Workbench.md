# Strategy Workbench
Backtesting:: [[@ TradingView]]
Broker:: [[FTX]]
TradingBots:: [[3Commas]]

***

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

***

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

*** 

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

***

```js
// === BUY LONGS
//if validsomOpnLngPos
//    // Enter 1st Long Position with largest TP and SL
//    if maxDn34
//        if allRising
//            strategy.entry(id = "Long Entry 1", direction = strategy.long, qty = 75, comment = "", alert_message = "")
//else if somLngIsActive
//    // Enter 2nd Long Position with smaller TP and SL
//    if maxDn34
//        if allRising
//            strategy.entry(id = "Long Entry 2", direction = strategy.long, qty = 75, comment = "", alert_message = "")
//else if somOpnLngPos
//    // Enter 1st Long Position with largest TP and SL
//    if maxDn34
//        if allRising
//            strategy.entry(id = "Long Entry 1", direction = strategy.long, qty = 75, comment = "", alert_message = "")

var float priceClose = close
var float priceLow = low
var float priceHigh = high
var float tp1 = (inpTP * .01 * priceHigh) + priceHigh // limit in strategy.exit
var float sl1 = priceLow - (inpSL * .01 * priceLow) // stop in strategy.exit
var float tpts1 = (inpTPTS * .01 * tp1) + tp1 // limit in strategy.exit
var float slts1 = sl1 - (inpSLTS * .01 * sl1) // stop in strategy.exit
var bool tp1Passed = high > tp1
var bool sl1Passed = low < sl1
var bool tpts1Reached = high > tpts1
var bool slts1Reached = low < slts1
```