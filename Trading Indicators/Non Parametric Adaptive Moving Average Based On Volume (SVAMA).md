# SVAMA - A Non Parametric Adaptive Moving Average Based On Volume

[alexgrover](https://www.tradingview.com/u/alexgrover/)[WIZARD](https://www.tradingview.com/pine-wizards/ "Pine Wizard | Premium")Jul 19, 2019

Advanced Micro Devices Inc

15

[Trend Analysis](https://www.tradingview.com/scripts/trendanalysis/) [Volume](https://www.tradingview.com/scripts/volumestudies/) [Moving Averages](https://www.tradingview.com/scripts/movingaverage/) [adaptive](https://www.tradingview.com/scripts/adaptive/) [noparameters](https://www.tradingview.com/scripts/noparameters/) [smooth](https://www.tradingview.com/scripts/smooth/) [filter](https://www.tradingview.com/scripts/filter/) [trend](https://www.tradingview.com/scripts/trend/) [cross](https://www.tradingview.com/scripts/cross/)

**Introduction**  
  
Technical indicators often have parameters settings that the user must enter, those are inconvenient when the user must design a strategy because such settings must be optimized, it must also been noted that the optimal settings at time _t_ could change at time _t+n_, this is why non parametric indicators are more efficient. Today i propose a moving average adapting to the market [volume](https://www.tradingview.com/scripts/volume/) without using parameters affecting the smoothing.  
  
**The Indicator**  
  
The [volume](https://www.tradingview.com/scripts/volume/) is rescaled in a range of (1,0) by using max or min normalization. Exponential averaging is used to provide the moving average.  
  
When using max normalization the moving average react faster when the [volume](https://www.tradingview.com/scripts/volume/) is closer to its all time high, when using min normalization the moving average react faster when the [volume](https://www.tradingview.com/scripts/volume/) is closer to its all time low. You can select the method _(max or min)_ from the "Method" parameter.  
  

[![snapshot](https://www.tradingview.com/x/ztoeAxmS)](https://www.tradingview.com/x/ztoeAxmS)

  
[Volume](https://www.tradingview.com/scripts/volume/) tend to be higher and more periodic with higher time-frames, this is why lower time-frames might return smoother results when using the Max method. It is recommended to use the Max method when we want a faster moving average while the Min method is more suited to get a slower moving average.  
  

[![snapshot](https://www.tradingview.com/x/paEL7MnK)](https://www.tradingview.com/x/paEL7MnK)

  
Both methods can provide an interesting MA-Cross system when used on higher time frames.  
  
**Conclusion**  
  
There should be more non parametric indicators, this would allow for faster and easier optimization processes when creating a strategy, in theory any indicator using a moving average or highest/lowest could be made non parametric by using a running mean or running max/min but the indicator might loose important information.  
  
This is one of my main focus right now since such indicators could also allow for improvements when used with artificial intelligence. I hope you find an use to it, don't hesitate to send me your suggestions.

## Code

```js
//@version=4
study("SVAMA",overlay=true)
Method = input("Max",options=["Max","Min"])
//----
h = 0.,l = 0.,c = 0.
//----
a = volume
h := a > nz(h[1],a) ? a : nz(h[1],a)
l := a < nz(l[1],a) ? a : nz(l[1],a)
//----
b = Method == "Max" ? a/h : l/a 
c := b*close+(1-b)*nz(c[1],close)
//----
plot(c,color=#2196f3,linewidth=2,transp=0)
```