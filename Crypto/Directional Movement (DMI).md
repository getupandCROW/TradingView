indicator
tags:: 
	- EaseOfMovement
	- EOM
	- EMV
	- TechnicalAnalysis
- 

#### Definition

### [[Directional Movement (DMI)] Example Script:
<div class="rich-link-card-container"><a class="rich-link-card" href="https://www.tradingview.com/scripts/directionalmovement/" target="_blank">
	<div class="rich-link-image-container">
		<div class="rich-link-image" style="background-image: url('https://www.tradingview.com/static/images/logo-preview.png')">
	</div>
	</div>
	<div class="rich-link-card-text">
		<h1 class="rich-link-card-title">Directional Movement Index (DMI) — Technical Indicators — Indicators and Signals — TradingView</h1>
		<p class="rich-link-card-description">
		The Directional Movement Index (DMI) is actually a collection of three separate indicators combined into one. — Indicators and Signals
		</p>
		<p class="rich-link-href">
		https://www.tradingview.com/scripts/directionalmovement/
		</p>
	</div>
</a></div>

### **DMI** is actually a collection of three separate indicators combined into one. 

1. Directional Movement consists of the [[Average Directional Index (ADX)]]
2. Plus [[Directional Indicator (+DI)]]
3. Minus [[Directional Indicator (-DI)]]

> ADX's purposes is to define whether or not there is a trend present. It does not take direction into account at all. 

###### The other two indicators (+DI and -DI) are used to compliment the ADX. 

- They serve the purpose of determining trend direction. 
  
By combining all three, a technical analyst has a way of determining and measuring a trend's strength as well as its direction.

