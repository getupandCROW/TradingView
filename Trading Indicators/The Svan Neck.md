# The Svan Neck

[thekarasystem](https://www.tradingview.com/u/thekarasystem/)[PREMIUM](https://www.tradingview.com/gopro/?source=badge&feature=pro_premium)Apr 15

[Bands and Channels](https://www.tradingview.com/scripts/bandsandchannels/) [Moving Averages](https://www.tradingview.com/scripts/movingaverage/) [savetrading](https://www.tradingview.com/scripts/savetrading/) [littlerisk](https://www.tradingview.com/scripts/littlerisk/) [trendfollowing](https://www.tradingview.com/scripts/trendfollowing/)



The Svan-Neck is a fixed EMA-200 Trading channel, which is set to 4 and 6 hours. The reason why it is fixed is because the big timeframes are still very important to consider. e.g. It could be that the price moves for a long time above both EMAs but it shows a [bearish](https://www.tradingview.com/scripts/bearish/) divergence (e.g. OBV, [RSI](https://www.tradingview.com/scripts/relativestrengthindex/) , etc). If divergences play out depends - among other factors - on the stretch of a bull run, thus it is essential to use bigger time frames (i.e. The Svan Neck is a trend-following indicator used for a multi-timeframe analysis.).  
  
## How to Trade?  
  
One could use a 2 Position entry system. If the price drops in the uptrend to EMA-4H-200-HIGH one could buy in the first time. The next buy in is on the bounce of the EMA-6H-200-LOW. The first trade is closed if the previous ATH is reached. The second could continue while the SL is being trailed. The SL for Position 1 is 2.5ATR below the EMA-6H-200-LOW. The SL for Position 2 is the same.  
  
The same applies for a downtrend.  
  
> After the Svan Neck is touched multiple times in a short time frame, it's a choppy market and you should rely on other indicators until a confirmed trend is visible.

## Code

```js
//@version=5
indicator(title='TKS::INDI:The Svan Neck', overlay=true)

ema4h = request.security(syminfo.tickerid, "240", ta.ema(close, 200))
ema6h = request.security(syminfo.tickerid, "360", ta.ema(close, 200))

pEMA4h = plot(ema4h, color=color.blue, title="EMA-HIGH")
pEMA6h = plot(ema6h, color=color.purple, title="EMA-LOW")

fill(pEMA4h, pEMA6h, color= (close < ema4h and close < ema6h) ? color.new(color.red, 80) : color.new(color.teal, 80))

```