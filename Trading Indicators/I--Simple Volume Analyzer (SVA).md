# SVA - Simple Volume Analyzer, by BlueJayBird 

[bjb]

[BlueJayBird](https://www.tradingview.com/u/BlueJayBird/)[PRO](https://www.tradingview.com/gopro/?source=badge&feature=pro)Jul 24, 2021

Bitcoin / TetherUS

1h

BINANCE

TradingView

+151.00 (+0.45%)

SVA

[Volume](https://www.tradingview.com/scripts/volumestudies/) [Volume Indicator](https://www.tradingview.com/scripts/volume/) [Volume Weighted Average Price (VWAP)](https://www.tradingview.com/scripts/vwap/) [VSA](https://www.tradingview.com/scripts/vsa/) [relativevolume](https://www.tradingview.com/scripts/relativevolume/) [colored](https://www.tradingview.com/scripts/colored/)

384

[11](https://www.tradingview.com/script/G4YdC6vT-SVA-Simple-Volume-Analyzer-by-BlueJayBird-bjb/#chart-view-comment-form "Comments")  

 ## Screenshot

![[SVA-BlueJay.PNG]]
***
The idea was initially inspired in the concepts shared by [@LazyBear](https://www.tradingview.com/u/LazyBear/) on his indicator "Better [Volume](https://www.tradingview.com/scripts/volume/) Indicator" ([https://www.tradingview.com/script/LfVJh...](https://www.tradingview.com/script/LfVJhuir-Indicators-Better-Volume-Indicator-InstrumentVolume/ "https://www.tradingview.com/script/LfVJhuir-Indicators-Better-Volume-Indicator-InstrumentVolume/")). But I found it somewhat complicated and dull. So I came up with this.  
  
## Concept:  
-   It changes the color of [volume](https://www.tradingview.com/scripts/volume/) bars based on surrounding [volume](https://www.tradingview.com/scripts/volume/) changes.  
-   [Volume](https://www.tradingview.com/scripts/volume/) changes are plotted as [volume](https://www.tradingview.com/scripts/volume/) MAs lines in the [volume](https://www.tradingview.com/scripts/volume/) pane.  
-   Whenever the [volume](https://www.tradingview.com/scripts/volume/) is higher than these MAs, the bar changes color.  
-   For this reason, the bar color change is _RELATIVE TO_ the surroundings, because the color change depends on how far the MA has been extended due to sudden (or not) changes in the [volume](https://www.tradingview.com/scripts/volume/) .  

  
## BAR COLORS:  

-   Weak Green and Red: Low [volume](https://www.tradingview.com/scripts/volume/) . The calm before or after the storm.  
-   Normal Green and Red: Mid [volume](https://www.tradingview.com/scripts/volume/) . Still low [volume](https://www.tradingview.com/scripts/volume/) , you may get bored.  
-   Yellow: High [volume](https://www.tradingview.com/scripts/volume/) . Players are playing hard and harder.  
-   White: Ultra-High [Volume](https://www.tradingview.com/scripts/volume/) . The elephants stepped in.  

  
## NOTES:  

-   [SVA](https://www.tradingview.com/symbols/NASDAQ-SVA/) works better at lower timeframes. Though as far as I can tell, it works pretty well as far as 1D timeframe.

## Code

```js
// This source code is subject to the terms of the Mozilla Public License 2.0 at https://mozilla.org/MPL/2.0/
// © BlueJayBird
//@version=4

study(title="[bjb] SVA - Simple Volume Analyzer, by @BlueJayBird", shorttitle="SVA", format = format.volume, precision = 0, scale = scale.right, overlay = false)

// ------------------------------------------- Inputs
// Main inputs
volume_enable = input(defval = true, title = "Enable Volume", type = input.bool)
volume_enable_ma = input(defval = true, title = "Enable Volume MAs (VMA)", type = input.bool)

// Signals
enable_supply_signals = input(defval = false, title = "Enable Supply Zone Signals (SZS)", type = input.bool)
enable_demand_signals = input(defval = false, title = "Enable Demand Zone Signals (DZS)", type = input.bool)

// Multipliers 
volume_res1_multiplier = input(defval = 1.1, title = "Low Volume (LV) Multiplier", type = input.float)
volume_res2_multiplier = input(defval = 1.5, title = "Medium Volume (MV) Multiplier", type = input.float)
volume_res3_multiplier = input(defval = 2.1, title = "High Volume (HV) Multiplier", type = input.float)
volume_res4_multiplier = input(defval = 7.5, title = "Ultra-High Volume (UHV) Multiplier", type = input.float)
// Smoothers
volume_smoother_a = input(defval = 20, title = "VMA Smoother A (LV, MV, HV)", type = input.integer)
volume_smoother_b = input(defval = 5, title = "VMA Smoother B (LV, MV, HV)", type = input.integer)
volume_smoother_c = input(defval = 200, title = "VMA Smoother C (UHV)", type = input.integer)
// (a) and (b) modify the behavior of the MAs, hence the modify the color of the volume bars
// I suggest you to keep the default values. I've extensively tested them.


// Miscellanea 1
volume_enable_vlr = input(defval = false, title = "Enable Volume Linebreak Resolution (VLR)", type = input.bool)
volume_resolution_vlr = input(defval = "", title = "VLR Resolution", type = input.resolution)
volume_enable_reversed = input(defval = false, title = "Switch Down Bearish Volume Bars", type = input.bool)

// Miscellanea 2
volume_resolution = ""
volume_sec = security(symbol = syminfo.tickerid, resolution = volume_resolution, expression = volume)
volume_sec_vlr = security(symbol = syminfo.tickerid, resolution = volume_resolution_vlr, expression = volume)
volume_sec_close = security(symbol = syminfo.tickerid, resolution = volume_resolution, expression = close)
volume_sec_open = security(symbol = syminfo.tickerid, resolution = volume_resolution, expression = open)
drawOnRealTime = true


// ------------------------------------------- Colors
color_upwards_price = #26a69a // Classic Green
color_downwards_price = #ef5350 // Classic Red


// ------------------------------------------- Functions
// Bar Colors
vol_color(ma, ma2, ma3, ma4) =>
    if volume_sec_close >= volume_sec_open
        // Bullish Volume
        if volume_sec >= ma4
            color.new(color.white, 0)
        else if volume_sec >= ma3
            color.new(color.yellow, 20)
        else if volume_sec >= ma2
            color.new(color_upwards_price, 10)
        else if volume_sec < ma2 and volume_sec >= ma
            color.new(color_upwards_price, 40)
        else
            vol_green = color.new(color_upwards_price, 70)
    else
        // Bearish
        if volume_sec >= ma4
            color.new(color.white, 0)
        else if volume_sec >= ma3
            color.new(color.yellow, 20)
        else if volume_sec >= ma2
            color.new(color_downwards_price, 10)
        else if volume_sec < ma2 and volume_sec >= ma
            color.new(color_downwards_price, 40)
        else
            color.new(color_downwards_price, 70)

// Text Colors
text_color(ma4) =>
    if volume_sec >= ma4
        color.new(color.black, 0)
    else
        color.new(color.white, 0)
        
// Label Colors
label_color(ma2, ma3, ma4) =>
    if volume_sec >= ma4
        color.new(color.white, 0)
    else if hl2 > hl2[1]
        color_downwards_price
    else
        color_upwards_price


// ------------------------------------------- Calculations
vol_ma_resistance_1 = ema(sma(volume_sec * volume_res1_multiplier, volume_smoother_a), volume_smoother_b)
vol_ma_resistance_2 = ema(vwma(volume_sec * volume_res2_multiplier, volume_smoother_a), volume_smoother_b)
vol_ma_resistance_3 = ema(vwma(volume_sec * volume_res3_multiplier, volume_smoother_a), volume_smoother_b)
volume_res4_multiplier := timeframe.period == "60" ? 4.1 : 7.5
vol_ma_resistance_4 = sma(volume_sec * volume_res4_multiplier, volume_smoother_c)


// ------------------------------------------- Plotting
// MA (Volume Moving Averages) → Low, Mid, High, and Ultra-High Volumen
plot(series = volume_enable_ma and volume_resolution == "" ? vol_ma_resistance_1 : na, title = "LV", color = color.new(color.yellow, 40), linewidth = 1, style = plot.style_line, editable = true)
plot(series = volume_enable_ma and volume_resolution == "" ? vol_ma_resistance_2 : na, title = "MV", color = color.new(color.orange, 30), linewidth = 1, style = plot.style_line, editable = true)
plot(series = volume_enable_ma and volume_resolution == "" ? vol_ma_resistance_3 : na, title = "HV", color = color.new(color.red, 50), linewidth = 1, style = plot.style_line, editable = true)
plot(series = volume_enable_ma and volume_resolution == "" ? vol_ma_resistance_4 : na, title = "UHV", color = color.new(color.white, 50), linewidth = 1, style = plot.style_line, editable = true, display = display.none)

// Volume Bars
volume_data = volume_enable_reversed ? volume_sec_close >= volume_sec_open ? volume_sec : volume_sec * -1 : volume_sec // For switching bearish volume upside down from the 0 level
plot(series = volume_enable ? volume_data : na, title = "Vol", color = vol_color(vol_ma_resistance_1, vol_ma_resistance_2, vol_ma_resistance_3, vol_ma_resistance_4), linewidth = 3, style = plot.style_histogram, editable = true) // Main volume plotting, color is defined using the moving avarages as triggering color change levels
plot(series = volume_enable_vlr ? volume_sec_vlr : na, title = "VLR", color = color.new(color.lime, 20), linewidth = 1, style = plot.style_linebr, editable = true) // Plotting Volume Linebreak Resolution

// Primary Signals (only)
shape_style = volume_enable_reversed ? shape.labelup : shape.labeldown
plotshape(enable_supply_signals and (barstate.ishistory or drawOnRealTime) and volume_sec >= vol_ma_resistance_2 and hl2 > hl2[1] ? volume_data + volume_data * 0.1 : na, color = label_color(vol_ma_resistance_2, vol_ma_resistance_3, vol_ma_resistance_4), style = shape_style, text = "S", textcolor = text_color(vol_ma_resistance_4), title = "Supply Zone Signals", location = location.absolute, editable = true)
plotshape(enable_demand_signals and (barstate.ishistory or drawOnRealTime) and volume_sec >= vol_ma_resistance_2 and hl2 <= hl2[1] ? volume_data + volume_data * 0.1 : na, color = label_color(vol_ma_resistance_2, vol_ma_resistance_3, vol_ma_resistance_4),style = shape_style, text = "D", textcolor = text_color(vol_ma_resistance_4), title = "Demand Zone Signals", location = location.absolute, editable = true)

// Zero Line (base line)
zero_line_color = color.new(color.silver, 50)
hline(price = 0, title = "Zero Line", color = zero_line_color, linestyle = hline.style_solid, linewidth = 1, editable = true)
```

## Footer