# Pinescript Functions

### `na` value

- `float myVar = na`
***OR***
- `myVar = float(na)`

To test if some value is [na](https://www.tradingview.com/pine-script-reference/v4/#var_na), a special function must be used: [na()](https://www.tradingview.com/pine-script-reference/v4/#fun_na). 
For example:

`myClose = na(myVar) ? 0 : close`

Do not use the `==` operator to test for [na](https://www.tradingview.com/pine-script-reference/v4/#var_na) values, as this method is unreliable.

Designing your calculations so they are [na](https://www.tradingview.com/pine-script-reference/v4/#var_na)-resistant is often useful. In this example, we define a condition that is `true` when the bar’s [close](https://www.tradingview.com/pine-script-reference/v5/#var_close) is higher than the previous one. For this calculation to work correctly on the dataset’s first bar where no previous close exists and `close[1]` will return [na](https://www.tradingview.com/pine-script-reference/v4/#var_na), we use the [nz()](https://www.tradingview.com/pine-script-reference/v4/#fun_nz) function to replace it with the current bar’s [open](https://www.tradingview.com/pine-script-reference/v5/#var_open) for that special case:

`bool risingClose = close > nz(close[1], open)`

Protecting against [na](https://www.tradingview.com/pine-script-reference/v4/#var_na) values can also be useful to prevent an initial [na](https://www.tradingview.com/pine-script-reference/v4/#var_na) value from propagating in a calculation’s result on all bars. This happens here because the initial value of `ath` is [na](https://www.tradingview.com/pine-script-reference/v4/#var_na), and [math.max()](https://www.tradingview.com/pine-script-reference/v5/#fun_math{dot}max) returns [na](https://www.tradingview.com/pine-script-reference/v4/#var_na) if one of its arguments is [na](https://www.tradingview.com/pine-script-reference/v4/#var_na):

```pine
// Declare `ath` and initialize it with `na` on the first bar.
var float ath = na
// On all bars, calculate the maximum between the `high` and the previous value of `ath`.
ath := math.max(ath, high)
```

To protect against this, we could instead use:

```pine
var float ath = na
ath := math.max(nz(ath), high)
```

where we are replacing any [na](https://www.tradingview.com/pine-script-reference/v4/#var_na) values of `ath` with zero. Even better would be:

```pine
var float ath = high
ath := math.max(ath, high)
```

There is no auto-casting rule that can automatically cast a “float” to an “int”, so we will need to do the job ourselves. For this, we will use the [int()](https://www.tradingview.com/pine-script-reference/v5/#fun_int) function to force the type conversion of the value we supply as a length to [ta.sma()](https://www.tradingview.com/pine-script-reference/v5/#fun_ta{dot}sma) from “float” to “int”:

```pine
//@version=5
indicator("")
len = 10.0
s = ta.sma(close, int(len))
plot(s)
```

Explicit type-casting can also be useful when declaring variables and initializing them to [na](https://www.tradingview.com/pine-script-reference/v4/#var_na) which can be done in two ways:

```pine
// Cast `na` to the "label" type.
lbl = label(na)
// Explicitly declare the type of the new variable.
label lbl = na
```

***


### import()


Used to load an external [library](https://www.tradingview.com/pine-script-reference/v5/#fun_library) into a script and bind its functions to a namespace. The importing script can be an indicator, a strategy, or another library. A library must be published (privately or publicly) before it can be imported.

import {username}/{libraryName}/{libraryVersion} as {alias}

#### Example

```js
//@version=5
indicator("num_methods import")
```

#### Arguments

- **username** (literal string) User name of the library's author.

- **libraryName** (literal string) Name of the imported library, which corresponds to the `title` argument used by the author in his library script.

- **libraryVersion** (literal int) Version number of the imported library.

- **alias** (literal string) Namespace used to refer to the library's functions. Optional. The default is the libraryName string.


#### Indicator

```js
indicator(title, shorttitle, overlay, format, precision, scale, max_bars_back, timeframe, timeframe_gaps, explicit_plot_zorder, max_lines_count, max_labels_count, max_boxes_count) → void
```


##### Arguments

- **title** (const string) indicator title that would be seen in Indicators widget. Argument IS REQUIRED.

- **shorttitle** (const string) indicator short title that would be seen in the chart legend. Argument is optional.

- **overlay** (const bool) if true the indicator will be added as an overlay for the main series. If false - it would be added on a separate chart pane. Default is false.

- **format** (const string) type of formatting indicator values on the price axis. Possible values are: [format.inherit](https://www.tradingview.com/pine-script-reference/v5/#var_format{dot}inherit), [format.price](https://www.tradingview.com/pine-script-reference/v5/#var_format{dot}price), [format.volume](https://www.tradingview.com/pine-script-reference/v5/#var_format{dot}volume). Default is [format.inherit](https://www.tradingview.com/pine-script-reference/v5/#var_format{dot}inherit).

- **precision** (const int) number of digits after the floating point for indicator values on the price axis. Must be a non negative integer and not greater than 16. If omitted, using formatting from parent series. If format is [format.inherit](https://www.tradingview.com/pine-script-reference/v5/#var_format{dot}inherit) and this argument is set, then format becomes [format.price](https://www.tradingview.com/pine-script-reference/v5/#var_format{dot}price).

- **scale** (scale_type) price scale that the indicator should be attached to. Possible values are: [scale.right](https://www.tradingview.com/pine-script-reference/v5/#var_scale{dot}right), [scale.left](https://www.tradingview.com/pine-script-reference/v5/#var_scale{dot}left), [scale.none](https://www.tradingview.com/pine-script-reference/v5/#var_scale{dot}none). Value [scale.none](https://www.tradingview.com/pine-script-reference/v5/#var_scale{dot}none) can be applied only in combination with 'overlay=true' setting. If omitted, using scale from main series.

- **max_bars_back** (const int) Maximum number of bars available for a indicator for historical reference. This parameter is applied to every built-in or user variable in the script if there is a reference to historical data of a variable in the script code (‘[]’ operator is used). Variable buffer sizes in the Pine Script are typically autodetected. This however is not possible in certain cases which is why the parameter allows a user to manually set the lower bound of this value. NOTE: using of the [max_bars_back](https://www.tradingview.com/pine-script-reference/v5/#fun_max_bars_back) function instead of the parameter is optimal because it applies to only one variable.

- **timeframe** (const string) custom resolution of the indicator, which defines indicator input and behavior like a indicator body in the security context. If you specify the empty string resolution, it will appear the same as on the chart. Argument is optional.

- **max_lines_count** (const int) The number of last line drawings displayed. The default value is 50 and the maximum allowed is 500.

- **max_labels_count** (const int) The number of last label drawings displayed. The default value is 50 and the maximum allowed is 500.

- **timeframe_gaps** (const bool) Can be [true](https://www.tradingview.com/pine-script-reference/v5/#op_true) or [false](https://www.tradingview.com/pine-script-reference/v5/#op_false). When the indicator is allowed to work with other timeframes because the `timeframe` parameter is used, this determines if the higher timeframe data will contain gaps. When [true](https://www.tradingview.com/pine-script-reference/v5/#op_true), higher timeframe values only appear on the bar where they become available, and `na` values are used on other bars. When [false](https://www.tradingview.com/pine-script-reference/v5/#op_false), `na` values are replaced by the last known higher timeframe value. Optional. The default is ‘true’.

- **max_boxes_count** (const int) The number of last box drawings displayed. The default value is 50 and the maximum allowed is 500.

- **explicit_plot_zorder** (const bool) Specifies the order in which the indicator's plots, fills, and hlines are rendered. If true, the plots will be drawn based on the order in which they appear in the indicator's code, each newer plot being drawn above the previous ones. This only applies to plot*() functions, [fill](https://www.tradingview.com/pine-script-reference/v5/#fun_fill), and [hline](https://www.tradingview.com/pine-script-reference/v5/#fun_hline). Optional. The default is `false`.


#### plotshape

- Plots visual shapes on the chart.

> plotshape(series, title, style, location, color, offset, text, textcolor, editable, size, show_last, display) → void

##### Example

```js
//@version=5
indicator("plotshape example 1", overlay=true)
data = close >= open
plotshape(data, style=shape.xcross)
```

##### Arguments

series (series bool) Series of data to be plotted as shapes. Series is treated as a series of boolean values for all location values except [location.absolute](https://www.tradingview.com/pine-script-reference/v5/#var_location{dot}absolute). Required argument.

title (const string) Title of the plot.

style (input string) Type of plot. Possible values are: [shape.xcross](https://www.tradingview.com/pine-script-reference/v5/#var_shape{dot}xcross), [shape.cross](https://www.tradingview.com/pine-script-reference/v5/#var_shape{dot}cross), [shape.triangleup](https://www.tradingview.com/pine-script-reference/v5/#var_shape{dot}triangleup), [shape.triangledown](https://www.tradingview.com/pine-script-reference/v5/#var_shape{dot}triangledown), [shape.flag](https://www.tradingview.com/pine-script-reference/v5/#var_shape{dot}flag), [shape.circle](https://www.tradingview.com/pine-script-reference/v5/#var_shape{dot}circle), [shape.arrowup](https://www.tradingview.com/pine-script-reference/v5/#var_shape{dot}arrowup), [shape.arrowdown](https://www.tradingview.com/pine-script-reference/v5/#var_shape{dot}arrowdown), [shape.labelup](https://www.tradingview.com/pine-script-reference/v5/#var_shape{dot}labelup), [shape.labeldown](https://www.tradingview.com/pine-script-reference/v5/#var_shape{dot}labeldown), [shape.square](https://www.tradingview.com/pine-script-reference/v5/#var_shape{dot}square), [shape.diamond](https://www.tradingview.com/pine-script-reference/v5/#var_shape{dot}diamond). Default value is [shape.xcross](https://www.tradingview.com/pine-script-reference/v5/#var_shape{dot}xcross).

location (input string) Location of shapes on the chart. Possible values are: [location.abovebar](https://www.tradingview.com/pine-script-reference/v5/#var_location{dot}abovebar), [location.belowbar](https://www.tradingview.com/pine-script-reference/v5/#var_location{dot}belowbar), [location.top](https://www.tradingview.com/pine-script-reference/v5/#var_location{dot}top), [location.bottom](https://www.tradingview.com/pine-script-reference/v5/#var_location{dot}bottom), [location.absolute](https://www.tradingview.com/pine-script-reference/v5/#var_location{dot}absolute). Default value is [location.abovebar](https://www.tradingview.com/pine-script-reference/v5/#var_location{dot}abovebar).

color (series color) Color of the shapes. You can use constants like 'color=color.red' or 'color=#ff001a' as well as complex expressions like 'color = close >= open ? color.green : color.red'. Optional argument.

offset (series int) Shifts shapes to the left or to the right on the given number of bars. Default is 0.

text (const string) Text to display with the shape. You can use multiline text, to separate lines use '\n' escape sequence. Example: 'line one\nline two'.

textcolor (series color) Color of the text. You can use constants like 'textcolor=color.red' or 'textcolor=#ff001a' as well as complex expressions like 'textcolor = close >= open ? color.green : color.red'. Optional argument.

editable (const bool) If true then plotshape style will be editable in Format dialog. Default is true.

show_last (input int) If set, defines the number of shapes (from the last bar back to the past) to plot on chart.

size (const string) Size of shapes on the chart. Possible values are: [size.auto](https://www.tradingview.com/pine-script-reference/v5/#var_size{dot}auto), [size.tiny](https://www.tradingview.com/pine-script-reference/v5/#var_size{dot}tiny), [size.small](https://www.tradingview.com/pine-script-reference/v5/#var_size{dot}small), [size.normal](https://www.tradingview.com/pine-script-reference/v5/#var_size{dot}normal), [size.large](https://www.tradingview.com/pine-script-reference/v5/#var_size{dot}large), [size.huge](https://www.tradingview.com/pine-script-reference/v5/#var_size{dot}huge). Default is [size.auto](https://www.tradingview.com/pine-script-reference/v5/#var_size{dot}auto).

display (plot_display) Controls where the plot is displayed. Possible values are: [display.none](https://www.tradingview.com/pine-script-reference/v5/#var_display{dot}none), [display.all](https://www.tradingview.com/pine-script-reference/v5/#var_display{dot}all). Default is [display.all](https://www.tradingview.com/pine-script-reference/v5/#var_display{dot}all).

##### Remarks

Use [plotshape](https://www.tradingview.com/pine-script-reference/v5/#fun_plotshape) function in conjunction with 'overlay=true' [indicator](https://www.tradingview.com/pine-script-reference/v5/#fun_indicator) parameter!

##### also

[plot](https://www.tradingview.com/pine-script-reference/v5/#fun_plot)[plotchar](https://www.tradingview.com/pine-script-reference/v5/#fun_plotchar)[plotarrow](https://www.tradingview.com/pine-script-reference/v5/#fun_plotarrow)[barcolor](https://www.tradingview.com/pine-script-reference/v5/#fun_barcolor)[bgcolor](https://www.tradingview.com/pine-script-reference/v5/#fun_bgcolor)



##### plotchar

```Javascript
study('plotchar example', overlay=true)
data = close >= open
plotchar(data, char='↓', color=lime)
plotchar(data, char='↑', location=location.belowbar, color=red)
```

### library()

Declaration statement identifying a script as a [library](https://www.tradingview.com/pine-script-docs/en/v5/concepts/Libraries.html).

> library(title, overlay) → void

#### Example

```js
//@version=5
// @description Math library
library("num_methods", overlay = true)
// Calculate "sinh()" from the float parameter `x`
export sinh(float x) =>
	(math.exp(x) - math.exp(-x)) / 2.0
plot(sinh(0))
```

#### Arguments

title (const string) The title of the library and its identifier. It cannot contain spaces, special characters or begin with a digit. It is used as the publication's default title, and to uniquely identify the library in the [import](https://www.tradingview.com/pine-script-reference/v5/#op_import) statement, when another script uses it. It is also used as the script's name on the chart.

overlay (const bool) If true, the library will be added over the chart. If false, it will be added in a separate pane. Optional. The default is false.

#### See also

[indicator](https://www.tradingview.com/pine-script-reference/v5/#fun_indicator)[strategy](https://www.tradingview.com/pine-script-reference/v5/#fun_strategy)

### export

Used in libraries to prefix the declaration of functions that will be available from other scripts importing the library.

#### Example

```js
//@version=5
//@description Library of debugging functions.
library("Debugging_library", overlay = true)
//@function Displays a string as a table cell for debugging purposes.
//@param txt String to display.
//@returns Void.
export print(string txt) => 
	var table t = table.new(position.middle_right, 1, 1)
	table.cell(t, 0, 0, txt, bgcolor = color.yellow)
// Using the function from inside the library to show an example on the published chart.
// This has no impact on scripts using the library.
print("Library Test")
```

#### Remarks

Each library must have at least one exported function. Exported functions cannot use variables from the global scope if they are arrays, mutable variables (reassigned with `:=`), or variables of 'input' form. Exported functions cannot use request.* functions, e.g. [request.security](https://www.tradingview.com/pine-script-reference/v5/#fun_request{dot}security). Exported functions must explicitly declare the type of their arguments, and all arguments must be used in the function's body. By default, all arguments of exported functions are of the [series](https://www.tradingview.com/pine-script-reference/v5/#op_series) form, unless explicitly specified as [simple](https://www.tradingview.com/pine-script-reference/v5/#op_simple) type in the function signature. The @description, @function, @param, and @returns directives are used to automatically generate the library's release notes, and in the Pine Editor's tooltips.

#### See also

[library](https://www.tradingview.com/pine-script-reference/v5/#fun_library)[import](https://www.tradingview.com/pine-script-reference/v5/#op_import)[simple](https://www.tradingview.com/pine-script-reference/v5/#op_simple)[series](https://www.tradingview.com/pine-script-reference/v5/#op_series)

### Inputs

Adds an input to the Inputs tab of your script's Settings, which allows you to provide configuration options to script users. This function automatically detects the type of the argument used for 'defval' and uses the corresponding input widget.

`input(defval, title, tooltip, inline, group) → input bool`

`input(defval, title, tooltip, inline, group) → input color`

`input(defval, title, tooltip, inline, group) → input int`

`input(defval, title, tooltip, inline, group) → input float`

`input(defval, title, tooltip, inline, group) → input string`

`input(defval, title, inline, group, tooltip) → series float`

#### Example

```js
//@version=5
indicator("input", overlay=true)
i_switch = input(true, "On/Off")
plot(i_switch ? open : na)

i_len = input(7, "Length")
i_src = input(close, "Source")
plot(ta.sma(i_src, i_len))

i_border = input(142.50, "Price Border")
hline(i_border)
bgcolor(close > i_border ? color.green : color.red)

i_col = input(color.red, "Plot Color")
plot(close, color=i_col)

i_text = input("Hello!", "Message")
l = label.new(bar_index, high, text=i_text)
label.delete(l[1])
```

###### Returns

- Value of input variable.

##### Arguments

**defval** (const int/float/bool/string/color or source-type built-ins) Determines the default value of the input variable proposed in the script's "Settings/Inputs" tab, from where script users can change it. Source-type built-ins are built-in series float variables that specify the source of the calculation: `close`, `hlc3`, etc.

**title** (const string) Title of the input. If not specified, the variable name is used as the input's title. If the title is specified, but it is empty, the name will be an empty string.

**tooltip** (const string) The string that will be shown to the user when hovering over the tooltip icon.

**inline** (const string) Combines all the input calls using the same argument in one line. The string used as an argument is not displayed. It is only used to identify inputs belonging to the same line.

**group** (const string) Creates a header above all inputs using the same group argument string. The string is also used as the header's text.

##### Remarks

Result of [input](https://www.tradingview.com/pine-script-reference/v5/#fun_input) function always should be assigned to a variable, see examples above.

##### See also

[input.bool](https://www.tradingview.com/pine-script-reference/v5/#fun_input{dot}bool)[input.color](https://www.tradingview.com/pine-script-reference/v5/#fun_input{dot}color)[input.int](https://www.tradingview.com/pine-script-reference/v5/#fun_input{dot}int)[input.float](https://www.tradingview.com/pine-script-reference/v5/#fun_input{dot}float)[input.string](https://www.tradingview.com/pine-script-reference/v5/#fun_input{dot}string)[input.symbol](https://www.tradingview.com/pine-script-reference/v5/#fun_input{dot}symbol)[input.timeframe](https://www.tradingview.com/pine-script-reference/v5/#fun_input{dot}timeframe)[input.text_area](https://www.tradingview.com/pine-script-reference/v5/#fun_input{dot}text_area)[input.session](https://www.tradingview.com/pine-script-reference/v5/#fun_input{dot}session)[input.source](https://www.tradingview.com/pine-script-reference/v5/#fun_input{dot}source)[input.time](https://www.tradingview.com/pine-script-reference/v5/#fun_input{dot}time)

#### input.bool

Adds an input to the Inputs tab of your script's Settings, which allows you to provide configuration options to script users. This function adds a checkmark to the script's inputs.

input.bool(defval, title, tooltip, inline, group, confirm) → input bool

##### Example

```js
//@version=5
indicator("input.bool", overlay=true)
i_switch = input.bool(true, "On/Off")
plot(i_switch ? open : na)
```

###### Returns

Value of input variable.

##### Arguments

defval (const bool) Determines the default value of the input variable proposed in the script's "Settings/Inputs" tab, from where the user can change it.

title (const string) Title of the input. If not specified, the variable name is used as the input's title. If the title is specified, but it is empty, the name will be an empty string.

tooltip (const string) The string that will be shown to the user when hovering over the tooltip icon.

inline (const string) Combines all the input calls using the same argument in one line. The string used as an argument is not displayed. It is only used to identify inputs belonging to the same line.

group (const string) Creates a header above all inputs using the same group argument string. The string is also used as the header's text.

confirm (const bool) If true, then user will be asked to confirm input value before indicator is added to chart. Default value is false.

##### Remarks

Result of [input.bool](https://www.tradingview.com/pine-script-reference/v5/#fun_input{dot}bool) function always should be assigned to a variable, see examples above.

See also

[input.int](https://www.tradingview.com/pine-script-reference/v5/#fun_input{dot}int)[input.float](https://www.tradingview.com/pine-script-reference/v5/#fun_input{dot}float)[input.string](https://www.tradingview.com/pine-script-reference/v5/#fun_input{dot}string)[input.text_area](https://www.tradingview.com/pine-script-reference/v5/#fun_input{dot}text_area)[input.symbol](https://www.tradingview.com/pine-script-reference/v5/#fun_input{dot}symbol)[input.timeframe](https://www.tradingview.com/pine-script-reference/v5/#fun_input{dot}timeframe)[input.session](https://www.tradingview.com/pine-script-reference/v5/#fun_input{dot}session)[input.source](https://www.tradingview.com/pine-script-reference/v5/#fun_input{dot}source)[input.color](https://www.tradingview.com/pine-script-reference/v5/#fun_input{dot}color)[input.time](https://www.tradingview.com/pine-script-reference/v5/#fun_input{dot}time)[input](https://www.tradingview.com/pine-script-reference/v5/#fun_input)

#### input.color

Adds an input to the Inputs tab of your script's Settings, which allows you to provide configuration options to script users. This function adds a color picker that allows the user to select a color and transparency, either from a palette or a hex value.

input.color(defval, title, tooltip, inline, group, confirm) → input color

#### Example

```js
//@version=5
indicator("input.color", overlay=true)
i_col = input.color(color.red, "Plot Color")
plot(close, color=i_col)
```

Returns

Value of input variable.

Arguments

defval (const color) Determines the default value of the input variable proposed in the script's "Settings/Inputs" tab, from where the user can change it.

title (const string) Title of the input. If not specified, the variable name is used as the input's title. If the title is specified, but it is empty, the name will be an empty string.

tooltip (const string) The string that will be shown to the user when hovering over the tooltip icon.

inline (const string) Combines all the input calls using the same argument in one line. The string used as an argument is not displayed. It is only used to identify inputs belonging to the same line.

group (const string) Creates a header above all inputs using the same group argument string. The string is also used as the header's text.

confirm (const bool) If true, then user will be asked to confirm input value before indicator is added to chart. Default value is false.

Remarks

Result of [input.color](https://www.tradingview.com/pine-script-reference/v5/#fun_input{dot}color) function always should be assigned to a variable, see examples above.

#### See also

[input.bool](https://www.tradingview.com/pine-script-reference/v5/#fun_input{dot}bool)[input.int](https://www.tradingview.com/pine-script-reference/v5/#fun_input{dot}int)[input.float](https://www.tradingview.com/pine-script-reference/v5/#fun_input{dot}float)[input.string](https://www.tradingview.com/pine-script-reference/v5/#fun_input{dot}string)[input.text_area](https://www.tradingview.com/pine-script-reference/v5/#fun_input{dot}text_area)[input.symbol](https://www.tradingview.com/pine-script-reference/v5/#fun_input{dot}symbol)[input.timeframe](https://www.tradingview.com/pine-script-reference/v5/#fun_input{dot}timeframe)[input.session](https://www.tradingview.com/pine-script-reference/v5/#fun_input{dot}session)[input.source](https://www.tradingview.com/pine-script-reference/v5/#fun_input{dot}source)[input.time](https://www.tradingview.com/pine-script-reference/v5/#fun_input{dot}time)[input](https://www.tradingview.com/pine-script-reference/v5/#fun_input)

#### input.float

Adds an input to the Inputs tab of your script's Settings, which allows you to provide configuration options to script users. This function adds a field for a float input to the script's inputs.

input.float(defval, title, minval, maxval, step, tooltip, inline, group, confirm) → input float

input.float(defval, title, options, tooltip, inline, group, confirm) → input float

#### Example

```js
//@version=5
indicator("input.float", overlay=true)
i_angle1 = input.float(0.5, "Sin Angle", minval=-3.14, maxval=3.14, step=0.02)
plot(math.sin(i_angle1) > 0 ? close : open, "sin", color=color.green)

i_angle2 = input.float(0, "Cos Angle", options=[-3.14, -1.57, 0, 1.57, 3.14])
plot(math.cos(i_angle2) > 0 ? close : open, "cos", color=color.red)
```

###### Returns

Value of input variable.

##### Arguments

defval (const int/float) Determines the default value of the input variable proposed in the script's "Settings/Inputs" tab, from where script users can change it. When a list of values is used with the `options` parameter, the value must be one of them.

title (const string) Title of the input. If not specified, the variable name is used as the input's title. If the title is specified, but it is empty, the name will be an empty string.

minval (const int/float) Minimal possible value of the input variable. Optional.

maxval (const int/float) Maximum possible value of the input variable. Optional.

step (const int/float) Step value used for incrementing/decrementing the input. Optional. The default is 1.

options (tuple of const int/float values: [val1, val2, ...]) A list of options to choose from a dropdown menu, separated by commas and enclosed in square brackets: [val1, val2, ...]. When using this parameter, the `minval`, `maxval` and `step` parameters cannot be used.

tooltip (const string) The string that will be shown to the user when hovering over the tooltip icon.

inline (const string) Combines all the input calls using the same argument in one line. The string used as an argument is not displayed. It is only used to identify inputs belonging to the same line.

group (const string) Creates a header above all inputs using the same group argument string. The string is also used as the header's text.

confirm (const bool) If true, then user will be asked to confirm input value before indicator is added to chart. Default value is false.

##### Remarks

Result of [input.float](https://www.tradingview.com/pine-script-reference/v5/#fun_input{dot}float) function always should be assigned to a variable, see examples above.

##### See also

[input.bool](https://www.tradingview.com/pine-script-reference/v5/#fun_input{dot}bool)[input.int](https://www.tradingview.com/pine-script-reference/v5/#fun_input{dot}int)[input.string](https://www.tradingview.com/pine-script-reference/v5/#fun_input{dot}string)[input.text_area](https://www.tradingview.com/pine-script-reference/v5/#fun_input{dot}text_area)[input.symbol](https://www.tradingview.com/pine-script-reference/v5/#fun_input{dot}symbol)[input.timeframe](https://www.tradingview.com/pine-script-reference/v5/#fun_input{dot}timeframe)[input.session](https://www.tradingview.com/pine-script-reference/v5/#fun_input{dot}session)[input.source](https://www.tradingview.com/pine-script-reference/v5/#fun_input{dot}source)[input.color](https://www.tradingview.com/pine-script-reference/v5/#fun_input{dot}color)[input.time](https://www.tradingview.com/pine-script-reference/v5/#fun_input{dot}time)[input](https://www.tradingview.com/pine-script-reference/v5/#fun_input)

#### input.int

Adds an input to the Inputs tab of your script's Settings, which allows you to provide configuration options to script users. This function adds a field for an integer input to the script's inputs.

input.int(defval, title, minval, maxval, step, tooltip, inline, group, confirm) → input int

input.int(defval, title, options, tooltip, inline, group, confirm) → input int

#### Example

```js
//@version=5
indicator("input.int", overlay=true)
i_len1 = input.int(10, "Length 1", minval=5, maxval=21, step=1)
plot(ta.sma(close, i_len1))

i_len2 = input.int(10, "Length 2", options=[5, 10, 21])
plot(ta.sma(close, i_len2))
```

###### Returns

Value of input variable.

##### Arguments

defval (const int) Determines the default value of the input variable proposed in the script's "Settings/Inputs" tab, from where script users can change it. When a list of values is used with the `options` parameter, the value must be one of them.

title (const string) Title of the input. If not specified, the variable name is used as the input's title. If the title is specified, but it is empty, the name will be an empty string.

minval (const int) Minimal possible value of the input variable. Optional.

maxval (const int) Maximum possible value of the input variable. Optional.

step (const int) Step value used for incrementing/decrementing the input. Optional. The default is 1.

options (tuple of const int values: [val1, val2, ...]) A list of options to choose from a dropdown menu, separated by commas and enclosed in square brackets: [val1, val2, ...]. When using this parameter, the `minval`, `maxval` and `step` parameters cannot be used.

tooltip (const string) The string that will be shown to the user when hovering over the tooltip icon.

inline (const string) Combines all the input calls using the same argument in one line. The string used as an argument is not displayed. It is only used to identify inputs belonging to the same line.

group (const string) Creates a header above all inputs using the same group argument string. The string is also used as the header's text.

confirm (const bool) If true, then user will be asked to confirm input value before indicator is added to chart. Default value is false.

##### Remarks

Result of [input.int](https://www.tradingview.com/pine-script-reference/v5/#fun_input{dot}int) function always should be assigned to a variable, see examples above.

#### See also

[input.bool](https://www.tradingview.com/pine-script-reference/v5/#fun_input{dot}bool)[input.float](https://www.tradingview.com/pine-script-reference/v5/#fun_input{dot}float)[input.string](https://www.tradingview.com/pine-script-reference/v5/#fun_input{dot}string)[input.text_area](https://www.tradingview.com/pine-script-reference/v5/#fun_input{dot}text_area)[input.symbol](https://www.tradingview.com/pine-script-reference/v5/#fun_input{dot}symbol)[input.timeframe](https://www.tradingview.com/pine-script-reference/v5/#fun_input{dot}timeframe)[input.session](https://www.tradingview.com/pine-script-reference/v5/#fun_input{dot}session)[input.source](https://www.tradingview.com/pine-script-reference/v5/#fun_input{dot}source)[input.color](https://www.tradingview.com/pine-script-reference/v5/#fun_input{dot}color)[input.time](https://www.tradingview.com/pine-script-reference/v5/#fun_input{dot}time)[input](https://www.tradingview.com/pine-script-reference/v5/#fun_input)

#### input.price

Adds a price input to the script's "Settings/Inputs" tab. Using `confirm = true` activates the interactive input mode where a price is selected by clicking on the chart.

input.price(defval, title, tooltip, inline, group, confirm) → input float

Example

```js
//@version=5
indicator("input.price", overlay=true)
price1 = input.price(title="Date", defval=42)
plot(price1)

price2 = input.price(54, title="Date")
plot(price2)
```

Returns

Value of input variable.

Arguments

defval (const int/float) Determines the default value of the input variable proposed in the script's "Settings/Inputs" tab, from where the user can change it.

title (const string) Title of the input. If not specified, the variable name is used as the input's title. If the title is specified, but it is empty, the name will be an empty string.

tooltip (const string) The string that will be shown to the user when hovering over the tooltip icon.

inline (const string) Combines all the input calls using the same argument in one line. The string used as an argument is not displayed. It is only used to identify inputs belonging to the same line.

group (const string) Creates a header above all inputs using the same group argument string. The string is also used as the header's text.

confirm (const bool) If true, the interactive input mode is enabled and the selection is done by clicking on the chart when the indicator is added to the chart, or by selecting the indicator and moving the selection after that. Optional. The default is false.

Remarks

When using interactive mode, a time input can be combined with a price input if both function calls use the same argument for their `inline` parameter.

See also

[input.bool](https://www.tradingview.com/pine-script-reference/v5/#fun_input{dot}bool)[input.int](https://www.tradingview.com/pine-script-reference/v5/#fun_input{dot}int)[input.float](https://www.tradingview.com/pine-script-reference/v5/#fun_input{dot}float)[input.string](https://www.tradingview.com/pine-script-reference/v5/#fun_input{dot}string)[input.text_area](https://www.tradingview.com/pine-script-reference/v5/#fun_input{dot}text_area)[input.symbol](https://www.tradingview.com/pine-script-reference/v5/#fun_input{dot}symbol)[input.resolution](https://www.tradingview.com/pine-script-reference/v5/#fun_input{dot}resolution)[input.session](https://www.tradingview.com/pine-script-reference/v5/#fun_input{dot}session)[input.source](https://www.tradingview.com/pine-script-reference/v5/#fun_input{dot}source)[input.color](https://www.tradingview.com/pine-script-reference/v5/#fun_input{dot}color)[input](https://www.tradingview.com/pine-script-reference/v5/#fun_input)

#### input.session

Adds an input to the Inputs tab of your script's Settings, which allows you to provide configuration options to script users. This function adds two dropdowns that allow the user to specify the beginning and the end of a session using the session selector and returns the result as a string.

input.session(defval, title, options, tooltip, inline, group, confirm) → input string

Example

```js
//@version=5
indicator("input.session", overlay=true)
i_sess = input.session("1300-1700", "Session", options=["0930-1600", "1300-1700", "1700-2100"])
t = time(timeframe.period, i_sess)
bgcolor(time == t ? color.green : na)
```

Returns

Value of input variable.

Arguments

defval (const string) Determines the default value of the input variable proposed in the script's "Settings/Inputs" tab, from where the user can change it. When a list of values is used with the `options` parameter, the value must be one of them.

title (const string) Title of the input. If not specified, the variable name is used as the input's title. If the title is specified, but it is empty, the name will be an empty string.

options (tuple of const string values: [val1, val2, ...]) A list of options to choose from.

tooltip (const string) The string that will be shown to the user when hovering over the tooltip icon.

inline (const string) Combines all the input calls using the same argument in one line. The string used as an argument is not displayed. It is only used to identify inputs belonging to the same line.

group (const string) Creates a header above all inputs using the same group argument string. The string is also used as the header's text.

confirm (const bool) If true, then user will be asked to confirm input value before indicator is added to chart. Default value is false.

Remarks

Result of [input.session](https://www.tradingview.com/pine-script-reference/v5/#fun_input{dot}session) function always should be assigned to a variable, see examples above.

See also

[input.bool](https://www.tradingview.com/pine-script-reference/v5/#fun_input{dot}bool)[input.int](https://www.tradingview.com/pine-script-reference/v5/#fun_input{dot}int)[input.float](https://www.tradingview.com/pine-script-reference/v5/#fun_input{dot}float)[input.string](https://www.tradingview.com/pine-script-reference/v5/#fun_input{dot}string)[input.text_area](https://www.tradingview.com/pine-script-reference/v5/#fun_input{dot}text_area)[input.symbol](https://www.tradingview.com/pine-script-reference/v5/#fun_input{dot}symbol)[input.timeframe](https://www.tradingview.com/pine-script-reference/v5/#fun_input{dot}timeframe)[input.source](https://www.tradingview.com/pine-script-reference/v5/#fun_input{dot}source)[input.color](https://www.tradingview.com/pine-script-reference/v5/#fun_input{dot}color)[input.time](https://www.tradingview.com/pine-script-reference/v5/#fun_input{dot}time)[input](https://www.tradingview.com/pine-script-reference/v5/#fun_input)

#### input.source

Adds an input to the Inputs tab of your script's Settings, which allows you to provide configuration options to script users. This function adds a dropdown that allows the user to select a source for the calculation, e.g. [close](https://www.tradingview.com/pine-script-reference/v5/#var_close), [hl2](https://www.tradingview.com/pine-script-reference/v5/#var_hl2), etc. If the script includes only one input.source() call, the user can also select an output from another indicator on their chart as the source.

input.source(defval, title, tooltip, inline, group) → series float

Example

```js
//@version=5
indicator("input.source", overlay=true)
i_src = input.source(close, "Source")
plot(i_src)
```

Returns

Value of input variable.

Arguments

defval (series int/float) Determines the default value of the input variable proposed in the script's "Settings/Inputs" tab, from where the user can change it.

title (const string) Title of the input. If not specified, the variable name is used as the input's title. If the title is specified, but it is empty, the name will be an empty string.

tooltip (const string) The string that will be shown to the user when hovering over the tooltip icon.

inline (const string) Combines all the input calls using the same argument in one line. The string used as an argument is not displayed. It is only used to identify inputs belonging to the same line.

group (const string) Creates a header above all inputs using the same group argument string. The string is also used as the header's text.

Remarks

Result of [input.source](https://www.tradingview.com/pine-script-reference/v5/#fun_input{dot}source) function always should be assigned to a variable, see examples above.

See also

[input.bool](https://www.tradingview.com/pine-script-reference/v5/#fun_input{dot}bool)[input.int](https://www.tradingview.com/pine-script-reference/v5/#fun_input{dot}int)[input.float](https://www.tradingview.com/pine-script-reference/v5/#fun_input{dot}float)[input.string](https://www.tradingview.com/pine-script-reference/v5/#fun_input{dot}string)[input.text_area](https://www.tradingview.com/pine-script-reference/v5/#fun_input{dot}text_area)[input.symbol](https://www.tradingview.com/pine-script-reference/v5/#fun_input{dot}symbol)[input.timeframe](https://www.tradingview.com/pine-script-reference/v5/#fun_input{dot}timeframe)[input.session](https://www.tradingview.com/pine-script-reference/v5/#fun_input{dot}session)[input.color](https://www.tradingview.com/pine-script-reference/v5/#fun_input{dot}color)[input.time](https://www.tradingview.com/pine-script-reference/v5/#fun_input{dot}time)[input](https://www.tradingview.com/pine-script-reference/v5/#fun_input)

#### input.string

Adds an input to the Inputs tab of your script's Settings, which allows you to provide configuration options to script users. This function adds a field for a string input to the script's inputs.

input.string(defval, title, options, tooltip, inline, group, confirm) → input string

Example

```js
//@version=5
indicator("input.string", overlay=true)
i_text = input.string("Hello!", "Message")
l = label.new(bar_index, high, i_text)
label.delete(l[1])
```

Returns

Value of input variable.

Arguments

defval (const string) Determines the default value of the input variable proposed in the script's "Settings/Inputs" tab, from where the user can change it. When a list of values is used with the `options` parameter, the value must be one of them.

title (const string) Title of the input. If not specified, the variable name is used as the input's title. If the title is specified, but it is empty, the name will be an empty string.

options (List of constants: [&lt;type&gt;...]) A list of options to choose from.

tooltip (const string) The string that will be shown to the user when hovering over the tooltip icon.

inline (const string) Combines all the input calls using the same argument in one line. The string used as an argument is not displayed. It is only used to identify inputs belonging to the same line.

group (const string) Creates a header above all inputs using the same group argument string. The string is also used as the header's text.

confirm (const bool) If true, then user will be asked to confirm input value before indicator is added to chart. Default value is false.

Remarks

Result of [input.string](https://www.tradingview.com/pine-script-reference/v5/#fun_input{dot}string) function always should be assigned to a variable, see examples above.

See also

[input.text_area](https://www.tradingview.com/pine-script-reference/v5/#fun_input{dot}text_area)[input.bool](https://www.tradingview.com/pine-script-reference/v5/#fun_input{dot}bool)[input.int](https://www.tradingview.com/pine-script-reference/v5/#fun_input{dot}int)[input.float](https://www.tradingview.com/pine-script-reference/v5/#fun_input{dot}float)[input.symbol](https://www.tradingview.com/pine-script-reference/v5/#fun_input{dot}symbol)[input.timeframe](https://www.tradingview.com/pine-script-reference/v5/#fun_input{dot}timeframe)[input.session](https://www.tradingview.com/pine-script-reference/v5/#fun_input{dot}session)[input.source](https://www.tradingview.com/pine-script-reference/v5/#fun_input{dot}source)[input.color](https://www.tradingview.com/pine-script-reference/v5/#fun_input{dot}color)[input.time](https://www.tradingview.com/pine-script-reference/v5/#fun_input{dot}time)[input](https://www.tradingview.com/pine-script-reference/v5/#fun_input)

#### input.symbol

Adds an input to the Inputs tab of your script's Settings, which allows you to provide configuration options to script users. This function adds a field that allows the user to select a specific symbol using the symbol search and returns that symbol, paired with its exchange prefix, as a string.

input.symbol(defval, title, tooltip, inline, group, confirm) → input string

Example

```js
//@version=5
indicator("input.symbol", overlay=true)
i_sym = input.symbol("DELL", "Symbol")
s = request.security(i_sym, 'D', close)
plot(s)
```

Returns

Value of input variable.

Arguments

defval (const string) Determines the default value of the input variable proposed in the script's "Settings/Inputs" tab, from where the user can change it.

title (const string) Title of the input. If not specified, the variable name is used as the input's title. If the title is specified, but it is empty, the name will be an empty string.

tooltip (const string) The string that will be shown to the user when hovering over the tooltip icon.

inline (const string) Combines all the input calls using the same argument in one line. The string used as an argument is not displayed. It is only used to identify inputs belonging to the same line.

group (const string) Creates a header above all inputs using the same group argument string. The string is also used as the header's text.

confirm (const bool) If true, then user will be asked to confirm input value before indicator is added to chart. Default value is false.

Remarks

Result of [input.symbol](https://www.tradingview.com/pine-script-reference/v5/#fun_input{dot}symbol) function always should be assigned to a variable, see examples above.

See also

[input.bool](https://www.tradingview.com/pine-script-reference/v5/#fun_input{dot}bool)[input.int](https://www.tradingview.com/pine-script-reference/v5/#fun_input{dot}int)[input.float](https://www.tradingview.com/pine-script-reference/v5/#fun_input{dot}float)[input.string](https://www.tradingview.com/pine-script-reference/v5/#fun_input{dot}string)[input.text_area](https://www.tradingview.com/pine-script-reference/v5/#fun_input{dot}text_area)[input.timeframe](https://www.tradingview.com/pine-script-reference/v5/#fun_input{dot}timeframe)[input.session](https://www.tradingview.com/pine-script-reference/v5/#fun_input{dot}session)[input.source](https://www.tradingview.com/pine-script-reference/v5/#fun_input{dot}source)[input.color](https://www.tradingview.com/pine-script-reference/v5/#fun_input{dot}color)[input.time](https://www.tradingview.com/pine-script-reference/v5/#fun_input{dot}time)[input](https://www.tradingview.com/pine-script-reference/v5/#fun_input)

#### input.text_area

Adds an input to the Inputs tab of your script's Settings, which allows you to provide configuration options to script users. This function adds a field for a multiline text input.

input.text_area(defval, title, tooltip, group, confirm) → input string

Example

```js
//@version=5
indicator("input.text_area")
i_text = input.text_area(defval = "Hello \nWorld!", title = "Message")
plot(close)
```

Returns

Value of input variable.

Arguments

defval (const string) Determines the default value of the input variable proposed in the script's "Settings/Inputs" tab, from where the user can change it.

title (const string) Title of the input. If not specified, the variable name is used as the input's title. If the title is specified, but it is empty, the name will be an empty string.

tooltip (const string) The string that will be shown to the user when hovering over the tooltip icon.

group (const string) Creates a header above all inputs using the same group argument string. The string is also used as the header's text.

confirm (const bool) If true, then user will be asked to confirm input value before indicator is added to chart. Default value is false.

Remarks

Result of [input.text_area](https://www.tradingview.com/pine-script-reference/v5/#fun_input{dot}text_area) function always should be assigned to a variable, see examples above.

See also

[input.string](https://www.tradingview.com/pine-script-reference/v5/#fun_input{dot}string)[input.bool](https://www.tradingview.com/pine-script-reference/v5/#fun_input{dot}bool)[input.int](https://www.tradingview.com/pine-script-reference/v5/#fun_input{dot}int)[input.float](https://www.tradingview.com/pine-script-reference/v5/#fun_input{dot}float)[input.symbol](https://www.tradingview.com/pine-script-reference/v5/#fun_input{dot}symbol)[input.timeframe](https://www.tradingview.com/pine-script-reference/v5/#fun_input{dot}timeframe)[input.session](https://www.tradingview.com/pine-script-reference/v5/#fun_input{dot}session)[input.source](https://www.tradingview.com/pine-script-reference/v5/#fun_input{dot}source)[input.color](https://www.tradingview.com/pine-script-reference/v5/#fun_input{dot}color)[input.time](https://www.tradingview.com/pine-script-reference/v5/#fun_input{dot}time)[input](https://www.tradingview.com/pine-script-reference/v5/#fun_input)

#### input.time

Adds a time input to the script's "Settings/Inputs" tab. This function adds two input widgets on the same line: one for the date and one for the time. The function returns a date/time value in UNIX format. Using `confirm = true` activates the interactive input mode where a point in time is selected by clicking on the chart.

input.time(defval, title, tooltip, inline, group, confirm) → input int

Example

```js
//@version=5
indicator("input.time", overlay=true)
i_date = input.time(timestamp("20 Jul 2021 00:00 +0300"), "Date")
l = label.new(i_date, high, "Date", xloc=xloc.bar_time)
label.delete(l[1])
```

Returns

Value of input variable.

Arguments

defval (const int) Determines the default value of the input variable proposed in the script's "Settings/Inputs" tab, from where the user can change it. The value can be a [timestamp](https://www.tradingview.com/pine-script-reference/v5/#fun_timestamp) function, but only if it uses a date argument in const string format.

title (const string) Title of the input. If not specified, the variable name is used as the input's title. If the title is specified, but it is empty, the name will be an empty string.

tooltip (const string) The string that will be shown to the user when hovering over the tooltip icon.

inline (const string) Combines all the input calls using the same argument in one line. The string used as an argument is not displayed. It is only used to identify inputs belonging to the same line.

group (const string) Creates a header above all inputs using the same group argument string. The string is also used as the header's text.

confirm (const bool) If true, the interactive input mode is enabled and the selection is done by clicking on the chart when the indicator is added to the chart, or by selecting the indicator and moving the selection after that. Optional. The default is false.

Remarks

When using interactive mode, a price input can be combined with a time input if both function calls use the same argument for their `inline` parameter.

See also

[input.bool](https://www.tradingview.com/pine-script-reference/v5/#fun_input{dot}bool)[input.int](https://www.tradingview.com/pine-script-reference/v5/#fun_input{dot}int)[input.float](https://www.tradingview.com/pine-script-reference/v5/#fun_input{dot}float)[input.string](https://www.tradingview.com/pine-script-reference/v5/#fun_input{dot}string)[input.text_area](https://www.tradingview.com/pine-script-reference/v5/#fun_input{dot}text_area)[input.symbol](https://www.tradingview.com/pine-script-reference/v5/#fun_input{dot}symbol)[input.timeframe](https://www.tradingview.com/pine-script-reference/v5/#fun_input{dot}timeframe)[input.session](https://www.tradingview.com/pine-script-reference/v5/#fun_input{dot}session)[input.source](https://www.tradingview.com/pine-script-reference/v5/#fun_input{dot}source)[input.color](https://www.tradingview.com/pine-script-reference/v5/#fun_input{dot}color)[input](https://www.tradingview.com/pine-script-reference/v5/#fun_input)

#### input.timeframe

Adds an input to the Inputs tab of your script's Settings, which allows you to provide configuration options to script users. This function adds a dropdown that allows the user to select a specific timeframe via the timeframe selector and returns it as a string. The selector includes the custom timeframes a user may have added using the chart's Timeframe dropdown.

input.timeframe(defval, title, options, tooltip, inline, group, confirm) → input string

Example

```js
//@version=5
indicator("input.timeframe", overlay=true)
i_res = input.timeframe('D', "Resolution", options=['D', 'W', 'M'])
s = request.security("AAPL", i_res, close)
plot(s)
```

Returns

Value of input variable.

Arguments

defval (const string) Determines the default value of the input variable proposed in the script's "Settings/Inputs" tab, from where the user can change it. When a list of values is used with the `options` parameter, the value must be one of them.

title (const string) Title of the input. If not specified, the variable name is used as the input's title. If the title is specified, but it is empty, the name will be an empty string.

options (tuple of const string values: [val1, val2, ...]) A list of options to choose from.

tooltip (const string) The string that will be shown to the user when hovering over the tooltip icon.

inline (const string) Combines all the input calls using the same argument in one line. The string used as an argument is not displayed. It is only used to identify inputs belonging to the same line.

group (const string) Creates a header above all inputs using the same group argument string. The string is also used as the header's text.

confirm (const bool) If true, then user will be asked to confirm input value before indicator is added to chart. Default value is false.

Remarks

Result of [input.timeframe](https://www.tradingview.com/pine-script-reference/v5/#fun_input{dot}timeframe) function always should be assigned to a variable, see examples above.

See also

[input.bool](https://www.tradingview.com/pine-script-reference/v5/#fun_input{dot}bool)[input.int](https://www.tradingview.com/pine-script-reference/v5/#fun_input{dot}int)[input.float](https://www.tradingview.com/pine-script-reference/v5/#fun_input{dot}float)[input.string](https://www.tradingview.com/pine-script-reference/v5/#fun_input{dot}string)[input.text_area](https://www.tradingview.com/pine-script-reference/v5/#fun_input{dot}text_area)[input.symbol](https://www.tradingview.com/pine-script-reference/v5/#fun_input{dot}symbol)[input.session](https://www.tradingview.com/pine-script-reference/v5/#fun_input{dot}session)[input.source](https://www.tradingview.com/pine-script-reference/v5/#fun_input{dot}source)[input.color](https://www.tradingview.com/pine-script-reference/v5/#fun_input{dot}color)[input.time](https://www.tradingview.com/pine-script-reference/v5/#fun_input{dot}time)[input](https://www.tradingview.com/pine-script-reference/v5/#fun_input)

#### int

Casts na or truncates float value to int

int(x) → simple int

int(x) → input int

int(x) → const int

int(x) → series int

Returns

The value of the argument after casting to int.

See also

[float](https://www.tradingview.com/pine-script-reference/v5/#fun_float)[bool](https://www.tradingview.com/pine-script-reference/v5/#fun_bool)[color](https://www.tradingview.com/pine-script-reference/v5/#fun_color)[string](https://www.tradingview.com/pine-script-reference/v5/#fun_string)[line](https://www.tradingview.com/pine-script-reference/v5/#fun_line)[label](https://www.tradingview.com/pine-script-reference/v5/#fun_label)

### label

Casts na to label

label(x) → series label

Returns

The value of the argument after casting to label.

See also

[float](https://www.tradingview.com/pine-script-reference/v5/#fun_float)[int](https://www.tradingview.com/pine-script-reference/v5/#fun_int)[bool](https://www.tradingview.com/pine-script-reference/v5/#fun_bool)[color](https://www.tradingview.com/pine-script-reference/v5/#fun_color)[string](https://www.tradingview.com/pine-script-reference/v5/#fun_string)[line](https://www.tradingview.com/pine-script-reference/v5/#fun_line)

#### label.copy

Clones the label object.

label.copy(id) → series label

Example

```js
//@version=5
indicator('Last 100 bars highest/lowest', overlay = true)
LOOKBACK = 100
highest = ta.highest(LOOKBACK)
highestBars = ta.highestbars(LOOKBACK)
lowest = ta.lowest(LOOKBACK)
lowestBars = ta.lowestbars(LOOKBACK)
if barstate.islastconfirmedhistory
	var labelHigh = label.new(bar_index + highestBars, highest, str.tostring(highest), color = color.green)
	var labelLow = label.copy(labelHigh)
	label.set_xy(labelLow, bar_index + lowestBars, lowest)
	label.set_text(labelLow, str.tostring(lowest))
	label.set_color(labelLow, color.red)
	label.set_style(labelLow, label.style_label_up)
```

Returns

New label ID object which may be passed to label.setXXX and label.getXXX functions.

Arguments

id (series label) Label object.

See also

[label.new](https://www.tradingview.com/pine-script-reference/v5/#fun_label{dot}new)[label.delete](https://www.tradingview.com/pine-script-reference/v5/#fun_label{dot}delete)

#### label.delete

Deletes the specified label object. If it has already been deleted, does nothing.

label.delete(id) → void

Arguments

id (series label) Label object to delete.

See also

[label.new](https://www.tradingview.com/pine-script-reference/v5/#fun_label{dot}new)

#### label.get_text

Returns the text of this label object.

label.get_text(id) → series string

Example

```js
//@version=5
indicator("label.get_text")
my_label = label.new(time, open, text="Open bar text", xloc=xloc.bar_time)
a = label.get_text(my_label)
label.new(time, close, text = a + " new", xloc=xloc.bar_time)
```

Returns

String object containing the text of this label.

Arguments

id (series label) Label object.

See also

[label.new](https://www.tradingview.com/pine-script-reference/v5/#fun_label{dot}new)

#### label.get_x

Returns UNIX time or bar index (depending on the last xloc value set) of this label's position.

label.get_x(id) → series int

Example

```js
//@version=5
indicator("label.get_x")
my_label = label.new(time, open, text="Open bar text", xloc=xloc.bar_time)
a = label.get_x(my_label)
plot(time - label.get_x(my_label)) //draws zero plot
```

Returns

UNIX timestamp (in milliseconds) or bar index.

Arguments

id (series label) Label object.

See also

[label.new](https://www.tradingview.com/pine-script-reference/v5/#fun_label{dot}new)

#### label.get_y

Returns price of this label's position.

label.get_y(id) → series float

Returns

Floating point value representing price.

Arguments

id (series label) Label object.

See also

[label.new](https://www.tradingview.com/pine-script-reference/v5/#fun_label{dot}new)

#### label.new

Creates new label object.

label.new(x, y, text, xloc, yloc, color, style, textcolor, size, textalign, tooltip) → series label

Example

```js
//@version=5
indicator("label.new")
var label1 = label.new(bar_index, low, text="Hello, world!", style=label.style_circle)
label.set_x(label1, 0)
label.set_xloc(label1, time, xloc.bar_time)
label.set_color(label1, color.red)
label.set_size(label1, size.large)
```

Returns

Label ID object which may be passed to label.setXXX and label.getXXX functions.

Arguments

x (series int) Bar index (if xloc = [xloc.bar_index](https://www.tradingview.com/pine-script-reference/v5/#var_xloc{dot}bar_index)) or bar UNIX time (if xloc = [xloc.bar_time](https://www.tradingview.com/pine-script-reference/v5/#var_xloc{dot}bar_time)) of the label position. Note that objects positioned using [xloc.bar_index](https://www.tradingview.com/pine-script-reference/v5/#var_xloc{dot}bar_index) cannot be drawn further than 500 bars into the future.

y (series int/float) Price of the label position. It is taken into account only if yloc=[yloc.price](https://www.tradingview.com/pine-script-reference/v5/#var_yloc{dot}price).

text (series string) Label text. Default is empty string.

xloc (series string) See description of **x** argument. Possible values: [xloc.bar_index](https://www.tradingview.com/pine-script-reference/v5/#var_xloc{dot}bar_index) and [xloc.bar_time](https://www.tradingview.com/pine-script-reference/v5/#var_xloc{dot}bar_time). Default is [xloc.bar_index](https://www.tradingview.com/pine-script-reference/v5/#var_xloc{dot}bar_index).

yloc (series string) Possible values are [yloc.price](https://www.tradingview.com/pine-script-reference/v5/#var_yloc{dot}price), [yloc.abovebar](https://www.tradingview.com/pine-script-reference/v5/#var_yloc{dot}abovebar), [yloc.belowbar](https://www.tradingview.com/pine-script-reference/v5/#var_yloc{dot}belowbar). If yloc=[yloc.price](https://www.tradingview.com/pine-script-reference/v5/#var_yloc{dot}price), **y** argument specifies the price of the label position. If yloc=[yloc.abovebar](https://www.tradingview.com/pine-script-reference/v5/#var_yloc{dot}abovebar), label is located above bar. If yloc=[yloc.belowbar](https://www.tradingview.com/pine-script-reference/v5/#var_yloc{dot}belowbar), label is located below bar. Default is [yloc.price](https://www.tradingview.com/pine-script-reference/v5/#var_yloc{dot}price).

color (series color) Color of the label border and arrow

style (series string) Label style. Possible values: [label.style_none](https://www.tradingview.com/pine-script-reference/v5/#var_label{dot}style_none), [label.style_xcross](https://www.tradingview.com/pine-script-reference/v5/#var_label{dot}style_xcross), [label.style_cross](https://www.tradingview.com/pine-script-reference/v5/#var_label{dot}style_cross), [label.style_triangleup](https://www.tradingview.com/pine-script-reference/v5/#var_label{dot}style_triangleup), [label.style_triangledown](https://www.tradingview.com/pine-script-reference/v5/#var_label{dot}style_triangledown), [label.style_flag](https://www.tradingview.com/pine-script-reference/v5/#var_label{dot}style_flag), [label.style_circle](https://www.tradingview.com/pine-script-reference/v5/#var_label{dot}style_circle), [label.style_arrowup](https://www.tradingview.com/pine-script-reference/v5/#var_label{dot}style_arrowup), [label.style_arrowdown](https://www.tradingview.com/pine-script-reference/v5/#var_label{dot}style_arrowdown), [label.style_label_up](https://www.tradingview.com/pine-script-reference/v5/#var_label{dot}style_label_up), [label.style_label_down](https://www.tradingview.com/pine-script-reference/v5/#var_label{dot}style_label_down), [label.style_label_left](https://www.tradingview.com/pine-script-reference/v5/#var_label{dot}style_label_left), [label.style_label_right](https://www.tradingview.com/pine-script-reference/v5/#var_label{dot}style_label_right), [label.style_label_lower_left](https://www.tradingview.com/pine-script-reference/v5/#var_label{dot}style_label_lower_left), [label.style_label_lower_right](https://www.tradingview.com/pine-script-reference/v5/#var_label{dot}style_label_lower_right), [label.style_label_upper_left](https://www.tradingview.com/pine-script-reference/v5/#var_label{dot}style_label_upper_left), [label.style_label_upper_right](https://www.tradingview.com/pine-script-reference/v5/#var_label{dot}style_label_upper_right), [label.style_label_center](https://www.tradingview.com/pine-script-reference/v5/#var_label{dot}style_label_center), [label.style_square](https://www.tradingview.com/pine-script-reference/v5/#var_label{dot}style_square), [label.style_diamond](https://www.tradingview.com/pine-script-reference/v5/#var_label{dot}style_diamond). Default is [label.style_label_down](https://www.tradingview.com/pine-script-reference/v5/#var_label{dot}style_label_down).

textcolor (series color) Text color.

size (series string) Label size. Possible values: [size.auto](https://www.tradingview.com/pine-script-reference/v5/#var_size{dot}auto), [size.tiny](https://www.tradingview.com/pine-script-reference/v5/#var_size{dot}tiny), [size.small](https://www.tradingview.com/pine-script-reference/v5/#var_size{dot}small), [size.normal](https://www.tradingview.com/pine-script-reference/v5/#var_size{dot}normal), [size.large](https://www.tradingview.com/pine-script-reference/v5/#var_size{dot}large), [size.huge](https://www.tradingview.com/pine-script-reference/v5/#var_size{dot}huge). Default value is [size.normal](https://www.tradingview.com/pine-script-reference/v5/#var_size{dot}normal).

textalign (series string) Label text alignment. Possible values: [text.align_left](https://www.tradingview.com/pine-script-reference/v5/#var_text{dot}align_left), [text.align_center](https://www.tradingview.com/pine-script-reference/v5/#var_text{dot}align_center), [text.align_right](https://www.tradingview.com/pine-script-reference/v5/#var_text{dot}align_right). Default value is [text.align_center](https://www.tradingview.com/pine-script-reference/v5/#var_text{dot}align_center).

tooltip (series string) Hover to see tooltip label.

See also

[label.delete](https://www.tradingview.com/pine-script-reference/v5/#fun_label{dot}delete)[label.set_x](https://www.tradingview.com/pine-script-reference/v5/#fun_label{dot}set_x)[label.set_y](https://www.tradingview.com/pine-script-reference/v5/#fun_label{dot}set_y)[label.set_xy](https://www.tradingview.com/pine-script-reference/v5/#fun_label{dot}set_xy)[label.set_xloc](https://www.tradingview.com/pine-script-reference/v5/#fun_label{dot}set_xloc)[label.set_yloc](https://www.tradingview.com/pine-script-reference/v5/#fun_label{dot}set_yloc)[label.set_color](https://www.tradingview.com/pine-script-reference/v5/#fun_label{dot}set_color)[label.set_textcolor](https://www.tradingview.com/pine-script-reference/v5/#fun_label{dot}set_textcolor)[label.set_style](https://www.tradingview.com/pine-script-reference/v5/#fun_label{dot}set_style)[label.set_size](https://www.tradingview.com/pine-script-reference/v5/#fun_label{dot}set_size)[label.set_textalign](https://www.tradingview.com/pine-script-reference/v5/#fun_label{dot}set_textalign)[label.set_tooltip](https://www.tradingview.com/pine-script-reference/v5/#fun_label{dot}set_tooltip)

#### label.set_color

Sets label border and arrow color.

label.set_color(id, color) → void

Arguments

id (series label) Label object.

color (series color) New label border and arrow color.

See also

[label.new](https://www.tradingview.com/pine-script-reference/v5/#fun_label{dot}new)

#### label.set_size

Sets arrow and text size of the specified label object.

label.set_size(id, size) → void

Arguments

id (series label) Label object.

size (series string) Possible values: [size.auto](https://www.tradingview.com/pine-script-reference/v5/#var_size{dot}auto), [size.tiny](https://www.tradingview.com/pine-script-reference/v5/#var_size{dot}tiny), [size.small](https://www.tradingview.com/pine-script-reference/v5/#var_size{dot}small), [size.normal](https://www.tradingview.com/pine-script-reference/v5/#var_size{dot}normal), [size.large](https://www.tradingview.com/pine-script-reference/v5/#var_size{dot}large), [size.huge](https://www.tradingview.com/pine-script-reference/v5/#var_size{dot}huge). Default value is [size.auto](https://www.tradingview.com/pine-script-reference/v5/#var_size{dot}auto).

See also

[size.auto](https://www.tradingview.com/pine-script-reference/v5/#var_size{dot}auto)[size.tiny](https://www.tradingview.com/pine-script-reference/v5/#var_size{dot}tiny)[size.small](https://www.tradingview.com/pine-script-reference/v5/#var_size{dot}small)[size.normal](https://www.tradingview.com/pine-script-reference/v5/#var_size{dot}normal)[size.large](https://www.tradingview.com/pine-script-reference/v5/#var_size{dot}large)[size.huge](https://www.tradingview.com/pine-script-reference/v5/#var_size{dot}huge)[label.new](https://www.tradingview.com/pine-script-reference/v5/#fun_label{dot}new)

#### label.set_style

Sets label style.

label.set_style(id, style) → void

Arguments

id (series label) Label object.

style (series string) New label style. Possible values: [label.style_none](https://www.tradingview.com/pine-script-reference/v5/#var_label{dot}style_none), [label.style_xcross](https://www.tradingview.com/pine-script-reference/v5/#var_label{dot}style_xcross), [label.style_cross](https://www.tradingview.com/pine-script-reference/v5/#var_label{dot}style_cross), [label.style_triangleup](https://www.tradingview.com/pine-script-reference/v5/#var_label{dot}style_triangleup), [label.style_triangledown](https://www.tradingview.com/pine-script-reference/v5/#var_label{dot}style_triangledown), [label.style_flag](https://www.tradingview.com/pine-script-reference/v5/#var_label{dot}style_flag), [label.style_circle](https://www.tradingview.com/pine-script-reference/v5/#var_label{dot}style_circle), [label.style_arrowup](https://www.tradingview.com/pine-script-reference/v5/#var_label{dot}style_arrowup), [label.style_arrowdown](https://www.tradingview.com/pine-script-reference/v5/#var_label{dot}style_arrowdown), [label.style_label_up](https://www.tradingview.com/pine-script-reference/v5/#var_label{dot}style_label_up), [label.style_label_down](https://www.tradingview.com/pine-script-reference/v5/#var_label{dot}style_label_down), [label.style_label_left](https://www.tradingview.com/pine-script-reference/v5/#var_label{dot}style_label_left), [label.style_label_right](https://www.tradingview.com/pine-script-reference/v5/#var_label{dot}style_label_right), [label.style_label_lower_left](https://www.tradingview.com/pine-script-reference/v5/#var_label{dot}style_label_lower_left), [label.style_label_lower_right](https://www.tradingview.com/pine-script-reference/v5/#var_label{dot}style_label_lower_right), [label.style_label_upper_left](https://www.tradingview.com/pine-script-reference/v5/#var_label{dot}style_label_upper_left), [label.style_label_upper_right](https://www.tradingview.com/pine-script-reference/v5/#var_label{dot}style_label_upper_right), [label.style_label_center](https://www.tradingview.com/pine-script-reference/v5/#var_label{dot}style_label_center), [label.style_square](https://www.tradingview.com/pine-script-reference/v5/#var_label{dot}style_square), [label.style_diamond](https://www.tradingview.com/pine-script-reference/v5/#var_label{dot}style_diamond).

See also

[label.new](https://www.tradingview.com/pine-script-reference/v5/#fun_label{dot}new)

#### label.set_text

Sets label text

label.set_text(id, text) → void

Arguments

id (series label) Label object.

text (series string) New label text.

See also

[label.new](https://www.tradingview.com/pine-script-reference/v5/#fun_label{dot}new)

#### label.set_textalign

Sets the alignment for the label text.

label.set_textalign(id, textalign) → void

Arguments

id (series label) Label object.

textalign (series string) Label text alignment. Possible values: [text.align_left](https://www.tradingview.com/pine-script-reference/v5/#var_text{dot}align_left), [text.align_center](https://www.tradingview.com/pine-script-reference/v5/#var_text{dot}align_center), [text.align_right](https://www.tradingview.com/pine-script-reference/v5/#var_text{dot}align_right).

See also

[text.align_left](https://www.tradingview.com/pine-script-reference/v5/#var_text{dot}align_left)[text.align_center](https://www.tradingview.com/pine-script-reference/v5/#var_text{dot}align_center)[text.align_right](https://www.tradingview.com/pine-script-reference/v5/#var_text{dot}align_right)[label.new](https://www.tradingview.com/pine-script-reference/v5/#fun_label{dot}new)

#### label.set_textcolor

Sets color of the label text.

label.set_textcolor(id, textcolor) → void

Arguments

id (series label) Label object.

textcolor (series color) New text color.

See also

[label.new](https://www.tradingview.com/pine-script-reference/v5/#fun_label{dot}new)

#### label.set_tooltip

Sets the tooltip text.

label.set_tooltip(id, tooltip) → void

Arguments

id (series label) Label object.

tooltip (series string) Tooltip text.

See also

[label.new](https://www.tradingview.com/pine-script-reference/v5/#fun_label{dot}new)

#### label.set_x

Sets bar index or bar time (depending on the xloc) of the label position.

label.set_x(id, x) → void

Arguments

id (series label) Label object.

x (series int) New bar index or bar time of the label position. Note that objects positioned using [xloc.bar_index](https://www.tradingview.com/pine-script-reference/v5/#var_xloc{dot}bar_index) cannot be drawn further than 500 bars into the future.

See also

[label.new](https://www.tradingview.com/pine-script-reference/v5/#fun_label{dot}new)

#### label.set_xloc

Sets x-location and new bar index/time value.

label.set_xloc(id, x, xloc) → void

Arguments

id (series label) Label object.

x (series int) New bar index or bar time of the label position.

xloc (series string) New x-location value.

See also

[xloc.bar_index](https://www.tradingview.com/pine-script-reference/v5/#var_xloc{dot}bar_index)[xloc.bar_time](https://www.tradingview.com/pine-script-reference/v5/#var_xloc{dot}bar_time)[label.new](https://www.tradingview.com/pine-script-reference/v5/#fun_label{dot}new)

#### label.set_xy

Sets bar index/time and price of the label position.

label.set_xy(id, x, y) → void

Arguments

id (series label) Label object.

x (series int) New bar index or bar time of the label position. Note that objects positioned using [xloc.bar_index](https://www.tradingview.com/pine-script-reference/v5/#var_xloc{dot}bar_index) cannot be drawn further than 500 bars into the future.

y (series int/float) New price of the label position.

See also

[label.new](https://www.tradingview.com/pine-script-reference/v5/#fun_label{dot}new)

#### label.set_y

Sets price of the label position

label.set_y(id, y) → void

Arguments

id (series label) Label object.

y (series int/float) New price of the label position.

See also

[label.new](https://www.tradingview.com/pine-script-reference/v5/#fun_label{dot}new)

#### label.set_yloc

Sets new y-location calculation algorithm.

label.set_yloc(id, yloc) → void

Arguments

id (series label) Label object.

yloc (series string) New y-location value.

See also

[yloc.price](https://www.tradingview.com/pine-script-reference/v5/#var_yloc{dot}price)[yloc.abovebar](https://www.tradingview.com/pine-script-reference/v5/#var_yloc{dot}abovebar)[yloc.belowbar](https://www.tradingview.com/pine-script-reference/v5/#var_yloc{dot}belowbar)[label.new](https://www.tradingview.com/pine-script-reference/v5/#fun_label{dot}new)