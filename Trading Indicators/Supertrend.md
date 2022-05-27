# Supertrend

#### Definition

Supertrend is a trend-following indicator based on Average True Range ([ATR](https://www.tradingview.com/scripts/averagetruerange/)). The calculation of its single line combines trend detection and volatility. It can be used to detect changes in trend direction and to position stops.

#### History

The Supertrend indicator was created by Olivier Seban.

#### Calculations

To calculate bands of the Supertrend, use the following formulas:

```
hl2 = (high + low) / 2  
basicUpperBand = hl2 + (multiplier × ATR)  
basicLowerBand = hl2 - (multiplier × ATR)  
  
upperBand = basicUpperBand < prev upperBand or prev close > prev upperBand ? basicUpperBand : prev upperBand  
lowerBand = basicLowerBand > prev lowerBand or prev close < prev lowerBand ? basicLowerBand : prev lowerBand  
  
superTrend = trendDirection == isUpTrend ? lowerBand : upperBand

//The trendDirection is determined based on the fulfillment of the following conditions:

//Until the ATR value is calculated 

trendDirection = isDownTrend  
else if prev superTrend == prev upperBand  
    trendDirection := close > upperBand ? isUpTrend : isDownTrend  
else  
    trendDirection := close < lowerBand ? isDownTrend : isUpTrend
```
#### The basics

The Supertrend is a trend-following indicator. It is overlaid on the main chart and their plots indicate the current trend. A Supertrend can be used with varying periods (daily, weekly, intraday etc.) and on varying instruments (stocks, futures or forex).

The Supertrend has several inputs that you can adjust to match your trading strategy. Adjusting these settings allows you to make the indicator more or less sensitive to price changes.

##### For the Supertrend inputs, you can adjust atrLength and multiplier:

-   the **atrLength** setting is the lookback length for the ATR calculation;
-   **multiplier** is what the ATR is multiplied by to offset the bands from price.

#### What to look for

When the price falls below the indicator curve, it turns red and indicates a downtrend. Conversely, when the price rises above the curve, the indicator turns green and indicates an uptrend. After each close above or below Supertrend, a new trend appears.

#### Summary

The Supertrend helps you make the right trading decisions. However, there are times when it generates false signals. Therefore, it is best to use the right combination of several indicators. Like any other indicator, Supertrend works best when used with other indicators such as [[Moving Average Convergence Divergence (MACD)]], [[Parabolic SAR]], or [[RSI]].


<div class="rich-link-card-container"><a class="rich-link-card" href="https://www.tradingview.com/scripts/macd/" target="_blank">
	<div class="rich-link-image-container">
		<div class="rich-link-image" style="background-image: url('https://www.tradingview.com/static/images/logo-preview.png')">
	</div>
	</div>
	<div class="rich-link-card-text">
		<h1 class="rich-link-card-title">Moving Average Convergence / Divergence (MACD) — Technical Indicators — Indicators and Signals — TradingView</h1>
		<p class="rich-link-card-description">
		The MACD is an extremely popular indicator used in technical analysis. — Indicators and Signals
		</p>
		<p class="rich-link-href">
		https://www.tradingview.com/scripts/macd/
		</p>
	</div>
</a></div>

<div class="rich-link-card-container"><a class="rich-link-card" href="https://www.tradingview.com/scripts/parabolicsar/" target="_blank">
	<div class="rich-link-image-container">
		<div class="rich-link-image" style="background-image: url('https://www.tradingview.com/static/images/logo-preview.png')">
	</div>
	</div>
	<div class="rich-link-card-text">
		<h1 class="rich-link-card-title">Parabolic Stop and Reverse (PSAR) — Technical Indicators — Indicators and Signals — TradingView</h1>
		<p class="rich-link-card-description">
		Parabolic SAR is a time and price technical analysis tool primarily used to identify points of potential stops and reverses. — Indicators and Signals
		</p>
		<p class="rich-link-href">
		https://www.tradingview.com/scripts/parabolicsar/
		</p>
	</div>
</a></div>

<div class="rich-link-card-container"><a class="rich-link-card" href="https://www.tradingview.com/scripts/relativestrengthindex/" target="_blank">
	<div class="rich-link-image-container">
		<div class="rich-link-image" style="background-image: url('https://www.tradingview.com/static/images/logo-preview.png')">
	</div>
	</div>
	<div class="rich-link-card-text">
		<h1 class="rich-link-card-title">Relative Strength Index (RSI) — Technical Indicators — Indicators and Signals — TradingView</h1>
		<p class="rich-link-card-description">
		The Relative Strength Index (RSI) is a well versed momentum based oscillator which is used to measure the speed (velocity) as well as the change (magnitude) of directional price movements. — Indicators and Signals
		</p>
		<p class="rich-link-href">
		https://www.tradingview.com/scripts/relativestrengthindex/
		</p>
	</div>
</a></div>


