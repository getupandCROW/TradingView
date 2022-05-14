# 888 BOT #alerts (open source)

This is an Expert Advisor **EA** or Automated trading script for **longs** and **shorts**, which uses only a Take Profit or, in the worst case, a Stop Loss to close the trade.
It is a much improved version of the previous **Repanocha**. It does not use **Trailing Stop** or **security()** functions (although using a security function does not mean that the script repaints) and all signals are confirmed, therefore the script doesn`t repaint in alert mode and is accurate in backtest mode. Apart from the previous indicators, some more functions have been added for Stop-Loss, re-entry and leverage.

### It uses 8 indicators:

1. Jurik Moving Average
    - It is a moving average created by Mark Jurik for professionals which eliminates the *lag* or delay of the signal. It**s better than other moving averages like EMA , DEMA , AMA or T3.
    - There are two ways to decrease noise using JMA . Increasing the **LENGTH** parameter will cause JMA to move more slowly and therefore reduce noise at the expense of adding *lag*
    - The **JMA LENGTH**, **PHASE** and **POWER** parameters offer a way to select the optimal balance between *lag* and over boost.
    - Green: Bullish
    - Red: Bearish

2. Range filter
    - Created by Donovan Wall, its function is to filter or eliminate noise and to better determine the price trend in the short term.
    - First, a uniform average price range **SAMPLING PERIOD** is calculated for the filter base and multiplied by a specific quantity **RANGE MULTIPLIER**.
    - The filter is then calculated by adjusting price movements that do not exceed the specified range.
    - Finally, the target ranges are plotted to show the prices that will trigger the filter movement.
    - Green: Bullish
    - Red: Bearish

3. Average Directional Index (ADX Classic) and (ADX Masanakamura)
    - It is an indicator designed by Welles Wilder to measure the strength and direction of the market trend. The price movement is strong when the ADX has a positive slope and is above a certain minimum level
    - **ADX THRESHOLD** and for a given period **ADX LENGTH**.
    - The green color of the bars indicates that the trend is bullish and that the ADX is above the level established by the threshold.
    - The red color of the bars indicates that the trend is down and that the ADX is above the threshold level.
    - The orange color of the bars indicates that the price is not strong and will surely lateralize.
    - You can choose between the classic option and the one created by a certain **Masanakamura**.
    - The main difference between the two is that in the first it uses RMA() and in the second SMA() in its calculation.

4. Parabolic SAR
   - This indicator, also created by Welles Wilder, places points that help define a trend. The Parabolic SAR can follow the price above or below, the peculiarity that it offers is that when the price touches the indicator, it jumps to the other side of the price (if the Parabolic SAR was below the price it jumps up and vice versa) to a distance predetermined by the indicator. At this time the indicator continues to follow the price, reducing the distance with each candle until it is finally touched again by the price and the process starts again.
   - This procedure explains the name of the indicator:
     - Parabolic SAR follows the price generating a characteristic parabolic shape, when the price touches it, stops and turns ( SAR is the acronym for **stop and reverse**), giving rise to a new cycle. When the points are below the price, the trend is up, while the points above the price indicate a downward trend.

5. RSI with Volume
    - This indicator was created by LazyBear from the popular RSI .
    - The RSI is an oscillator-type indicator used in technical analysis and also created by Welles Wilder that shows the strength of the price by comparing individual movements up or down in successive closing prices.
    - LazyBear added a volume parameter that makes it more accurate to the market movement.
    - A good way to use RSI is by considering the 50 **RSI CENTER LINE** centerline. When the oscillator is above, the trend is bullish and when it is below, the trend is bearish

6. Moving Average Convergence Divergence (MACD) and (MAC-Z)
    - It was created by Gerald Appel. Subsequently, the histogram was added to anticipate the crossing of MA. Broadly speaking, we can say that the MACD is an oscillator consisting of two moving averages that rotate around the zero line. The MACD line is the difference between a short moving average **MACD FAST MA LENGTH** and a long moving average **MACD SLOW MA LENGTH**.
    - It is an indicator that allows us to have a reference on the trend of the asset on which it is operating, thus generating market entry and exit signals.
    - We can talk about a bull market when the MACD histogram is above the zero line, along with the signal line, while we are talking about a bear market when the MACD histogram is below the zero line.
    - There is the option of using the MAC-Z indicator created by LazyBear, which according to its author is more effective, by using the parameter VWAP (volume weighted average price)
    - **Z-VWAP LENGTH** together with a standard deviation **STDEV LENGTH** in its calculation.

7. Volume Condition
    - Volume indicates the number of participants in this war between bulls and bears, the more volume the more likely the price will move in favor of the trend.
    - A low trading volume indicates a lower number of participants and interest in the instrument in question. Low volumes may reveal weakness behind a price movement.
    - With this condition, those signals whose volume is less than the volume SMA for a period- **SMA VOLUME LENGTH** multiplied by a factor **VOLUME FACTOR** are filtered.
    - In addition, it determines the leverage used, the more volume , the more participants, the more probability that the price will move in our favor, that is, we can use more leverage.
    - The leverage in this script is determined by how many times the volume is above the SMA line.
    - The maximum leverage is 8 (eight).

8. Bollinger Bands
    - This indicator was created by John Bollinger and consists of three bands that are drawn superimposed on the price evolution graph.
    - The central band is a moving average, normally a simple moving average calculated with 20 periods is used. (**BB LENGTH** Number of periods of the moving average)
    - The upper band is calculated by adding the value of the simple moving average X times the standard deviation of the moving average.
    - (**BB MULTIPLIER** Number of times the standard deviation of the moving average)
    - The lower band is calculated by subtracting the simple moving average X times the standard deviation of the moving average.
    - The band between the upper and lower bands contains, statistically, almost 90% of the possible price variations, which means that any movement of the price outside the bands has special relevance.
    - In practical terms, Bollinger bands behave as if they were an elastic band so that, if the price touches them, it has a high probability of bouncing.
    - Sometimes, after the entry order is filled, the price is returned to the opposite side. If price touch the Bollinger band in the same previous conditions, another order is filled in the same direction of the position to improve the average entry price, (% MINIMUM BETTER PRICE **: Minimum price for the re-entry to be executed and that is better than the price of the previous position in a given %) in this way we give the trade a chance that the Take Profit is executed before.
    - The downside is that the position is doubled in size. **ACTIVATE DIVIDE TP**: Divide the size of the TP in half. More probability of the trade closing but less profit.

## STOP LOSS and RISK MANAGEMENT

A good risk management is what can make your equity go up or be liquidated.
The % risk is the percentage of our capital that we are willing to lose by operation. This is recommended to be between 1-5%.

### % Risk: (% Stop Loss x % Equity per trade x Leverage) / 100

First the strategy is calculated with Stop Loss, then the risk per operation is determined and from there, the amount per operation is calculated and not vice versa.
In this script you can use a normal Stop Loss or one according to the ATR.
Also activate the option to trigger it earlier if the risk percentage is reached.

- **% RISK ALLOWED** which is calculated with: **% EQUITY ON EACH ENTRY**. Only works with Stop Loss on **NORMAL** or **BOTH** mode.
- **STOP LOSS CONFIRMED**: The Stop Loss is only activated if the closing of the previous bar is in the loss limit condition. It is useful to prevent the SL from triggering when they do a *pump* to sweep Stops and then return the price to the previous state.

## ALERTS

There is an alert for each leverage, therefore a maximum of 8 alerts can be set for *long* and 8 for *short*, plus an alert to close the trade with Take Profit or Stop Loss in market mode. You can also place Take Profit limit and Stop Loss limit orders a few seconds after filling the position entry order.

- **MAXIMUM LEVERAGE**: It is the maximum allowed multiplier of the % quantity entered on each entry for 1X according to the volume condition.

- **ADVANCE ALERTS**: There is always a time delay from when the alert is triggered until it reaches the exchange and can be between 1-15 seconds. With this parameter, you can advance the alert by the necessary seconds to activate it earlier. In this way it can be synchronized with the exchange so that the execution time of the entry order to the position coincides with the opening of the bar.

*The settings are for Bitcoin at Binance Futures (BTC: USDTPERP ) in 15 minutes.
For other pairs and other timeframes, the settings have to be adjusted again. And within a month, the settings will be different because we all know the market and the trend are changing.*

## BACKTEST

The objective of the Backtest is to evaluate the effectiveness of our strategy. A good Backtest is determined by some parameters such as:

- **RECOVERY FACTOR**: It consists of dividing the **net profit** by the **drawdown**. An excellent trading system has a recovery factor of 10 or more (it generates 10 times more net profit than drawdown).
- **PROFIT FACTOR**: The **Profit Factor** is another popular measure of system performance. It is as simple as dividing what win trades earn by what loser trades lose. If the strategy is profitable then by definition the **Profit Factor** is going to be greater than 1. Strategies that are not profitable produce profit factors less than one. A good system has a profit factor of 2 or more. The good thing about the **Profit Factor** is that it tells us what we are going to earn for each dollar we lose. A profit factor of 2.5 tells us that for every dollar we lose operating we will earn 2.5.
- **SHARPE**: (Return system - Return without risk) / Deviation of returns.
- When the variations of gains and losses are very high, the deviation is very high and that leads to a very poor **Sharpe** ratio. If the operations are very close to the average (little deviation) the result is a fairly high **Sharpe** ratio. If a strategy has a **Sharpe** ratio greater than 1 it is a good strategy. If it has a **Sharpe** ratio greater than 2, it is excellent. If it has a **Sharpe** ratio less than 1 then we don**t know if it is good or bad, we have to look at other parameters.
- **MATHEMATICAL EXPECTATION**: (% winning trades X average profit) + (% losing trades X average loss). To earn money with a Trading system, it is not necessary to win all the operations, what is really important is the final result of the operation. A Trading system has to have positive mathematical expectation as is the case with this script: ME = (0.87 x 30.74$) - (0.13 x 56.16$) = (26.74 - 7.30) = $19.44 > 0

## PARAMETERS

- **BACKTEST DAYS**: Number of days back of historical data for the calculation of the Backtest.
- **ENTRY TYPE**: For **% EQUITY** if you have ($)10,000 of capital and select (7.5%), your entry would be ($)750 without leverage. If you select CONTRACTS for the **BTCUSDT** pair, for example, it would be the amount in **Bitcoins** and if you select **CASH** it would be the amount in ($) dollars.
- **QUANTITY (LEVERAGE 1X)**: The amount for an entry with X1 leverage according to the previous section.
- **MAXIMUM LEVERAGE**: It is the maximum allowed multiplier of the quantity entered in the previous section according to the volume condition.

*The settings are for Bitcoin at Binance Futures (BTC: USDTPERP) in 15 minutes.
For other pairs and other timeframes, the settings have to be adjusted again. And within a month, the settings will be different because we all know the market and the trend are changing*
