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
//@version=5
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
