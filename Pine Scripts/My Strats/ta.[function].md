
## ta.pivothigh()

### Code Example

``` JavaScript
//@version=5

indicator("Pivot plots", "", true)

pivotHigh = fixnan(ta.pivothigh(3,3))

plot(pivotHigh, "High pivot", ta.change(pivotHigh) ? na : color.olive, 3)

plotchar(ta.change(pivotHigh), "ta.change(pivotHigh)", "•", location.top, size = size.small)
```

#### Notes

- We use pivotHigh = fixnan(ta.pivothigh(3,3)) to hold our pivot values. Because ta.pivothigh() only returns a value when a new pivot is found, we use fixnan() to fill the gaps with the last pivot value returned. The gaps here refer to the na values ta.pivothigh() returns when no new pivot is found.
- Our pivots are detected three bars after they occur because we use the argument 3 for both the leftbars and rightbars parameters in our ta.pivothigh() call.
- The last plot is plotting a continuous value, but it is setting the plot’s color to na when the pivot’s value changes, so the plot isn’t visible then. Because of this, a visible plot will only appear on the bar following the one where we plotted using na color.
- The blue dot indicates when a new high pivot is detected and no plot is drawn between the preceding bar and that one. Note how the pivot on the bar indicated by the arrow has just been detected in the realtime bar, three bars later, and how no plot is drawn. The plot will only appear on the next bar, making the plot visible four bars after the actual pivot.


### ta.accdist

Accumulation/distribution index.
TYPE
series float
ta.iii

Intraday Intensity Index.
TYPE
series float
EXAMPLE
//@version=5
indicator("Intraday Intensity Index")
plot(ta.iii, color=color.yellow)

// the same on pine
f_iii() =>
    (2 * close - high - low) / ((high - low) * volume)

plot(f_iii())

### ta.nvi

Negative Volume Index.
TYPE
series float
EXAMPLE
//@version=5
indicator("Negative Volume Index")

plot(ta.nvi, color=color.yellow)

// the same on pine
f_nvi() =>
    float ta_nvi = 1.0
    float prevNvi = (nz(ta_nvi[1], 0.0) == 0.0)  ? 1.0: ta_nvi[1]
    if nz(close, 0.0) == 0.0 or nz(close[1], 0.0) == 0.0
        ta_nvi := prevNvi
    else
        ta_nvi := (volume < nz(volume[1], 0.0)) ? prevNvi + ((close - close[1]) / close[1]) * prevNvi : prevNvi
    result = ta_nvi

plot(f_nvi())

### ta.obv

On Balance Volume.
TYPE
series float
EXAMPLE
//@version=5
indicator("On Balance Volume")
plot(ta.obv, color=color.yellow)

// the same on pine
f_obv() =>
    ta.cum(math.sign(ta.change(close)) * volume)

plot(f_obv())

### ta.pvi

Positive Volume Index.
TYPE
series float
EXAMPLE
//@version=5
indicator("Positive Volume Index")

plot(ta.pvi, color=color.yellow)

// the same on pine
f_pvi() =>
    float ta_pvi = 1.0
    float prevPvi = (nz(ta_pvi[1], 0.0) == 0.0)  ? 1.0: ta_pvi[1]
    if nz(close, 0.0) == 0.0 or nz(close[1], 0.0) == 0.0
        ta_pvi := prevPvi
    else
        ta_pvi := (volume > nz(volume[1], 0.0)) ? prevPvi + ((close - close[1]) / close[1]) * prevPvi : prevPvi
    result = ta_pvi

plot(f_pvi())

### ta.pvt

Price-Volume Trend.
TYPE
series float
EXAMPLE
//@version=5
indicator("Price-Volume Trend")
plot(ta.pvt, color=color.yellow)

// the same on pine
f_pvt() =>
    ta.cum((ta.change(close) / close[1]) * volume)

plot(f_pvt())

### ta.tr

True range. Same as tr(false). It is max(high - low, abs(high - close[1]), abs(low - close[1]))
TYPE
series float
SEE ALSO
ta.trta.atr
ta.vwap

Volume-weighted average price. It uses hlc3 as a source series.
TYPE
series float

SEE ALSO

- ta.vwap
- ta.wad

Williams Accumulation/Distribution.

TYPE
series float

EXAMPLE

```
//@version=5

indicator("Williams Accumulation/Distribution")

plot(ta.wad, color=color.yellow)
```
```
// the same on pine
f_wad() =>
    trueHigh = math.max(high, close[1])
    trueLow = math.min(low, close[1])
    mom = ta.change(close)
    gain = (mom > 0) ? close - trueLow : (mom < 0) ? close - trueHigh : 0
    ta.cum(gain)

plot(f_wad())
```

### ta.wvad

Williams Variable Accumulation/Distribution.
TYPE
series float
EXAMPLE
//@version=5
indicator("Williams Variable Accumulation/Distribution")
plot(ta.wvad, color=color.yellow)

// the same on pine
f_wvad() =>
    (close - open) / (high - low) * volume

plot(f_wvad())
