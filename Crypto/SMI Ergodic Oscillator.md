---
title: SMI Ergodic Oscillator — TradingView
alias:
type: Article
knowledge-topic: 
  - 
keywords: []
URL: https://www.tradingview.com/support/solutions/43000594671-smi-ergodic-oscillator/
author: 
publisher: 
publisher-url: 
published-date: 

synonym:
plural:
acronym:
language: 
abbreviation:

reference:
see-also:
recommended-by: 

date-created: <% tp.file.creation_date("YYYY-MM-DD • HH:mm:ss") %>
date-modified: <% tp.file.last_modified_date("YYYY-MM-DD • HH:mm:ss") %>
status: 
  - current: [new|editing|researching|review]
  - history: 
    - [[<% tp.file.creation_date("YYYY-MM-DD") %>]]: markdownload-extract
---

# SMI Ergodic Oscillator — TradingView

> excerpt:: The Stochastic Momentum Index (SMI) Ergodic Oscillator, often referred to as SMIEO, uses and manipulates the SMI Ergodic indicator’s double moving averages of price minus previous price over two time frames. The indicator uses a signal line, consisting of the Exponential Moving Average (EMA) of the SMI indicator, and subtracts this from the SMI. The oscillator is displayed on the chart as a histogram, and can be altered in its settings by the trader (i.e. input, method (EMA), and period length settings).

***
#### Definition

The Stochastic Momentum Index (SMI) Ergodic Oscillator, often referred to as SMIEO, uses and manipulates the SMI Ergodic indicator’s double moving averages of price minus previous price over two time frames. The indicator uses a signal line, consisting of the Exponential Moving Average (EMA) of the SMI indicator, and subtracts this from the SMI. The oscillator is displayed on the chart as a histogram, and can be altered in its settings by the trader (i.e. input, method (EMA), and period length settings). 

#### Calculations

The following is a condensed code for the SMI Ergodic Oscillator indicator.

//price (user defined, default is closing price)

//method = moving average (user defined, default is EMA)

//prevP = previousPrice, index = current bar number

//abs = absolute value

//ma = moving average

prevP = price[index-1];

change = price - prevP;

absChange = abs(price - prevP);

tempChange = ma(method, index, fastPeriod, change);

tempAbsC = ma(method, index, fastPeriod, absChange);

tempChange = ma(method, index, slowPeriod, tempChange);

tempAbsC = ma(method, index, slowPeriod, tempAbsC);

SMI = tempChange / tempAbsC;

SIGNAL = ma(method, index, sigPeriod, SMI);

Plot: SMIEO = SMI - SIGNAL;

#### Takeaways and what to look for

The SMI Ergodic Oscillator is best used with other indicators and tools for technical analysis.

#### Summary

The SMIEO uses and manipulates the SMI Ergodic indicator’s double moving averages of price minus previous price over two timeframes. This aids the trader by giving them helpful trigger signals. The indicator uses a signal line and then subtracts this from the SMI. The trader can change indicator settings, such as input, method (EMA), and period length, depending on their trade needs or preferences.

***

## Footer

article-length:: 1722
content-direction:: ltr