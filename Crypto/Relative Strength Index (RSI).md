#### Definition

The [Relative Strength Index (RSI)](https://www.tradingview.com/scripts/relativestrengthindex/) is a well versed momentum based oscillator which is used to measure the speed (velocity) as well as the change (magnitude) of directional price movements. Essentially RSI, when graphed, provides a visual mean to **monitor both the current, as well as historical, strength and weakness of a particular market**. 

The strength or weakness is based on closing prices over the duration of a specified trading period creating a reliable metric of price and momentum changes. Given the popularity of cash settled instruments (stock indexes) and leveraged financial products (the entire field of derivatives); RSI has proven to be a viable indicator of price movements.

#### History

[[J.Welles Wilder Jr.]] is the creator of the Relative Strength Index. A former Navy mechanic, Wilder would later go on to a career as a mechanical engineer. After a few years of trading commodities, Wilder focused his efforts on the study of technical analysis. In 1978 he published _[[New Concepts in Technical Trading Systems]]_. This work featured the debut of his new **momentum oscillator**, the Relative Strength Index, better known as RSI.

Over the years, RSI has remained quite popular and is now seen as one of the core, essential tools used by technical analysts the world over. Some practitioners of RSI have gone on to further build upon the work of Wilder. One rather notable example is James Cardwell who used RSI for trend confirmation.

#### Calculation

`RSI = 100 – 100/ (1 + RS)`

RS = Average Gain of n days UP  / Average Loss of n days DOWN

###### For a practical example, the built-in Pine Script function rsi(), could be replicated in long form as follows.

```pine
change = change(close)
gain = change >= 0 ? change : 0.0
loss = change < 0 ? (-1) * change : 0.0
avgGain = rma(gain, 14)
avgLoss = rma(loss, 14)
rs = avgGain / avgLoss
rsi = 100 - (100 / (1 + rs))
```

"rsi", above, is exactly equal to `rsi(close, 14)`.


#### The basics

As previously mentioned, RSI is a **momentum based oscillator**. What this means is that as an oscillator, this indicator operates within a band or a set range of numbers or parameters. Specifically, 

> RSI operates between a scale of 0 and 100. The closer RSI is to 0, the weaker the momentum is for price movements. The opposite is also true. An RSI closer to 100 indicates a period of stronger momentum.


### Period

14 days is likely the most popular period, however traders have been known to use a wide variety of numbers of days.

#### What to look for

##### Overbought/Oversold

Wilder believed that when prices rose very rapidly and therefore momentum was high enough, that the underlying financial instrument/commodity would have to eventually be considered overbought and a selling opportunity was possibly at hand. 

Likewise, when prices dropped rapidly and therefore momentum was low enough, the financial instrument would at some point be considered oversold presenting a possible buying opportunity.

There are set number ranges within RSI that Wilder consider useful and noteworthy in this regard. According to Wilder, 

###### ***any number above 70 should be considered overbought and any number below 30 should be considered oversold***.

###### ***An RSI between 30 and 70 was to be considered neutral and an RSI around 50 signified “no trend”***.

Some traders believe that Wilder’s overbought/oversold ranges are too wide and choose to alter those ranges. For example, someone might consider any number above 80 as overbought and anything below 20 as oversold. This is entirely at the trader’s discretion.

#### Divergence

RSI Divergence occurs when there is a difference between what the price action is indicating and what RSI is indicating. These differences can be interpreted as an impending reversal. Specifically there are two types of divergences, bearish and bullish.

_**Bullish RSI Divergence**_ – When price makes a new low but RSI makes a **higher low**.

_**Bearish RSI Divergence**_ – When price makes a new high but RSI makes a **lower high**.

##### Wilder believed that 

- Bearish Divergence creates a selling opportunity while 
- Bullish Divergence creates a buying opportunity.

#### Failure Swings

Failure swings are another occurrence which Wilder believed increased the likelihood of a price reversal. One thing to keep in mind about failure swings is that they are completely independent of price and rely solely on RSI. Failure swings consist of four “steps” and are considered to be either Bullish (buying opportunity) or Bearish (selling opportunity).

##### Bullish Failure Swing

A.  RSI drops below 30 (considered oversold).
B.  RSI bounces back above 30.
C.  RSI pulls back but remains above 30 (remains above oversold)
D.  RSI breaks out above its previous high.

##### Bearish Failure Swing

A.  RSI rises above 70 (considered overbought)
B.  RSI drops back below 70
C.  RSI rises slightly but remains below 70 (remains below overbought)
D.  RSI drops lower than its previous low.

[Failure Swing Noted](https://www.tradingview.com/wiki/File:Failureswingnoted.jpg)

[![](https://s3.amazonaws.com/cdn.freshdesk.com/data/helpdesk/attachments/production/43082660571/original/WKS_3gphxBKhB9W-S4ETRfWhfdG43ntOsw.png?1572957289)](https://www.tradingview.com/wiki/File:Failureswingnoted.jpg)

#### Cardwell’s trend confirmations

Of course no one indicator is a magic bullet and almost nothing can be taken simply at face value. Andrew Cardwell, who was mentioned earlier, was one of those students who took Wilder’s RSI interpretations and built upon them. Cardwell’s work with RSI led to RSI being a great tool not just for anticipating reversals but also for confirming trends.

##### Uptrends/Downtrends

Cardwell made keen observations while studying Wilder’s ideas of divergence. Cardwell believed that:

-   Bullish Divergence only occurs in a Bearish Trend.
-   Bearish Divergence only occurs in an Bullish Trend.
-   Both Bullish and Bearish Divergence usually cause a brief price correction and not an actual trend reversal.

What this means is that essentially Divergence should be used as a way to confirm trends and not necessarily anticipate reversals.

##### Reversals

Cardwell also discovered what are referred to as Positive and Negative Reversals. Positive and Negative Reversals are basically the opposite of Divergence.

-   **Positive Reversal occurs when price makes a higher low while RSI makes a lower low**. Price proceeds to rise. Positive Reversals only occur in Bullish Trends.
-   **Negative Reversal occurs when price makes a lower high while RSI makes a higher high**. Price proceeds to fall. Negative Reversals only occur in Bearish Trends.

Positive and Negative Reversals can be boiled down to cases where ***price outperformed momentum***. And because Positive and Negative Reversals only occur in their specified trends, they can be used as yet another tool for trend confirmation.

#### Summary

For more than four decades the Relative Strength Index (RSI) has been an extremely valuable tool for almost any serious technical analyst. Wilder’s work with momentum laid the groundwork for future chartists and analysts to dive in deeper to further explore the implications of his RSI modeling and its correlation with underlying price movements. 

As such, RSI is simply one of the best tools or indicators in a trader’s arsenal of market metrics to develop most any trading methodology. Only the novice will take one look at RSI and assume which direction the market will be heading next based off of one number. 

> Wilder believed that a bullish divergence was a sign that the market would soon be on the rise, while Cardwell believed that such a divergence was merely a slight price correction on the continued road of a downward trend. 

As with any indicator, a trader should take the time to research and experiment with the indicator before relying on it as a sole source of information for any trading decision. When used in proper its perspective, RSI has proven to be a core indicator and reliable **metric of price, velocity and depth of market**.

#### Inputs


![](https://s3.amazonaws.com/cdn.freshdesk.com/data/helpdesk/attachments/production/43284019870/original/43zBUO9WcFNAEWfeb1suzEVsErhGwK8FbA.png?1640790102)

##### RSI Length

The time period to be used in calculating the RSI. 14 days is the default.

##### Source

Determines what data from each bar will be used in calculations. Close is the default.

##### MA Type

Determines the type of Moving Average that is applied to the RSI calculation. Selecting Bollinger Bands adds two additional plots that envelop the MA.

##### MA Length

Determines the time period to be used in calculating the MA specified in MA Type.

##### BB StdDev

Only applicable when MA Type is Bollinger Bands. This setting specifies the number of Standard Deviations away from the SMA that the Upper and Lower Bands should be. 2 is the default.

#### Style

![](https://s3.amazonaws.com/cdn.freshdesk.com/data/helpdesk/attachments/production/43284021362/original/2vmz7ALgSu3xaTi-Kg9rxBtR0ZucsZEGKA.png?1640790382)

##### RSI

Can toggle the visibility of the RSI as well as the visibility of a price line showing the actual current price of the RSI. Can also select the RSI's color, line thickness and line style.

##### RSI-based MA

Can toggle the visibility of the RSI-based MA as well as the visibility of a price line showing the actual current MA value. Can also select its color, line thickness and line style.

##### Upper Bollinger Band

Only applicable when Bollinger Bands are selected as the MA Type in the Inputs section, otherwise the bands will not appear even if this is selected. Can toggle the visibility of the Upper Bollinger Band well as the visibility of a price line showing its value. Can also select its color, line thickness and line style.

##### Lower Bollinger Band

Only applicable when Bollinger Bands are selected as the MA Type in the Inputs section, otherwise the bands will not appear even if this is selected. Can toggle the visibility of the Lower Bollinger Band well as the visibility of a price line showing its value. Can also select its color, line thickness and line style.

##### RSI Upper Band

Can toggle the visibility of the Upper Band as well as sets the boundary, on the scale of 1-100, for the Upper Band (70 is the default). The color, line thickness and line style can also be determined.

##### RSI Middle Band

Can toggle the visibility of the Middle Band as well as sets the boundary, on the scale of 1-100, for the Middle Band (50 is the default). The color, line thickness and line style can also be determined.

##### RSI Lower Band

Can toggle the visibility of the Lower Band as well as sets the boundary, on the scale of 1-100, for the Lower Band (30 is the default). The color, line thickness and line style can also be determined.

##### RSI Background Fill

Toggles the visibility of a Background color within the RSI's boundaries. Can also change the Color itself as well as the opacity.

##### Bollinger Bands Background Fill

Only applicable when Bollinger Bands are selected as the MA Type in the Inputs section, otherwise the background fill will not appear even if this is selected. Toggles the visibility of a Background color within the Bollinger Bands' boundaries. Can also change the Color itself as well as the opacity.

##### Precision

Sets the number of decimal places to be left on the indicator's value before rounding up. The higher this number, the more decimal points will be on the indicator's value.