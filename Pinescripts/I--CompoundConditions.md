---
---

# Compound Conditions 
## Example Indicator

```js
//@version=5 
indicator("Compound conditions") 

periodInput = input.int(20) 
bullLevelInput = input.int(55) 


r = ta.rsi(close, periodInput) 


// Condition #1. 
rsiBull = r > bullLevelInput 

// Condition #2. 
hiChannel = ta.highest(r, periodInput * 2)[1] 
aboveHiChannel = r > hiChannel 

// Condition #3. 
channelIsOld = hiChannel >= hiChannel[periodInput] 

// Condition #4. 
historyIsBull = math.sum(rsiBull ? 1 : -1, periodInput * 3) > 0 

// Compound condition. 
bull = rsiBull and aboveHiChannel and channelIsOld and historyIsBull 

hline(bullLevelInput) 

plot(r, "RSI", color.black) 
plot(hiChannel, "High Channel") 

plotchar(rsiBull ? bullLevelInput : na, "rIsBull", "1", location.absolute, color.green, size = size.tiny) 
plotchar(aboveHiChannel ? r : na, "aboveHiChannel", "2", location.absolute, size = size.tiny) 
plotchar(channelIsOld, "channelIsOld", "3", location.bottom, size = size.tiny) 
plotchar(historyIsBull, "historyIsBull", "4", location.top, size = size.tiny) 

bgcolor(bull ? not bull[1] ? color.new(color.green, 50) : color.new(color.green, 90) : na)
```

