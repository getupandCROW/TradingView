---
---

# Full Auto Trading
## Introduction
I have an example of the path I would personally take in order to develop the most robust trading system possible. At each step at least one decision is made by me in order to decide the next step and filter/focus/progress (whatever) the process. With a bot, every single decision can be tested, which leads to about a billion infinity possible combinations of indicators to analyze. 

Once you need a calculator in order to track the zeroes of something, you've gone way to big or way to small. Either way it's annoying to count zeros and commas and move decimels. 

Just now I realized that in America, we dislike moving decimel metric conversions so much that we devised fraction numerator, denominator, common, not common arbitrary number scale system. Like, get off my lawn metric man,  and pick up all those commas and decimels points your dog leaves behind. Beause I'm a red blooded American and I'll cross multiply you if you push my buttons. That sounds like I'm a calculator, but those are made in China, so you know that ain't true. I do all my maths on a 100% American made app on my Samsung phone. Ok, to be honest, I don't know who made the Google Calculator app, or where...but I did use my American #1 Best Fractions and Arbitrary Length Systems in my Freedom Brain which directed my Freedom Fingers to push those inferior foreign screen buttons...things.




## Determine most profitable trading
- frequency using
	- high / low pivots most frequent range
		- take profit set at entry of range
			- trailing stop set at exit of range
		- stop loss set using ATR with dynamic length determined by pivot lengths and last pivot

## Brainstorm Steps to Build Complete Trading Strategy from Scratch
#### 30 Positions Needed for Major Trend Areas + Strategy Entry and Exit
- [ ] 1 Day
	- [ ] Up
		- [ ] Entry
		- [ ] Exit
	- [ ] Dn
		- [ ] Entry 
		- [ ] Exit
	- [ ] No
		- [ ] Entry
		- [ ] Exit
- [ ] 4 Hour
	- [ ] Up
		- [ ] Entry
		- [ ] Exit
	- [ ] Dn
		- [ ] Entry 
		- [ ] Exit
	- [ ] No
		- [ ] Entry
		- [ ] Exit
- [ ] 1 Hour
	- [ ] Up
		- [ ] Entry
		- [ ] Exit
	- [ ] Dn
		- [ ] Entry 
		- [ ] Exit
	- [ ] No
		- [ ] Entry
		- [ ] Exit
- [ ] 15 Minutes
	- [ ] Up
		- [ ] Entry
		- [ ] Exit
	- [ ] Dn
		- [ ] Entry 
		- [ ] Exit
	- [ ] No
		- [ ] Entry
		- [ ] Exit
- [ ] 3 Minutes
	- [ ] Up
		- [ ] Entry
		- [ ] Exit
	- [ ] Dn
		- [ ] Entry 
		- [ ] Exit
	- [ ] No
		- [ ] Entry
		- [ ] Exit

#### 200 EMA Trend Line
| 1M | 15M | 1H | 4H |
|:---:|:---:|:---:|:---:|
| UP | UP | UP | UP |
| DN | DN | DN | DN |
| NO | NO | NO | NO |


#### Steps to Determine Entry / Exit for each Trend Area
1. find the <mark style="background: #FFB86CA6;">best</mark> high / low pivot points across all resolutions
	1. most frequent pivots range
	2. most profitable pivots range
	1. set Take Profit, Trailing Take Profit in order to try and raise the average trade profit
	2. set Stop Loss, Trailing Stop Loss = avg, between each H/L(L/H) pivot, dif(highest high, lowest low)
2. find a signal/indicator that can identify some of the Long entry/exit positions, [REPEAT], until all Trend areas are filled
	1. filter/focus goals and demands placed on indicator 
		1. UpTrend
		2. DownTrend
		3. NoTrend
	2. filter/focus resolutions for Trends
		
	3. filter/focus Indicators used for deciding Trends
		1. Volume
		2. [[Options Galore]] Market Trend Line
		3. Other Change/Movement Indicators 
			1. [[Directional Movement (DMI)]] ?
			2. [[Average Directional Index (ADX)]] ?
	4. find an indicator that matches up with as many strategy.entry/exit as possible, in only one focused Trend area. [LOOP until all areas of Trends are filled]
		1. find another indicator that matches up with as many as possible of the remaining unmatched strategy positions.
			1. find another indicator that matches up with as many as possible of the remaining unmatched strategy positions. Until all strategy positions have an indicator match.
	5. set priority order for all indicators so that the best matching indicator is used for each strategy position change.
		1. create Pyramiding or Safety Order signals using opportunities when multiple indicators signal at different times, and increase the overall profitability of the current open trade

