---
---

# Moving Average Convergence Divergence – MACD  

The most popular indicator used in technical analysis, the moving average convergence divergence ( MACD ), created by Gerald Appel. 

> MACD is a *trend-following momentum indicator*, designed to reveal changes in the strength, direction, momentum, and duration of a trend in a financial instrument’s price  
  
## Historical evolution of MACD 
- [[Gerald Appel]] created the MACD line
- [[Thomas Aspray]] added the histogram feature to MACD  
- [[Giorgos E. Siligardos]] created a leader of MACD  

## About
- MACD employs two Moving Averages of varying lengths (which are lagging indicators) to identify trend direction and duration. 
- Then, MACD takes the difference in values between those two Moving Averages ( MACD Line) and an [[Exponential Moving Average (EMA)|EMA]] of those Moving Averages (Signal Line) and plots that difference between the two lines as a histogram which oscillates above and below a center Zero Line. 
- The histogram is used as a good indication of a security's momentum.  
  
## The MACD indicator is typically good for identifying three types of basic signals
  
### **Signal Line Crossovers**  
A Signal Line Crossover is the most common signal produced by the MACD . On the occasions where the MACD Line crosses above or below the Signal Line, that can signify a potentially strong move. The standard interpretation of such an event is a recommendation to buy if the MACD line crosses up through the Signal Line (a "bullish" crossover), or to sell if it crosses down through the Signal Line (a "bearish" crossover). These events are taken as indications that the trend in the financial instrument is about to accelerate in the direction of the crossover.  
  
### **Zero Line Crossovers**  
Zero Line Crossovers occur when the MACD Line crossed the Zero Line and either becomes positive (above 0) or negative (below 0). A change from positive to negative MACD is interpreted as "bearish", and from negative to positive as "bullish". Zero crossovers provide evidence of a change in the direction of a trend but less confirmation of its momentum than a signal line crossover  
  
 ### **Divergence**  
Divergence is another signal created by the MACD . Simply, divergence occurs when the MACD and actual price are not in agreement. A "positive divergence" or "bullish divergence" occurs when the price makes a new low but the MACD does not confirm with a new low of its own. A "negative divergence" or "bearish divergence" occurs when the price makes a new high but the MACD does not confirm with a new high of its own. A divergence with respect to price may occur on the MACD line and/or the MACD Histogram  
  
#### **Moving Average Crossovers**, 
another hidden signal that MACD Indicator identifies  
Many traders will watch for a short-term moving average to cross above a longer-term moving average and use this to signal increasing upward momentum. This [bullish](https://www.tradingview.com/scripts/bullish/) crossover suggests that the price has recently been rising at a faster rate than it has in the past, so it is a common technical buy sign. Conversely, a short-term moving average crossing below a longer-term average is used to illustrate that the asset's price has been moving downward at a faster rate and that it may be a good time to sell.  
Moving Average Crossovers in reality is Zero Line Crossovers, the value of the MACD indicator is equal to zero each time the two moving averages cross over each other. For easy interpretation by trades, Zero Line Crossovers are simply described as positive or negative MACD  
  
#### **False signals**  
Like any forecasting algorithm, the MACD can generate false signals. A false positive, for example, would be a [bullish](https://www.tradingview.com/scripts/bullish/) crossover followed by a sudden decline in a financial instrument. A false negative would be a situation where there is [bearish](https://www.tradingview.com/scripts/bearish/) crossover, yet the financial instrument accelerated suddenly upwards  
  
  
## What is “MACD-X” and Why it is “More Than MACD”  
In its simples form, MACD-X implements variety of different calculation techniques applied to obtain MACD Line. Different calculation techniques lead to different values for MACD Line, as will further discuss below, and as a consequence the signal line and the histogram values will differentiate accordingly.  
  
## Main features of MACD-X 
1. Plotting of the Oscillator presented on top of the price chart (main chart) and applicable on both log and linear scale. Maximum plotting length is limited to 250 bars  
2. Introduces different proven techniques applied on MACD calculation, such as MACD-AS (Histogram), MACD-Leader and MACD-Source, besides the traditional MACD (MACD-TRADITIONAL)  

## More MACD Indicator Variations 
• MACD-Traditional, by Gerald Appel  
	- It is the MACD that we know, stated as traditional just to avoid confusion with other techniques used with this study  
  
• MACD-Histogram, by Thomas Aspray  
	  - The MACD-Histogram measures the distance between MACD and its signal line (the 9-day [EMA](https://www.tradingview.com/scripts/ema/) of MACD ). 
	  - Aspray developed the MACD-Histogram to anticipate signal line crossovers in MACD. 
	  - Because MACD uses moving averages and moving averages lag price, signal line crossovers can come late and affect the reward-to-risk ratio of a trade. [Bullish](https://www.tradingview.com/scripts/bullish/) or [bearish](https://www.tradingview.com/scripts/bearish/) divergences in the MACD-Histogram can alert chartists to an imminent signal line crossover in MACD  
	  - Aspray's contribution served as a way to anticipate (and therefore cut down on lag) possible MACD crossovers which are a fundamental part of the indicator.  
  
• MACD-Leader, by Giorgos E. Siligardos, [PhD](https://www.tradingview.com/symbols/NYSE-PHD/)  
	  - MACD Leader has the ability to lead MACD at critical situations. 
	  - Almost all smoothing methods encounter in [technical analysis](https://www.tradingview.com/scripts/technicalanalysis/) are based on a relative-weighted sum of past prices, and the Leader is no exception. 
	  - The concealed weights of MACD Leader are such that more relative weight is used in the more recent prices than the respective weights used by the components of MACD . 
	  - In effect, the Leader expresses more changes in average price dynamics for the recent price movement than MACD , thus eventually leading MACD , especially when significant trend changes are about to take place.  
  
• MACD-Source, a custom experimental interpretation of mine,  
	  - MACD Source, presents an application of MACD that evaluates Source/MA Ratio, relatively with less lag, as a basis for MACD Line, also can be expressed as source convergence/divergence to its moving average. 
	  - Among the various techniques for removing the lag between price and moving average (MA) of the price, one in particular stands out: the addition to the moving average of a portion of the difference between the price and MA. 
	  - MACD Source, is based on signal length mean of the difference between Source and average value of shot length and long length moving average of the source (Source/MA Ratio), where the source is actual value and hence no lag and relatively less lag with the average value of moving average of the source .  
	  - MACD Source provides relatively early crossovers comparing to MACD and better momentum direction indications, assuming the lengths are set to same values  
  
## 3- Alerts presented for MACD and Signal Line Crosses both for Early Warning and Confirmed Crossovers  
  
  
## See Also  

- [MACD-X, More Than](https://www.tradingview.com/script/Gq9I627Q-MACD-X-More-Than-MACD-by-DGT/) 
- MACD by DGT, 
- [P-MACD by DGT](https://www.tradingview.com/script/ZG82h6Wi-P-MACD-by-DGT/) 
- [Price Distance to its MA by DGT](https://www.tradingview.com/script/QzjN5jCL-Price-Distance-to-its-MA-by-DGT/)