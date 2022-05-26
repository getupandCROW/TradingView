---
date created: Wednesday, May 25th 2022, 12:36:51 pm
date modified: Wednesday, May 25th 2022, 12:38:00 pm
title: Pinescript Variables
---

# Pinescript Variables

Some variables have function versions as well, e.g.:

-   The [ta.tr](https://www.tradingview.com/pine-script-reference/v5/#fun_ta{dot}tr) variable returns the “True Range” of the current bar. The [ta.tr(true)](https://www.tradingview.com/pine-script-reference/v5/#fun_ta{dot}tr) function call also returns the “True Range”, but when the previous [close](https://www.tradingview.com/pine-script-reference/v5/#var_close) value which is normally needed to calculate it is [na](https://www.tradingview.com/pine-script-reference/v5/#var_na), it calculates using `high - low` instead.
-   The [time](https://www.tradingview.com/pine-script-reference/v5/#var_time) variable gives the time at the [open](https://www.tradingview.com/pine-script-reference/v5/#var_open) of the current bar. The [time(timeframe)](https://www.tradingview.com/pine-script-reference/v5/#fun_time) function returns the time of the bar’s [open](https://www.tradingview.com/pine-script-reference/v5/#var_open) from the `timeframe` specified, even if the chart’s timeframe is different. The [time(timeframe, session)](https://www.tradingview.com/pine-script-reference/v5/#fun_time) function returns the time of the bar’s [open](https://www.tradingview.com/pine-script-reference/v5/#var_open) from the `timeframe` specified, but only if it is within the `session` time. The [time(timeframe, session, timezone)](https://www.tradingview.com/pine-script-reference/v5/#fun_time) function returns the time of the bar’s [open](https://www.tradingview.com/pine-script-reference/v5/#var_open) from the `timeframe` specified, but only if it is within the `session` time in the specified `timezone`.

Some variables have function versions as well, e.g.:

-   The [ta.tr](https://www.tradingview.com/pine-script-reference/v5/#fun_ta{dot}tr) variable returns the “True Range” of the current bar. The [ta.tr(true)](https://www.tradingview.com/pine-script-reference/v5/#fun_ta{dot}tr) function call also returns the “True Range”, but when the previous [close](https://www.tradingview.com/pine-script-reference/v5/#var_close) value which is normally needed to calculate it is [na](https://www.tradingview.com/pine-script-reference/v5/#var_na), it calculates using `high - low` instead.
-   The [time](https://www.tradingview.com/pine-script-reference/v5/#var_time) variable gives the time at the [open](https://www.tradingview.com/pine-script-reference/v5/#var_open) of the current bar. The [time(timeframe)](https://www.tradingview.com/pine-script-reference/v5/#fun_time) function returns the time of the bar’s [open](https://www.tradingview.com/pine-script-reference/v5/#var_open) from the `timeframe` specified, even if the chart’s timeframe is different. The [time(timeframe, session)](https://www.tradingview.com/pine-script-reference/v5/#fun_time) function returns the time of the bar’s [open](https://www.tradingview.com/pine-script-reference/v5/#var_open) from the `timeframe` specified, but only if it is within the `session` time. The [time(timeframe, session, timezone)](https://www.tradingview.com/pine-script-reference/v5/#fun_time) function returns the time of the bar’s [open](https://www.tradingview.com/pine-script-reference/v5/#var_open) from the `timeframe` specified, but only if it is within the `session` time in the specified `timezone`.

## ?:

Ternary conditional operator.

> expr1 ? expr2 : expr3

### Example

```js
// Draw circles at the bars where open crosses close
s2 = cross(open, close) ? avg(open,close) : na
plot(s2, style=plot.style_circles, linewidth=2, color=color.red)

// Combination of ?: operators for 'switch'-like logic
c = timeframe.isintraday ? color.red : timeframe.isdaily ? color.green : timeframe.isweekly ? color.blue : color.gray
plot(hl2, color=c)
```

### Returns
- expr2 if expr1 is evaluated to true, expr3 otherwise. Zero value (0 and also NaN, +Infinity, -Infinity) is considered to be false, any other value is true.

### Remarks
- Use [na](https://www.tradingview.com/pine-script-reference/v4/#var_na) for 'else' branch if you do not need it.

- You can combine two or more [?:](https://www.tradingview.com/pine-script-reference/v4/#op_{question}{colon}) operators to achieve the equivalent of a 'switch'-like statement (see examples above).

- You may use arithmetic operators with numbers as well as with series variables. In case of usage with series the operators are applied elementwise.

### See Also

[iff](https://www.tradingview.com/pine-script-reference/v4/#fun_iff)[na](https://www.tradingview.com/pine-script-reference/v4/#fun_na)
