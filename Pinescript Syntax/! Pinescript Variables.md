---
date created: Wednesday, May 25th 2022, 12:36:51 pm
date modified: Wednesday, May 25th 2022, 12:38:00 pm
title: Pinescript Variables
---

# Pinescript Variables

> Some **variables** have **function** versions as well, e.g.:

### [[ta.tr()]]
-   The [ta.tr] variable returns the “True Range” of the current bar. The [ta.tr(true)] function call also returns the “True Range”, but when the previous [close] value which is normally needed to calculate it is [na], it calculates using **high - low** instead.

### [[time()]]
- The [time] variable gives the time at the [open] of the current bar. 
- The [time(timeframe)] function returns the time of the bar’s [open] from the **timeframe** specified, even if the chart’s timeframe is different. 
- The [time(timeframe, session)] function returns the time of the bar’s [open] from the **timeframe** specified, but only if it is within the **session time**. 
- The [time(timeframe, session, timezone)] function returns the time of the bar’s [open] from the **timeframe** specified, but only if it is within the **session time** in the specified **timezone**.

## [[? :]]

Ternary conditional operator.

> `expr1 ? expr2 : expr3`

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
- expr2 if expr1 is evaluated to true, expr3 otherwise. 
- Zero value (0 and also NaN, +Infinity, -Infinity) is considered to be false, any other value is true.

### Remarks
- Use [na] for 'else' branch if you do not need it.
- You can combine two or more [? :] operators to achieve the equivalent of a 'switch'-like statement.
- You may use arithmetic operators with numbers as well as with series variables. In case of usage with series the operators are applied elementwise.

### See Also
- [[iff()]]
- [[na]]

## Variable Types
- series <mark style="background: #FFB8EBA6;">string</mark> 
- series <mark style="background: #FFB86CA6;">bool</mark> 
- series <mark style="background: #FFF3A3A6;">int</mark> 
- series <mark style="background: #BBFABBA6;">float</mark> 
- 

## [[var]]

**var** is the keyword used for assigning and one-time initializing of the variable.

Normally, a syntax of assignment of variables, which doesn’t include the keyword var, results in the value of the variable being overwritten with every update of the data. Contrary to that, when assigning variables with the keyword var, they can “keep the state” despite the data updating, only changing it when conditions within if-expressions are met.

`var variable_name = expression`

### where:
- **variable_name** - any name of the user’s variable that’s allowed in Pine Script™ (can contain capital and lowercase Latin characters, numbers, and underscores, but can’t start with a number).
- **expression** - any arithmetic expression, just as with defining a regular variable. The expression will be calculated and assigned to a variable once.

### Example

```js
//@version=5
indicator("Var keyword example")
var a = close
var b = 0.0
var c = 0.0
var green_bars_count = 0
if close > open
	var x = close
	b := x
	green_bars_count := green_bars_count + 1
	if green_bars_count >= 10
		var y = close
		c := y
plot(a)
plot(b)
plot(c)
```

	- The variable 'a' keeps the closing price of the first bar for each bar in the series.
	- The variable 'b' keeps the closing price of the first "green" bar in the series.
	- The variable 'c' keeps the closing price of the tenth "green" bar in the series.

## [[varip]]
**varip** (var intrabar persist) is the keyword used for assigning and one-time initializing of a variable. It is similar to the var keyword, but variables declared with varip retain their values between the updates of a real-time bar.

`varip variable_name = expression`

### where:
**variable_name** - any name of the user's variable that's allowed in Pine Script™ (can contain capital and lowercase Latin characters, numbers, and underscores, but can't start with a number).
**expression** - any arithmetic expression, just as when defining a regular variable. The expression will be calculated and assigned to the variable only once, on the first bar.

### Example
```js
//@version=5
indicator("varip")
varip int v = -1
v := v + 1
plot(v)
```

	With var, the plot would return the value of bar_index. With varip, the same behavior occurs on historical bars, but in the real-time bar, the plot returns a value that increases by one for each tick.

### Remarks
Can be used only with simple types such as float, int, bool, string, and with arrays of these types.


## Footer

