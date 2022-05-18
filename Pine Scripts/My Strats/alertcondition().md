# alertcondition()


## PineScript Example Scripts

```Javascript
//@version=5

indicator("")

r = ta.rsi(close, 14)
xUp = ta.crossover(r, 50)

plot(r, "RSI", display = display.none)

alertcondition(xUp, "xUp alert", message = 'RSI is bullish at: {{plot("RSI")}}')
```