[![DMI Example Image](https://i.gyazo.com/a01ba0bbc04cbb815760f6353e6471b4.png)](https://gyazo.com/a01ba0bbc04cbb815760f6353e6471b4)
#### History

[[J. Welles Wilder]] created the **DMI** and featured it in his book _[[New Concepts in Technical Trading Systems]]_. 

The book was published in 1978 and also featured several of his now classic indicators such as: 

- [[Relative Strength Index (RSI)]]
- [[Average True Range (ATR)]]
- [[Parabolic SAR]]
  
Much like the indicators mentioned, the **DMI** is still widely used and has great importance in the world of technical analysis.

#### Calculation

Calculating the **DMI** can actually be broken down into two parts. 

1. calculating the **+DI** and **-DI**
2. calculating the **ADX**. 
   
To calculate the **+DI** and **-DI** you need to find the **+DM** and **-DM** (**Directional Movement**). 

- **+DM** and **-DM** are calculated using the **High**, **Low** and **Close** for each period. 
  
### You can then calculate the following:

	Current High - Previous High = UpMove
	Previous Low - Current Low = DownMove

	If UpMove > DownMove and UpMove > 0, 
		then +DM = UpMove, 
	else +DM = 0
	
	If DownMove > Upmove and Downmove > 0, 
		then -DM = DownMove, 
	else -DM = 0

#### Once you have the current **+DM** and **-DM** calculated, the **+DM** and **-DM** lines can be calculated and plotted based on the number of user defined periods.

	+DI = 100 times Exponential Moving Average (EMA)
		of (+DM / Average True Range (ATR))
		
	-DI = 100 times Exponential Moving Average (EMA)
		of (-DM / Average True Range (ATR))

##### Now that **+DX** and **-DX** have been calculated, the last step is calculating the **ADX**.

	ADX = 100 times the Exponential Moving Average (EMA)
		of the Absolute Value (abs) 
			of (+DI - -DI) / (+DI + -DI)

#### The basics

**DMI** has a value between `0` and `100` and is used to measure the *strength of the current trend*. **+DI** and **-DI** are then used to measure direction. 

When combined, the indicator can provide some valuable insight. A general interpretation would be that:

- During a strong trend (**ADX** above `25`) *but dependent on the analyst's interpretation*: 
	- when the **+DI** is above the **-DI**, 
		- then a Bullish Market is defined. 
	- When **-DI** is above **+DI**, 
		- then a Bearish Market is at hand.  


###### **Strength** or a *potential signal*, is up to the trader's interpretation. 

Acceptable values may change depending on the financial instrument being examined, therefore some historical analysis of the instrument in question would be prudent. A technical analyst can make better decisions based on what has occurred in historical examples.

## What to look for

### Trend Strength

> Analyzing trend strength is the most basic use for the DMI. 

To analyze trend strength, the focus should be on the **ADX** line and not the **+DI** or **-DI** lines. 

- Wilder believed that a **DMI** reading above `25` indicated a strong trend, 
- while a reading below `20` indicated a weak or non-existent trend. 
- A reading between those two values, would be considered indeterminable. 
  
However, as previously mentioned, an experienced trader would not take the `25` and `20` values and apply them in every situation. 

What is truly a strong trend or a weak trend depends on the financial instrument being examined. Historical analysis can assist in determining appropriate values.


Also, keep in mind that Wilder developed the **DMI** for use with 

- currencies 
- and commodities 
  
  which are typically more **volatile** than stocks and have stronger trends. 

#### This will factor into determining which values are appropriate for: 

- analyzing the strength of a trend, 
- analysing any signals generated.

### Crosses

DI Crossovers are the significant trading signal generated by the **DMI**. There is a particular set of conditions for each cross.

#### Bullish DI Cross

1.  **ADX** must be over 25 (strong trend. The value is determined by trader)
2.  The **+DI** crosses above the **-DI**.
3.  Stop Loss should be set at the current day's low. The signal should not be abandoned, if the low is not breached, even if the **-DI** crosses above the **+DI**
4.  The signal strengthens if **ADX** rises.
5.  If **ADX** strengthens, trader's should employ a trailing stop.

#### Bearish DI Cross

1.  **ADX** must be over 25 (strong trend. The value is determined by trader)
2.  The **-DI** crosses above the **+DI**.
3.  Stop Loss should be set at the current day's high. The signal should not be abandoned, if the high is not breached, even if the **+DI** crosses above the **-DI**
4.  The signal strengthens if **ADX** rises.
5.  If **ADX** strengthens, trader's should employ a trailing stop.

## Summary

Directional Movement (**DMI**) is another quite valuable technical analysis indicator provided by Wilder. It takes the very complex subject of trend strength and direction and calculates it down into a very simple and straightforward visual. The key takeaway of using the **DMI** is that even though it can provide quality information and even trading signals, it is not an easy indicator to master. To truly get the most out of **DMI**, a technical analyst will have to continually study and tweak their use of the indicator. Combining the knowledge of how **DMI** works and its capabilities, along with a decent amount of historical analysis and experience, will help the trader to make the **DMI** a good, possible addition to their overall trading strategy.

## Inputs

![](https://s3.amazonaws.com/cdn.freshdesk.com/data/helpdesk/attachments/production/43080395589/original/v7cJLNxiquQrlzZ5tASS-Iv2GO7rGPbf2w.png?1572022653)

### ADX

The time period to be used in calculating the **ADX** which has a smoothing component (14 is the Default).

### DI Length

The time period to be used in calculating the DI (14 is Default).

## Style

![](https://s3.amazonaws.com/cdn.freshdesk.com/data/helpdesk/attachments/production/43080395621/original/XtzPAHLbSmj5n7ukXXkHZ2GdsJ9ZWP4Bnw.png?1572022668)

### ADX

Can toggle the visibility of the **ADX** Line as well as the visibility of a price line showing the actual current value of the **ADX**. Can also select the **ADX** Line's color, line thickness and visual style (Line is the Default).

### +DI

Can toggle the visibility of the **+DI** Line as well as the visibility of a price line showing the actual current value of the **+DI**. Can also select the **+DI** Line's color, line thickness and visual style (Line is the Default).

### -DI

Can toggle the visibility of the **-DI** Line as well as the visibility of a price line showing the actual current value of the **-DI**. Can also select the **-DI** Line's color, line thickness and visual style (Line is the Default).

### Precision

Sets the number of decimal places to be left on the indicator's value before rounding up. The higher this number, the more decimal points will be on the indicator's value.