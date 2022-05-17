# plot(

## Introduction

The plot() function is the most frequently used function used to display information calculated using Pine scripts. It is versatile and can plot different styles of lines, histograms, areas, columns (like volume columns), fills, circles or crosses.


## #PineScript Examples

### This script showcases a few different uses of plot() in an overlay script:

``` Javascript
//@version=5

indicator("`plot()`", "", true)

plot(high, "Blue `high` line")

plot(math.avg(close, open), "Crosses in body center", close > open ? color.lime : color.purple, 6, plot.style_cross)

plot(math.min(open, close), "Navy step line on body low point", color.navy, 3, plot.style_stepline)

plot(low, "Gray dot on `low`", color.gray, 3, plot.style_circles)

color VIOLET = #AA00FF
color GOLD   = #CCCC00

ma = ta.alma(hl2, 40, 0.85, 6)
var almaColor = color.silver

almaColor := ma > ma[2] ? GOLD : ma < ma[2]  ? VIOLET : almaColor

plot(ma, "Two-color ALMA", almaColor, 2)
```

## Notes
