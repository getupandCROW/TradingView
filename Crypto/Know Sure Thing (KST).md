# Know Sure Thing 
acronym:: KST

#### Definition

The [Know Sure Thing indicator (KST)](https://www.tradingview.com/scripts/knowsurething/) is a **momentum based oscillator**. KST is based on [[Rate of Change (ROC)]]. Know Sure Thing takes four different timeframes of ROC and smooth's them out using Simple Moving Averages. KST then calculates a final value that fluctuates between positive and negative values above and below a Zero Line. There is also a signal line which is an SMA of the KST line itself. 

> Essentially, the Know Sure Thing Indicator measures the momentum of four separate price cycles. 

##### Technical Analysts use this information to spot 

- divergences
- overbought and oversold conditions 
- crossovers.

#### History

The Know Sure Thing indicator (KST) was developed by [[Martin Pring]] and introduced in 1992 in [[Stocks & Commodities Magazine]]. He originally referred to the indicator as the _**Summed Rate of Change**_.

#### Calculation

*This calculation is using the default parameters in Tradingview of* `10,15,20,30,10,10,10,15,9`.

1.  The first four numbers `(10,15,20,30)` represent the **ROC** lengths to be used.
2.  The second four numbers `(10,10,10,15)` are the **SMA** lengths to be applied to their corresponding Know Sure Thing (**KST**) lengths. 
3.  The final number `(9)` is the Know Sure Thing (**KST**) length to be used in calculating the signal line.

##### Therefore in this example, you will first need to calculate the ROCMA for each price cycle.

- **ROCMA1** = 10 Period SMA -of- 10 Period ROC

- **ROCMA2** = 10 Period SMA -of- 15 Period ROC

- **ROCMA3** = 10 PERIOD SMA -of- 20 Period ROC

- **ROCMA4** = 15 Period SMA -of- 30 Period ROC

##### Now that you have all for ROCMA calculated, the KST can be calculated.

`(RCMA1 x 1) + (ROCMA2 x 2) + (ROCMA3 x 3) + (ROCMA4 x 4) = KST`

- The signal line is then a 9 Period SMA -of- the KST

#### The basics

KST takes the Rate of Change for four different time periods, smooth's them out with moving averages, weights them and then sums the results. The intention is to get a better understanding of the momentum for a particular security of financial instrument. The general rule is that when KST is positive, then momentum is up and when KST is negative, then momentum is down. This would translate to Bullish and Bearish markets respectively.

One thing to note, is that the time frames used in the indicator's parameters is at the trader's discretion. Pring recommended that when switching between daily, weekly and monthly charts; the parameters of the indicator should be switched accordingly. For example:

- **Daily**:  `(10, 15, 20, 30, 10, 10, 10, 15, 9)`  
- **Weekly**:  `(10, 13, 15, 20, 10, 13, 15, 20, 9)`
- **Monthly**:  `(9, 12, 18, 24, 6, 6, 6, 9, 9)`

#### What to look for

##### Divergence

Divergence occurs when price action or movements is not confirmed by the indicator's readings. This can be a sign that the current, underlying momentum does not support price and a ***reversal is potentially at hand***.  

- Bullish KST Divergence is when price is falling but KST is rising.
- Bearish KST Divergence is when price is rising but KST is falling.

 

##### Overbought/Oversold

Overbought and Oversold conditions are somewhat more difficult to define in regards to the KST. The reason is that unlike other momentum oscillators (such as the [[Relative Strength Index (RSI)|RSI]]), KST is not bound to a specific range. Therefore, defining true overbought and oversold levels will take some research and experimentation. Historical analysis can assist in the process. 

Most of the time, KST overbought and oversold conditions are **good for trend confirmation and not necessarily reversals**. Overbought can be seen as a sign of strength during a bullishmarket, while oversold may be a sign of strength in a bearish market.

##### Crossovers

There are two different type of crossovers when analyzing the KST. There are **Zero Line crossovers** as well as **signal line crossovers**. Zero Line crossovers typically have a lot of lag and are not always reliable. Signal line crossovers on the other hand, can signify an underlying change in momentum.

- When the KST line is negative yet crosses above the signal line, upside momentum is increasing.
- When the KST line is positive and crosses below the signal line, downside momentum is increasing.

#### Summary

The Know Sure Thing indictor ([[Know Sure Thing (KST)|KST]]) is like many other technical analysis indicators in that it has both strengths and weaknesses and should not be used as a stand-alone signal generating system. 

Because the indicator employs a series of moving averages, there is lag inherently built in. This can cause simple signals like Zero Line crossovers to be unreliable. 

However, the indicator still can be considered useful when using overbought and oversold conditions, not as a way to anticipate reversals, but as a way to confirm trend direction. Signal line crossovers have also been shown to be effective in anticipating price movements.

#### Inputs

![](https://s3.amazonaws.com/cdn.freshdesk.com/data/helpdesk/attachments/production/43080381172/original/o98mX3-zj_wQqA2miNDpY5ZW2GlIXwKk1A.png?1572018671)

##### ROCLen1

The time period to be used in calculating the first ROC.

##### ROCLen2

The time period to be used in calculating the second ROC.

##### ROCLen3

The time period to be used in calculating the third ROC.

##### ROCLen4

The time period to be used in calculating the fourth ROC.

##### SMALen1

The time period to be used for the SMA of the first ROC.

##### SMALen2

The time period to be used for the SMA of the second ROC.

##### SMALen3

The time period to be used for the SMA of the third ROC.

##### SMALen4

The time period to be used for the SMA of the fourth ROC.

##### SigLen

The time period to be used in calculating the signal line.

#### Style

![](https://s3.amazonaws.com/cdn.freshdesk.com/data/helpdesk/attachments/production/43080381277/original/79Cjo6tVwKvmV8KKGtbFDrlz92O4yMM5Wg.png?1572018697)

##### KST

Can toggle the visibility of the KST Line as well as the visibility of a price line showing the actual current value of the KST Line. Can also select the KST Line's color, line thickness and visual type (Line is the default).

##### Sig

Can toggle the visibility of the Signal Line as well as the visibility of a price line showing the actual current value of the Signal Line. Can also select the Signal Line's color, line thickness and visual type (Line is the default).

##### Zero Line

Can toggle the visibility of the Zero Line. Can also select the Signal Line's value, color, line thickness and line type (dashes is the default).

##### Precision

Sets the number of decimal places to be left on the indicator's value before rounding up. The higher this number, the more decimal points will be on the indicator's value.