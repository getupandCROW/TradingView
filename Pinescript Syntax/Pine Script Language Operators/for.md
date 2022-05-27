---
---

# [[for]]

> The 'for' structure allows the repeated execution of a number of statements:

```js
[var_declaration =] for counter = from_num to to_num [by step_num]  
  statements | continue | break  
  return_expression
```

**var_declaration** - An optional variable declaration that will be assigned the value of the loop's return_expression.

**counter** - A variable holding the value of the loop's counter, which is incremented/decremented by 1 or by the step_num value on each iteration of the loop.

**from_num** - The starting value of the counter. "series int/float" values/expressions are allowed.

**to_num** - The end value of the counter. When the counter becomes greater than to_num (or less than to_num in cases where from_num > to_num) the loop is broken. "series int/float" values/expressions are allowed, but they are evaluated only on the loop's first iteration.

**step_num** - The increment/decrement value of the counter. It is optional. The default value is +1 or -1, depending on which of from_num or to_num is the greatest. When a value is used, the counter is also incremented/decremented depending on which of from_num or to_num is the greatest, so the +/- sign of step_num is optional.

**statements | continue | break** - Any number of statements, or the 'continue' or 'break' keywords, indented by 4 spaces or a tab.

**return_expression** - The loop's return value which is assigned to the variable in var_declaration if one is present. If the loop exits because of a 'continue' or 'break' keyword, the loop's return value is that of the last variable assigned a value before the loop's exit.

**continue** - A keyword that can only be used in loops. It causes the next iteration of the loop to be executed.

**break** - A keyword that exits the loop.

## Example

```js
//@version=5
indicator("for")
// Here, we count the quantity of bars in a given 'lookback' length which closed above the current bar's close
qtyOfHigherCloses(lookback) =>
	int result = 0
	for i = 1 to lookback
		if close[i] > close
			result += 1
	result
plot(qtyOfHigherCloses(14))
```

## See also
- [[while]]

# [[for...in]]

> The `for...in` structure allows the repeated execution of a number of statements for each element in an array. 

- It can be used with either one argument: `array_element`, or with two: `[index, array_element]`. 
- The second form doesn't affect the functionality of the loop. It tracks the current iteration's index in the tuple's first variable.


```js
[var_declaration =] for array_element in array_id  
  statements | continue | break  
  return_expression  
  
[var_declaration =] for [index, array_element] in array_id  
  statements | continue | break  
  return_expression
```

**var_declaration** - An optional variable declaration that will be assigned the value of the loop's `return_expression`.

**index** - An optional variable that tracks the current iteration's index. Indexing starts at 0. The variable is immutable in the loop's body. When used, it must be included in a tuple also containing `array_element`.

**array_element** - A variable containing each successive array element to be processed in the loop. The variable is immutable in the loop's body.

**array_id** - The ID of the array over which the loop is iterated.

**statements | continue | break** - Any number of statements, or the 'continue' or 'break' keywords, indented by 4 spaces or a tab.

**return_expression** - The loop's return value assigned to the variable in `var_declaration`, if one is present. If the loop exits because of a 'continue' or 'break' keyword, the loop's return value is that of the last variable assigned a value before the loop's exit.

**continue** - A keyword that can only be used in loops. It causes the next iteration of the loop to be executed.

**break** - A keyword that exits the loop.

It is allowed to modify the array's elements or its size inside the loop.

## Here, we use the single-argument form of `for...in` to determine on each bar how many of the bar's OHLC values are greater than the SMA of 'close' values:

### Example

```js
//@version=5
indicator("for...in")
// Here we determine on each bar how many of the bar's OHLC values are greater than the SMA of 'close' values
float[] ohlcValues = array.from(open, high, low, close)
qtyGreaterThan(value, array) =>
	int result = 0
	for currentElement in array
		if currentElement > value
			result += 1
		result
plot(qtyGreaterThan(ta.sma(close, 20), ohlcValues))
```

## Here, we use the two-argument form of [for...in](https://www.tradingview.com/pine-script-reference/v5/#op_for{dot}{dot}{dot}in) to set the values of our `isPos` array to `true` when their corresponding value in our `valuesArray` array is positive:

### Example

```js
//@version=5
indicator("for...in")
var valuesArray = array.from(4, -8, 11, 78, -16, 34, 7, 99, 0, 55)
var isPos = array.new_bool(10, false)

for [index, value] in valuesArray
	if value > 0
		array.set(isPos, index, true)

if barstate.islastconfirmedhistory
	label.new(bar_index, high, str.tostring(isPos))
```

## Iterate through matrix rows as arrays.

### Example

```js
//@version=5
indicator("`for ... in` matrix Example")

// Create a 2x3 matrix with values `4`.
matrix1 = matrix.new<int>(2, 3, 4)

sum = 0.0
// Loop through every row of the matrix.
for rowArray in matrix1
	// Sum values of the every row 
	sum += array.sum(rowArray)

plot(sum)
```

## See also
- [[for]]
- [[while]]
- [[array.sum]]
- [[array.min]]
- [[array.max]]