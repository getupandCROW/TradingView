# NNFX Strength System - User Guide

URL:: [mql5.com](https://www.mql5.com/en/blogs/post/744029#:~:text=NNFX%20Strength%20System%20is%20a,on%20the%20MQL5%20Market%20here.)

author:: "Benjamin Joshua Nash"

22-27 minutes

---

NNFX Strength System is a trend following multi-currency trading system that follows the No Nonsense Forex method to maximise profits and simplify trading. The indicator can be traded alone or in combination with other indicators in an NNFX algorithm. It is available on the MQL5 Market [here](https://www.mql5.com/en/market/product/67194). 

### How does it work?

1. NNFX Strength indicator scans 28 Forex pairs to determine the relative strength of the 8 major currencies within a given period, these are normalised as percentages from 0 to 100. 
2. The resulting currency lines are smoothed by a definable moving average and data is extracted from the currency relationships to give momentum-based trend and trade signals. 
3. By switching through the 28 currency pairs you can quickly see whether a trade opportunity exists to act on, the recommended StopLoss and TakeProfit levels are also shown. 
4. Once trades are placed it is easy to manage their progress with the data shown visually, telling you to either hold or exit.

*Currency pairs scanned are all combinations of EUR, USD, GBP, CHF, CAD, AUD, JPY, NZD only.*

[![NNFX Strength CADJPY](https://c.mql5.com/6/887/Screenshot-3-CADJPY__1.png "NNFX Strength CADJPY")](https://c.mql5.com/6/887/Screenshot-3-CADJPY.png "https://c.mql5.com/6/887/Screenshot-3-CADJPY.png")  

### 

What is the No Nonsense Forex (NNFX) method?

The No Nonsense Forex way of trading has become increasingly popular as a method of dramatically improving trade performance and turning average or losing traders into prop trading professionals. VP, the founder of this methodology has laid out the framework for creating a successful trading algorithm on his website [here](https://www.mql5.com/go?link=https://nononsenseforex.com/ "https://nononsenseforex.com/"), and on his youtube channel [here](https://www.youtube.com/channel/UCc8IRYpgBr4NGbaQFnd2b-A "https://www.youtube.com/channel/UCc8IRYpgBr4NGbaQFnd2b-A").

NNFX Strength can be used as the main entry confirmation indicator (C1) for an NNFX algorithm or multi-indicator strategy. It also functions as a volatility/volume indicator (MOMENTUM) as well as an exit indicator (when TREND changes direction). Because NNFX Strength covers all these functions it can be used alone OR in conjunction with other indicators. If you are new to NNFX it is highly recommended you watch VP's videos before proceeding to trade this way.

### 

Recommended Timeframes

We recommend the D1 and H4 charts, although it will work on any timeframe. The daily timeframe is used for strict No Nonsense Forex trading and gives you the freedom of trading for only 15 minutes per day (starting 20 minutes before the end of the trading day). For those wanting more trading opportunities, the H4 timeframe gives excellent signals that can be managed every 4 hours (at the open of the next candle). Shorter timeframes also offer the potential for very profitable scalping opportunities at the expense of more time invested.

### 

How to trade the NNFX Strength System

### 

_Prepare..._  

-   Open a new chart with the desired timeframe (ie. EURUSD H4) and load NNFX Strength onto it. The necessary data will download and populate the charts for the indicator to show correctly. Right-click then Refresh if necessary.
-   To preload all required history data for the 28 currency pairs, load [this expert advisor](https://www.mql5.com/en/code/28560) onto a new chart with a minimum value 0f 200 bars. Alternatively, you can load each chart one by one and right-click then Refresh. There are several ways to do this.
-   When all the history data is available the indicator will show correctly. If any symbols are missing, add them in Market Watch. 
-   On the right side of the indicator window is the currency analysis data calculated by NNFX Strength. This includes STRENGTH, DIFFERENCE, MOVEMENT, MOMENTUM and TREND.
-   On the bottom left side the TRADE signal is given based on this data. If a trade signal exists it will look like this... **Sell EURUSD** or **Buy GBPJPY**.
-   **Hold Buy**, **Hold Sell** or **Hold or Exit** signals do not count as entries and are used for managing trades only.

### 

_Trade..._

> IMPORTANT: Before trading first check the [$EVZ chart](https://www.mql5.com/go?link=https://www.barchart.com/stocks/quotes/$EVZ/interactive-chart "https://www.barchart.com/stocks/quotes/$EVZ/interactive-chart") which measures Forex volatility. It is recommended to only trade when the **$EVZ is at 6 or above**. Most losses occur during times when the value is below 6.
> 
> _**For H4 timeframe (and others)**_

1.  Use default indicator settings, these are optimised for H4 timeframe.
2.  Make sure your GMT offset is correct for your trade server. You will then see the market session in the top left corner of the indicator window. You can double check this with **Show_History** enabled on a H1 chart, comparing with a data source such as [Forex Factory](https://www.mql5.com/go?link=https://www.forexfactory.com/market "https://www.forexfactory.com/market"). 
3.  Check the trading signal for your current pair at the open of a new candle (ie, 4:00, 8:00, 12:00 etc).
4.  If a trade signal is given (ie, Buy EURGBP) open two market orders with recommended Lot size, TP and SL levels. Set the TP on one to 0 to allow profits to run if it trends strongly. Total risk is split between both trades, so for 2% total risk you would use 1% risk on each. You can also use a trade assistant such as this one or this one (easier to use but can slow down charts).
5.  Click and drag the next pair in the Market Watch window onto the chart to change it. Alternatively, use a symbol changer indicator such as [this one](https://www.mql5.com/go?link=https://indicatorspot.com/indicator/symbol-changer-indicator/ "https://indicatorspot.com/indicator/symbol-changer-indicator/") to do this more easily (double-click to refresh NNFX Strength quicker).
6.  If a trade signal is given open two market orders like before (ie, 0.2 lots + 0.2 lots = 0.4 lots risk total). 
7.  Repeat this for all 28 Forex pairs, being careful not to become overexposed in one particular currency (ie, EUR or GBP). If you do want to take all trades given, lower the lot size risk of all your trades to accomodate with **Lots_Risk_Percent**.
8.  Set an alarm for the next candle (ie, in 4 hours) as a reminder to return to the charts and manage your trades.

> _**For D1 timeframe**_

1.  Open indicator settings and load [this  preset](https://www.mql5.com/go?link=https://drive.google.com/file/d/189nrcSMW_8YlD7tCfaucJdy_0puKlsss/view?usp=sharing "https://drive.google.com/file/d/1KOD4R-jmwqfkVtUumzvTNPt476AJAINR/view?usp=sharing"). 
2.  Note that **Use_Previous_Close** is _false_. This will use the close of the current candle for data as you are trading at the end of the candle instead of the beginning.
3.  Make sure your GMT offset is correct for your trade server. You will then see the market session in the top left corner of the indicator window.  You can double check this with **Show_History** enabled on a H1 chart , comparing with a data source such as [Forex Factory](https://www.mql5.com/go?link=https://www.forexfactory.com/market "https://www.forexfactory.com/market"). 
4.  Check the trading signal for your current pair 20 mins before the end of the trading day (New York market close, or 23:40 server time). If the new trading day has already begun set **Use_Previous_Close** to _true_.
5.  If a trade signal is given (ie, Buy EURGBP) open **two** market orders with recommended Lot size, TP and SL levels. Set the TP on one to 0 to allow profits to run if it trends strongly. Total risk is split between both trades, so for 2% total risk you would use 1% risk on each. You can also use a trade assistant such as [this one](https://www.mql5.com/go?link=https://www.earnforex.com/metatrader-indicators/Position-Size-Calculator/ "https://www.earnforex.com/metatrader-indicators/Position-Size-Calculator/") or [this one](https://www.mql5.com/go?link=https://nononsensetrader.com/trading-assistant-5-0/ "https://nononsensetrader.com/trading-assistant-5-0/") (easier to use but can slow down charts).
6.  Click and drag the next pair in the Market Watch window onto the chart to change it. Alternatively, use a symbol changer indicator such as [this one](https://www.mql5.com/go?link=https://indicatorspot.com/indicator/symbol-changer-indicator/ "https://indicatorspot.com/indicator/symbol-changer-indicator/") to do this more easily (double-click to refresh NNFX Strength quicker).
7.  If a trade signal is given open two market orders like before (ie, 0.2 lots + 0.2 lots = 0.4 lots risk total). 
8.  Repeat this for all 28 Forex pairs, being careful not to become overexposed in one particular currency (ie, EUR or GBP). If you do want to take all trades given, lower the lot size risk of all your trades to accomodate with **Lots_Risk_Percent**.
9.  Walk away! Come back tomorrow at the same time to check and manage your trades. Watching and micro-managing your trades throughout the day will increase your chances of letting emotions ruin your success.

_So to reiterate the entry process, two trades are placed dividing the total risk between them _(ie, 1% + 1% = 2% total)_. For one, the SL is typically set to 1.5x ATR, TP is 1x ATR. For the other SL is 1.5x ATR and TP is not added._

IMPORTANT: When changing currency pairs, make sure the indicator has fully updated either by a market tick or by refreshing the chart. If using a symbol changer click the currency pair button two or three times to speed this up. The first signal that immediately appears is not correct because it hasn't updated yet.

### 

_Manage..._  

1.  First check on your existing trades by loading their respective currency pairs on the chart.
2.  If they display **Hold Buy** or **Hold Sell**, don't touch them.
3.  If they display **Hold or Exit**, you can either leave the trade to continue or close it at your discretion. The inbuilt backtester closes trades on this signal by default.
4.  If the Trade signal or Trend has changed direction, exit the trade.
5.  If a trade has reached the TakeProfit level and closed, move the StopLoss on the remaining trade to Break even (entry price) and let it run until one of the above signals occurs.
6.  If you like you can then look for more trade opportunities on the remaining pairs.
7.  Come back at the open of the next candle (or end of candle for D1) and repeat the process.
8.  If you have a 'Don't Trade' signal with existing open trades, you may choose to either hold or exit the trade but the backtesting algorithm would have closed the trade.

### 

How to trade strictly the NNFX way

To trade the No Nonsense Forex way strictly follow these additional steps...

-   Before trading first check the [$EVZ chart](https://www.mql5.com/go?link=https://www.barchart.com/stocks/quotes/$EVZ/interactive-chart "https://www.barchart.com/stocks/quotes/$EVZ/interactive-chart") which is a market indicator for total forex volume. If the number is below 7, trade with half the lotsize than usual. If the the number is below 6, it is recommended not to trade at all.
-   Check the economic news for the day [here](https://www.mql5.com/go?link=https://www.forexfactory.com/calendar "https://www.forexfactory.com/calendar") to look for upcoming high impact events. If any are due to occur, don't trade the impacted currencies on that day (preferably 24hrs before and after).
-   Trades should not exceed 2% risk, low $EVZ trades should therefore not exceed 1%.
-   Do not overexpose yourself on one currency more than 1% risk (ie, half the total exposure of EURUSD at 2% risk). Alternatively, lower your risk to trade more pairs with the same currency.
-   A trailing stop can be set at 1.5x the ATR (14) when price goes into profit by 2x ATR. For every 0.5x ATR move the Stoploss again to 1.5x ATR.
-   Follow your trading plan and don't deviate from it!

There are other specific rules set out by VP that relate to the different indicator components of an NNFX algorithm (Baseline, Confirmation, Continuation, etc), however these do not apply if you are using NNFX Strength on its own.

If you want more confirmation for your trades, adding a baseline (moving average) would be the first step. Find a good moving average (there's a ton of them, [All Averages](https://www.mql5.com/go?link=https://top-trading-indicators.com/blog/all-averages-v4-9-indicator/ "https://top-trading-indicators.com/blog/all-averages-v4-9-indicator/") is a good start), put it on the chart and adjust its period to help filter out any bad trades. Enable **Show_History** to view previous trade signals. When price is above the baseline Buy, when it is below Sell. 

### 

What do the numbers mean?  

[![NNFX Strength GBPNZD](https://c.mql5.com/6/887/Screenshot-4-GBPNZD__1.png "NNFX Strength GBPNZD")](https://c.mql5.com/6/887/Screenshot-4-GBPNZD.png "https://c.mql5.com/6/887/Screenshot-4-GBPNZD.png")

All values shown on the right side are percentages. Normalised in this way they can be interpreted with user-defined thresholds that work across many different currency pairs without changing the settings for each pair.

> ### STRENGTH
> 
> The relative strength of the two currencies in a pair compared to the others within a defined period of candles (STRENGTH_Range_Period). Previous values are also shown.
> 
> ### DIFFERENCE
> 
> The difference between the two relative strengths of the currency pair. Previous value is also shown.
> 
> ### MOVEMENT
> 
> The percentage of movement up or down for each currency in the pair.  Previous values are also shown.
> 
> ### MOMENTUM 
> 
> The difference between the current and previous DIFFERENCE percentage. This is the volatility trigger for trade signals and trend strength. Previous value is also shown.
> 
> ### TREND
> 
> Whichever direction has the most MOVEMENT determines the TREND, with the intensity (Weak, Strong) determined by MOMENTUM (threshold adjustable).
> 
> ### TRADE 
> 
> The trade signal based on TREND and MOMENTUM (threshold adjustable).
> 
> ### LOTS
> 
> Lot size is determined by **Lots_Risk_Percent** (default is 1%) and **StopLoss_ATR_Multiplier**.
> 
> ### SL
> 
> Default set to 1.5x ATR (Average True Range) distance from entry price.
> 
> ### TP
> 
> Default set to 1x ATR (Average True Range) distance from entry price.
> 
> ### BACKTEST
> 
> Trade statistics of range period includes profit in pips, total trades, win rate and profit factor.

In the top left corner the current strength values are shown under the colour of each currency for quick reference.

### 

Trading Tips

_Cut your losses and let your profits run._  

As losses are an unavoidable part of the trading process, it is better to cut them off early before they reach StopLoss. A **Hold or Exit** signal will help to determine if a trade is not going as intended and will get you out of a bad trade earlier than if you wait for a trend reversal (exit signal). At the same time the opposite is true for profitable trades, it's best to hold onto them as long as possible. Therefore you will notice that when you have a group of trades open, you will be getting rid of the losses first and allowing the profitable ones to carry on the trend as long as possible. This is a better approach than simply closing all trades when you are in cumulative profit.

_Keep an eye on Momentum._

A trend can exist when a pair of currency strength lines is either expanding OR contracting, it doesn't really matter which way they're moving but ideally they should be moving in opposite directions. The key is to keep an eye on the Momentum of movement. Increasing momentum is a good sign that the trend is strengthening and the trade will keep going in your favour. Decreasing momentum is a sign of trend exhaustion and indicates an approaching consolidation or reversal. Note that Momentum is the difference of the current and previous strength difference and is always expressed as an absolute (positive number).

_Watch the Hold signals when backtesting._

When using **Show_History** to backtest or optimise the **TRADE_Allow_Momentum_Threshold** setting, notice that the Hold Buy or Hold Sell signals prevent new trade signals forming at the end of a trend swing. Therefore with the Trade threshold try to strike a good balance between an early signal and one that keeps you in the trade for as long as possible. Often the Trade threshold is better at a lower value (like 1.0 on H4) but this depends on the timeframe, MA and Currency strength settings.

_Test different market sessions._

Each market session behaves differently so it is useful to test each one and see which works best for your strategy settings. The default setting for H4 disables trade signals for New York session because this time period impacts negatively on overall profits, whereas with different settings it might perform better than Sydney, Tokyo or London. Use Backtest mode to gauge which session is best for your custom settings to help eliminate losses. Make sure your GMT Offset is correct as this will affect the test results. When trading on D1 timeframe make sure all sessions are set to _true_.

### 

Backtesting  

NNFX Strength cannot be used in Strategy Tester because MT4 doesn't support multi-currency testing. The inbuilt Backtest display shows trade statistics for the specified indicator period, this display is enabled by **Show_Backtest**. To determine the overall profitability of your settings simply add the profits of each of the 28 currency pairs. For average WinRate and Profit Factor, add them all and divide the total by 28. The highest profit, profit factor and winrate with the least amount of trades is preferable.

Although unnecessary, if you want to backtest manually follow these steps...

> _**Simple WinRate (faster but not as accurate)**_

-   This method only uses one trade per trade signal to determine Win rate.
-   Download the **No Nonsense ATR** indicator [available here](https://www.mql5.com/go?link=https://nnfxalgotester.com/download/ "https://nnfxalgotester.com/download/") and load it on the same chart as NNFX Strength. 
-   Open NNFX Strength settings and change **Show_History** to true.
-   Using the mouse pointer, scan the history of trade signals. 
-   Where a Buy signal exists, click once on the chart to show whether the trade is a Win or a Loss.
-   Where a Sell signal exists, click twice on the chart to show whether the trade is a Win or a Loss.
-   From left to right, tally up the total Wins and Losses then calculate as a percentage (Wins / (Wins + Losses) x 100).
-   Do this for all 28 currency pairs then average the total.

> **_Full Pip Test (accurate but slower)_**

-   This method uses both trades to determine total pips made if traded continuously.
-   Using the **No Nonsense ATR** indicator as above, scan for trade signals from left to right with the mouse pointer.
-   For Buy signals click once on the chart, for Sell signals click twice.
-   From the entry candle check each following candle after the trade signal. 
-   If the trade reaches TP before there is a **Hold or Exit** signal, count the pips of the win for one trade.
-   For the remaining trade (that doesn’t have TP) follow the trade signal as the candles progress.
-   When the trade signal changes to **Hold or Exit** or the TREND changes direction, close the trade there. Drag the crosshair (middle mouse button) from the close of that candle to the close of the entry candle to determine how many pips the second trade would have made.
-   If after hitting TP the second trade then hits Breakeven before a **Hold or Exit** signal, count the trade as 0.
-   If SL is hit before a **Hold or Exit** signal or hitting TP, count both losses.
-   Add the pips of the two trades together and move onto the next trade signal.
-   Do this for all 28 currency pairs and add them together.

### 

Indicator Settings  

### GENERAL SETTINGS 

**Show_History** - When enabled the historical data and trade signals will be shown by the position of the mouse pointer.

**Use_Previous_Close** - Enable this when using timeframes other than D1. This will prevent a constantly updating signal. Do not use with Show_History enabled.

### BACKTEST SETTINGS 

**Show_Backtest** - Shows the trade statistics for the currency pair in the range determined by **Strength_Range_Period** (eg, 240 bars). Total pips profit, number of trades, win rate and profit factor are shown. The test is performed as per standard NNFX entries with two trades, one of which does not have TP and relies on the Hold or Exit signal to close. The backtest also factors in breakeven trades after the TP is hit. Enabling this option does slow down the indicator slightly due to the extra calculations.

**Simple_WinRate_Mode** - This mode only uses one trade at a time and relies only on TP or SL to close the trade, the 'Hold or Exit' signal is not used. The resulting simple win rate % will give a rough indication of the strategy's profitability and is not an accurate representation (unless it is traded this way). This method is often used as a quick way to determine the profitability of a confirmation indicator or setting in an NNFX algorithm. Note that the number of trades will be half the the usual number as only one trade is placed instead of two.

**Backtest_Start** - Sets the number of bars going backwards the test is started from (ie, 20 = starting from 20 bars ago). If value is 0 the entire range will be tested.

**Backtest Length** - The number of bars past Backtest_Start to test for, going backwards. For example, **Backtest_Start** = 20 and **Backtest_Length**  = 100 will test the range from 20 to 120 bars ago. You can use this to get sub-sample data, for instance to see if the settings were still profitable recently.

**Backtest_Spread** - Sets the spread for each trade in the backtest, therefore total profit will be _Total Profit - (Spread x Trades)._

### CURRENCY STRENGTH

**STRENGTH_Range_Period** - The candle period to determine the relative strength of currencies.

**STRENGTH_Range_Timeframe** - This can be set to a specific timeframe or the current one. 

### MOVING AVERAGES

**Use_MA** - This smoothes out the currency strength lines to make analysis easier and less choppy.

**MA_Period** - The period of the MA applied to currency strength lines.

**MA_Method** -  The method of the MA applied to currency strength lines.

### TREND & TRADE SIGNAL

**TREND_Weak_Momentum_Threshold** - If Momentum is less than this threshold, the Trend is considered Weak. This does not affect the Trade signal.

**TREND_Strong_Momentum_Threshold** - If Momentum is greater than this threshold, the Trend is considered Strong.  This does not affect the Trade signal.

**TRADE_Momentum_Threshold** - The Trade signal is shown if only if Momentum is above this threshold. The Trend signal determines trade direction.

**TRADE_Increasing_Momentum_Only** - Enable if you want trade signals with increasing momentum only. Exits when momentum is decreasing.

**TRADE_Opposite_Directions_Only** - Trade signals will show only if currency strengths are moving in opposite directions. Exits when strengths are moving the same direction.

**StopLoss_ATR_Multiplier** - The ATR multiplier for StopLoss level.

**TakeProfit_ATR_Multiplier** - The ATR multiplier for TakeProfit level.

**ATR_Period** - Sets the ATR period for TP and SL levels.

**Lots_Risk_Percent** - Sets the percentage of risk of your account balance per trade based on the StopLoss and currency pair.

**Use_Fixed_Balance** - If you are using the indicator to trade on another account, enter the account balance here.

### AMA BASELINE FILTER

[Download AMA indicator here](https://www.mql5.com/go?link=https://drive.google.com/file/d/1C1_ubIN-vQmYkfAJwesF_jY00C4oW1iA/view?usp=sharing "https://www.fxtradingrevolution.com/forex-indicators-robots/ama-mt4-indicator-kaufman-adaptive-moving-average")

**Use_AMA_Filter** - The Adaptive Moving Average indicator acts like a baseline as a trend confirmation indicator. When price is above AMA = Buy, when below = Sell.

**periodAMA** - The AMA period.

**nfast** - The period of the fast moving average.

**nslow** - The period of the slow moving average.

**G** - The overall multiplying power.

  

### DAMIANI VOLATMETER FILTER

[Download Damiani Volatmeter indicator here](https://www.mql5.com/go?link=https://drive.google.com/file/d/1CtyQIXTwmx8Pg5tj6OiqvrrRliDKxscz/view?usp=sharing "https://drive.google.com/file/d/11uietIyC16G_7mykTOiHA2PznRxWWaTb/view?usp=sharing")

**Use_Damiani_Filter** - Prevents trade signals from occurring during ranging periods. 'Don't Trade' signal is shown when trade not allowed.

**Viscosity** - Short ATR period.

**Sedimentation** - Long ATR period

**Threshold_level** - Adjust this setting first to help filter out losing trades. Higher values = less trades.

**Lag supressor** - Removes some delay.

### CHOPPINESS FILTER

[Download Choppiness Index indicator here](https://www.mql5.com/go?link=https://drive.google.com/file/d/1-XCv3GQwBjVzpYztm8sVMccjTELNJ2AW/view?usp=sharing "https://drive.google.com/file/d/1-XCv3GQwBjVzpYztm8sVMccjTELNJ2AW/view?usp=sharing")

The lower the value the less choppy price is. If enabled trades are allowed below the threshold percentage (default is 50) and not shown above the threshold. This filter improves Win rate % but can be disabled to allow more trades if desired.

**Use_Choppiness_Filter** - Prevents trade signals from occurring during choppy periods. 'Don't Trade' signal is shown when trade not allowed.

**Choppiness_Period** - Period of Choppiness index.

**Choppiness_Threshold** - Allows trade signals below this percentage threshold.

### MARKET SESSIONS FILTER

**Trade_SYDNEY** - Allows trade signals during the Sydney market session.

****Trade_TOKYO**** - Allows trade signals during the Tokyo market session.

****Trade_LONDON**** - Allows trade signals during the London market session.

****Trade_NEWYORK**** -  Allows trade signals during the New York market session.

**Trade_Overlaps_Only** -  Allows trade signals only during market session overlaps (ie, London/NewYork).

**Server_GMT_Offset** - Set this to the GMT of your broker's trade server for correct signals.

**Server_Daylight_Savings** - Enable if your brokers trade server is in daylight savings.

### LEVEL ALERTS

**Show_Levels** - Shows percentage levels as a grid in the indicator window.

**Level_Alerts** - When enabled alerts are given if a currency breaches the specified percentage level.

**Alert_Level_Rising** - Alerts when price rises above this level.

**Alert_Level_Falling** -  Alerts when price falls below this level.

### VISUAL STYLE

Here you can change the colours of all visual components.

**WARNING:** Please be aware that this indicator updates and recalculates its historical strength values out of necessity. As currency strength is relative, when the total range expands the previous values must be compressed due to normalisation. This DOES NOT affect the accuracy of the trade signal.