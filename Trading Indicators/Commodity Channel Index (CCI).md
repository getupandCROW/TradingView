#### Definition

The [Commodity Channel Index (CCI)](https://www.tradingview.com/scripts/commoditychannelindex/) is a **momentum oscillator** used in technical analysis primarily to identify overbought and oversold levels by measuring an instrument's variations away from its statistical mean. CCI is a very well-known and widely-used indicator that has gained level of popularity in no small part of its versatility. Besides overbought/oversold levels, CCI is often used to find reversals as well as divergences. Originally, the indicator was designed to be used for identifying trends in commodities, however it is now used in a wide range of financial instruments.

#### History

The Commodity Channel Index (CCI) was created by Donald Lambert and introduced in 1980. It first appeared in what was then known as _Commodities_ Magazine.

#### Calculation

There are several steps involved in calculating the Commodity Channel Index. The following example is for a typical 20 Period CCI:

CCI = (Typical Price  -  20 Period SMA of TP) / (.015 x Mean Deviation)
Typical Price (TP) = (High + Low + Close)/3
Constant = .015

The Constant is set at .015 for scaling purposes. By including the constant, the majority of CCI values will fall within the 100 to -100 range. There are three steps to calculating the Mean Deviation.

1.  Subtract the most recent 20 Period Simple Moving from each typical price (TP) for the Period.
2.  Sum these numbers strictly using absolute values.
3.  Divide the value generated in step 3 by the total number of Periods (20 in this case).

#### The basics

The Commodity Channel Index indicator takes a security's change in price and compares that to its average change in price. CCI's calculation produces positive and negative values that oscillate above and below a Zero Line. Typically a value of 100 is identified as overbought and a reading of -100 is identified as being oversold. However, it is important to note a couple of things.

1.  Actual overbought and oversold thresholds can vary depending on the financial instrument being traded. For example, a more volatile instrument may have thresholds at 200 and -200.
2.  Frequently, overbought/oversold conditions are seen as a precursor to a price reversal. However, when using CCI, overbought and oversold conditions can often be a sign of strength, meaning the current trend may be strengthening and continuing.

#### What to look for

##### Overbought/Oversold

Because The Commodity Channel Index's primary function is to identify when a security is either overbought or oversold, it makes sense that anticipating future movements of price when these levels are crossed, is crucial to getting the most out of the CCI.

-   Overbought and Oversold conditions can be used in their more traditional sense to identify future reversals. Remember true overbought/oversold thresholds values can and often do vary between instruments.

When price crosses above the overbought threshold, a fall in price may occur soon afterwards.

Price crossing below oversold conditions may signify a reversal to a rise in price.

-   Overbought and Oversold conditions can also be seen as a sign of strength when using the CCI. The current trend may be strengthening.

During a Bullish Trend, price crossing above the overbought threshold may indicate strong confidence in the move and price will continue to rise.

During a Bearish Trend, price crossing below the oversold threshold may indicate strong confidence in the move and price will continue to fall.

##### Divergence

Momentum often does precede changes in price. Therefore, as with most momentum based oscillators, divergence between price and the indicator's reading should not be ignored. The Commodity Channel Index is no different. Divergences between CCI and price action can be a signal that changes in trend may be forthcoming.

Bullish CCI Divergence occurs when price makes a lower low while CCI makes a higher low.

Bearish CCI Divergence occurs when price makes a higher high while CCI makes a lower high.

#### Summary

The fact that The Commodity Channel Index indicator has been in use now for over 30 years is a testament to the value placed on it within the technical analysis community. Time and time again it is demonstrated how important momentum is when analyzing the market and attempting to determine future moves. Whether you are using CCI to confirm trends or to look for reversals, its momentum quantifying prowess should not go unnoticed. Like most indicators, CCI is best used not as a stand-alone indicator but in conjunction with others.

#### Inputs

![](https://s3.amazonaws.com/cdn.freshdesk.com/data/helpdesk/attachments/production/43080400684/original/DuJiWhml0DrP4wWlcy8DUnPXtK4DOzzW-g.png?1572024190)

  

##### Length

The time period to be used in calculating the SMA portion of the CCI (20 is the Default).

##### Source

Determines what data from each bar will be used in calculations. Close is the default.

#### Style

![](https://s3.amazonaws.com/cdn.freshdesk.com/data/helpdesk/attachments/production/43080400720/original/zsSMNroNAsnjAstRSvF4hSNQ0Le57yYFvQ.png?1572024200)

##### CCI

Can toggle the visibility of the CCI as well as the visibility of a price line showing the actual current price of the CCI. Can also select the CCI Line's color, line thickness and visual style (Line is the Default).

##### Upper Band

Can toggle the visibility of the Upper Band as well as select its value, color, line thickness and line style.

##### Lower Band

Can toggle the visibility of the Lower Band as well as select its value, color, line thickness and line style.

##### Background

Toggles the visibility of a Background color within the Bands. Can also change the Color itself as well as the opacity.

##### Precision

Sets the number of decimal places to be left on the indicator's value before rounding up. The higher this number, the more decimal points will be on the indicator's value.