### Strategy Entry/Exit Heirarchy Order Confirmations

##### if Signal(**1D**)
if Signal(4H)
		if Signal(1H)
			if Signal(15M)
				if Signal(3M)
					Place **1D** Order

##### if Signal(**4H**)
if Signal(1H)
		if Signal(15M)
			if Signal(3M)
				Place **4H** Order

##### if Signal(**1H**)
if Signal(15M)
		if Signal(3M)
			Place **1H** Order

##### if Signal(**15M**)
if Signal(3M)
		Place **15M** Order



## Potential Indicators List
1. [[Accumulation / Distribution]]  
2. [[Advance-Decline Ratio]]
3. [[Average Directional Index (ADX)]]  
4. [[Average True Range (ATR)]] 
5. [[Average True Range Percent (ATR%)]]  
6. [[Bollinger Bands (BB)]]
7. [[Camarilla Pivot Points]]  
8. [[Chaikin Money Flow (CMF)]]
9. [[Chaikin Oscillator]]  
10. [[Choppiness Index (CI)]]
11. [[Classic Pivot Points]]
12. [[Commodity Channel Index (CCI)]]  
13. [[Coppock Curve (CC)]]  
14. [[Demark Pivot Points (DPP)]]
15. [[Directional Movement (DMI)]]
16. [[Donchian Channels (DC)]]
17. [[Ease of Movement (EOM)]]  
18. [[Elliott Wave (EW)]]
19. [[Exponential Moving Average (EMA)]]
20. [[Fibonacci Moving Average (FMA)]]  
21. [[Fibonacci Pivot Points (FPP)]]  
22. [[Force Index (FI)]]
23. [[Historical Volatility (HVOL)]]  
24. [[Hull Moving Average (HMA)]]
25. [[Kaufman's Adaptive Moving Average (KAMA)]]
26. [[Keltner Channels (KC)]]
27. [[Know Sure Thing (KST)]]
28. [[KST Oscillator (KST)]]
29. [[(MACD)]]
30. [[Mass Index (MI)]]
31. [[Momentum (MOM)]]
32. [[Money Flow Index (MFI)]]
33. [[On-Balance Volume (OBV)]]  
34. [[Parabolic Stop-and-Reverse (PSAR)]]
35. [[Price Volume Trend (PVT)]]
36. [[Rate of Change (ROC)]]  
37. [[Relative Strength Index (RSI)]]  
38. [[RSI-Stochastic Oscillator]]
39. [[Simple Moving Average (SMA)]]
40. [[SMI Ergodic Oscillator]]
41. [[Stochastic Oscillator]]
42. [[Supertrend]]
43. [[Traditional Pivot Points]]
44. [[Triangular RSI]]
45. [[True Strength Index (TSI)]]
46. [[True Range (TR)]]
47. [[(TRIX)]]
48. [[Ultimate Oscillator (UO)]]
49. [[Volume Oscillator (VO)]]
50. [[Vortex Indicator (VI)]]
51. [[Volume Weighted Average Price (VWAP)]]
52. [[Weighted Moving Average (WMA)]]
53. [[Wilder's Moving Average]]
54. [[Woodie Pivot Points (WPP)]]


## Notes
- Weighted Signals 
	- Dynamic Decisions
- 

### For Every Coin Pair
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
	- Best indicator short list precompiled 
- Custom Weighted Scoring of Pivot Filters and Indicator Short List
	- Filter Total Score By 3+1 Range split
		- White (11+)                     -->     Hot       👌 
		- Green (7-10)                 -->     Great    👍 
		- Yellow (4-6)                 -->     Wait      ✋️ 
		- Red (0-3)                      -->     Nope    👎




## Footer