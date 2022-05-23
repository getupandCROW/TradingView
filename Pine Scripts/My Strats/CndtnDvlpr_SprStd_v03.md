


```js
//@version=5

strategy(title="Condition Developer Super Study Script [andCROW] v03", shorttitle="CndtnDvlpr_SprStd_v03", overlay=true, precision = 0)

  
  

// --*************************- ************************* -*************************-- //

                        // -- plot() | Condition Examples -- //

  
  

src                                    =           close

BULL_COLOR                  =           color.lime

i                                       =           1

len                                   =           input(20, "Length")

float f                              =           10.5

closeRoundedToTick     =           math.round_to_mintick(close)

st                                     =           ta.supertrend(4, 14)

var barRange                  =           float(na)

var firstBarOpen             =           open

varip float lastClose       =           na

[macdLine, signalLine, histLine]        =           ta.macd(close, 12, 26, 9)

  
  

priceClose                              =          (close)

priceOpen                               =          (open)

priceHigh                               =          (high)

priceLow                                =          (low)

  

priceClose_1                            =          (close[1])

priceOpen_1                             =          (open[1])

priceHigh_1                             =          (high[1])

priceLow_1                              =          (low[1])

  

priceClose_2                            =          (close[2])

priceOpen_2                             =          (open[2])

priceHigh_2                             =          (high[2])

priceLow_2                              =          (low[2])

  

priceClose_3                            =          (close[3])

priceOpen_3                             =          (open[3])

priceHigh_3                             =          (high[3])

priceLow_3                              =          (low[3])

  

priceClose_4                            =          (close[4])

priceOpen_4                             =          (open[4])

priceHigh_4                             =          (high[4])

priceLow_4                              =          (low[4])

  
  

// --*************************- ************************* -*************************-- //

  
  

// --*************************- ************************* -*************************-- //

                              // -- INPUTS  ||  Plots  -- //

///////////////////////////////////////////////////////////////////////////////

// Date:2017.11.13

// Author: Backtest-Rookies.com

// Version: 1.0

// Description: A Series of default strategy inputs

////////////////////////////////////////////////////////////////////////////////////////

// Notes:

//  - This template is better suited to instruments that trade 24/5 or 24/7 (crypto)

//    as trading sessions can be selected.

///////////////////////////////////////////////////////////////////////////////////////

  

// Create General Strategy Inputs

dir_inp = input(defval="Both", title='Trade Direction', options=["Long Only","Short Only","Both"])

st_yr_inp = input(defval=2017, title='Backtest Start Year', type=integer)

st_mn_inp = input(defval=01, title='Backtest Start Month', type=integer)

st_dy_inp = input(defval=01, title='Backtest Start Day', type=integer)

en_yr_inp = input(defval=2025, title='Backtest End Year', type=integer)

en_mn_inp = input(defval=01, title='Backtest End Month', type=integer)

en_dy_inp = input(defval=01, title='Backtest End Day', type=integer)

  

// Default Stop Types

fstp = input(defval=true, title="Fixed % stop")

fper = input(defval=0.1, title='% for fixed stop', type=float)

atsp = input(defval=false, title="ATR Based stop")

atrl = input(defval=7, title='ATR Length for stop')

atrm = input(defval=1, title='ATR Multiplier for stop')

  

// Sessions

asa_inp = input(defval=true, title="Trade the Asian Session")

eur_inp = input(defval=true, title="Trade the European Session")

usa_inp = input(defval=true, title="Trade the US session")

ses_cls = input(defval=true, title="End of Session Close Out?")

  

// Session Start / End times (In exchange TZ = UTC-5)    

asa_ses = "1700-0300"

eur_ses = "0200-1200"

usa_ses = "0800-1700"  

  

in_asa = time(period, asa_ses)

in_eur = time(period, eur_ses)

in_usa = time(period, usa_ses)

  

// Long / Short Logic

dir = dir_inp == "Both" ? strategy.direction.all :

  dir_inp == "Short Only" ? strategy.direction.short :

  strategy.direction.long

strategy.risk.allow_entry_in(dir)

  

// Set start and end dates for backtest

start = timestamp(st_yr_inp, st_mn_inp, st_dy_inp,00,00)

end = timestamp(en_yr_inp, en_mn_inp, en_dy_inp,00,00)

  

// Check if we are in a sessions we want to trade

can_trade = asa_inp and not na(in_asa) ? true :

  eur_inp and not na(in_eur) ? true :

  usa_inp and not na(in_usa) ? true :

  false

// atr calc for stop

atr = atr(atrl)

atr_stp_dst = atr * atrm

  

// --------------------------------------------------------- //

//                                                           //

//                  INSERT STRATEGY CODE                     //

//                                                           //

// --------------------------------------------------------- //

//

// Notes:

//  1 - To use the backtest start and end time you must include

//      time >= start and time <= end in your entry checks

//

//  2 - To use the session input functions you must include the

//      can_trade check in your entry conditions

//

//  3 - End of session supported but requires that that close_all

//      call below is not removed from the strategy.

//

// --------------------------------------------------------- //

  
  
  
  
  
  
  
  

    // --*************-- //

    // --*************-- //

  

    // --*************-- //

    // --*************-- //

  

    // --*************-- //

    // --*************-- //

  

//

//atrPeriodInput        =     input.int(14,       "ATR period",       minval   =  1,              tooltip       =   "Using a period of 1 yields True Range.")

//

//var table atrDisplay  =     table.new(position.top_right,   1,  1,  bgcolor  =  color.gray,     frame_width   =   2,    frame_color = color.black)

//myAtr                 =     ta.atr(atrPeriodInput)

//

//if barstate.islast

//    table.cell(atrDisplay, 0, 0, str.tostring(myAtr, format.mintick), text_color = color.white)

//

  
  

var string GP1 = "Moving averages"

int     masQtyInput    = input.int(20, "Quantity", minval = 1, maxval = 40, group = GP1, tooltip = "1-40")

int     masStartInput  = input.int(20, "Periods begin at", minval = 2, maxval = 200, group = GP1, tooltip = "2-200")

int     masStepInput   = input.int(20, "Periods increase by", minval = 1, maxval = 100, group = GP1, tooltip = "1-100")

  

var string GP2 = "Display"

string  tableYposInput = input.string("top", "Panel position", inline = "11", options = ["top", "middle", "bottom"], group = GP2)

string  tableXposInput = input.string("right", "", inline = "11", options = ["left", "center", "right"], group = GP2)

color   bullColorInput = input.color(color.new(color.green, 30), "Bull", inline = "12", group = GP2)

color   bearColorInput = input.color(color.new(color.red, 30), "Bear", inline = "12", group = GP2)

color   neutColorInput = input.color(color.new(color.black, 30), "Neutral", inline = "12", group = GP2)

  

var table panel = table.new(tableYposInput + "_" + tableXposInput, 2, masQtyInput + 1)

if barstate.islast

    // Table header.

    table.cell(panel, 0, 0, "MA", bgcolor = neutColorInput)

    table.cell(panel, 1, 0, "Value", bgcolor = neutColorInput)

  

int period = masStartInput

for i = 1 to masQtyInput

    // ————— Call MAs on each bar.

    float ma = ta.sma(close, period)

    // ————— Only execute table code on last bar.

    if barstate.islast

        // Period in left column.

        table.cell(panel, 0, i, str.tostring(period), bgcolor = neutColorInput)

        // If MA is between the open and close, use neutral color. If close is lower/higher than MA, use bull/bear color.

        bgColor = close > ma ? open < ma ? neutColorInput : bullColorInput : open > ma ? neutColorInput : bearColorInput

        // MA value in right column.

        table.cell(panel, 1, i, str.tostring(ma, format.mintick), text_color = color.black, bgcolor = bgColor)

    period += masStepInput

  
  
  

    // --*************-- //

    // --*************-- //

  
  
  

line1           =       ta.sma(close,       5)

line2           =       ta.sma(close,       20)

p1PlotID        =       plot(line1)

p2PlotID        =       plot(line2)

  

fill(p1PlotID,  p2PlotID,   line1 > line2     ?    color.new(color.green, 90)     :     color.new(color.red, 90))

  
  
  
  

// plotColor = if close > open

//     color.green

// else

//     color.red

  
  
  

    // --***************************-- //

    // --Candlestick Count and Color-- //

    // - Candlestick Count and Color - //

    // --Candlestick Count and Color-- //    

    // --***************************-- //

  

/////////////////-- Green Bars Count --//

////////////

///////

///

//

//var cntCnscUPDN = 0

//

//isGreen = close >= open

//

//if isGreen

//    cntCnscUPDN := cntCnscUPDN + 1

//

//plot(cntCnscUPDN)

//

//CndlStk_PrdNpt = input.int(14,  "Consecutive Candlestick Colors Period", minval = 1, tooltip = "A running count of the # of consecutive green or red candles. Lookback Length --> (period).")

//

//var table CndlStkCnt_Display = table.new(position.top_right, 10, 1, bgcolor = (isGreen ? color.green : color.red), frame_width = 2, frame_color = color.black)

//

//if barstate.islast

//    table.cell(atrDisplay,      0,      0,      str.tostring(cntCnscUPDN,       format.mintick),    text_color      =       color.white)

//

  
  

    // --*************-- //

    //      --RSI--      //

    //      - RSI -      //

    //      --RSI--      //

    // --*************-- //

  
  
  

r = ta.rsi(close, 20)

rIsLow = r < 30

hline(30)

  

plot(r,                     "RSI",                          rIsLow      ?       color.fuchsia       :       color.black)    // Method #1: Change the plot's color.

  

plotchar(rIsLow,            "rIsLow char at bottom", "▲",   location.bottom,        size = size.small)                      // Method #2: Plot a character in the bottom region of the display.

  

plotchar(rIsLow ? r : na,   "rIsLow char on line", "•",     location.absolute,      color.red,          size = size.small)  // Method #3: Plot a character on the RSI line.

  

plotshape(rIsLow,           "rIsLow shape",                 shape.arrowup,          location.top)                           // Method #4: Plot a shape in the top region of the display.

  

plotarrow(rIsLow ? 1 : na,  "rIsLow arrow")                                                                                 // Method #5: Plot an arrow.

  

bgcolor(rIsLow ? color.new(color.green, 90) : na)                                                                           // Method #6: Change the background's color.

  
  
  
  

    // --*************-- //

    // --*************-- //

  
  
  
  

sensitivityInput = input.int(2, "Sensitivity for (SMA-20-CLOSE)", minval = 1, tooltip = "Higher values make color changes less sensitive.")

  

ma = ta.sma(close, 20)

maUp = ta.rising(ma, sensitivityInput)

maDn = ta.falling(ma, sensitivityInput)

  
  

var maColor = color.gray                                                                                // On first bar only, initialize color to gray

  

if maUp    

    maColor := color.lime                                                                               // MA has risen for two bars in a row --> make it lime.

else if maDn    

    maColor := color.fuchsia                                                                            // MA has fallen for two bars in a row --> make it fuchsia.

  

plot(ma, "MA", maColor, 2)

  
  
  

// --*************************- ************************* -*************************-- //

  
  

// --*************************- ************************* -*************************-- //

                        // -- 3 Candle Odds | Simple Start -- //

  
  
  

// determine candle direction

candle_dir = math.round((close-open)*2)/2

  
  

shortCondition = (candle_dir[2] >= 0 and candle_dir[1] >= 0 and candle_dir < 0)                         // sell if previous 2 candles were green and this is red

  

longCondition = (candle_dir[3] < 0 and candle_dir[2] < 0 and candle_dir[1] < 0 and candle_dir > 0)      // buy if previous 3 candles was red, and this candle was green

  
  
  

// --*************************- ************************* -*************************-- //

  
  

// --*************************- ************************* -*************************-- //

            // -- ALERT SIGNS--||--INDICATOR SIGNALS--||--SCREENING -- //

  
  
  
  
  
  
  
  

// --*************************- ************************* -*************************-- //

  
  

// --*************************- ************************* -*************************-- //

                        // -- Strategy--||--ENTRY--||--EXIT -- //

  
  
  

long_condition = false // can_trade, time >= start etc...

short_condition = false

  

if (long_condition)

    strategy.entry("Long Entry",  strategy.long)

    if strategy.position_size <= 0 // Less than as in both direction strat - Could be long before switching

        if atsp

            atr_stop = open  - atr_stp_dst

            strategy.exit('ATR Fixed Short Stop', "Long Entry", stop=atr_stop)

        if fstp

            stop = open - (open * fper)

            strategy.exit('Perc Fixed Long Stop Exit', "Long Entry", stop=stop)

  

if (short_condition)

    strategy.entry("Short Entry",strategy.short)

    if strategy.position_size >= 0 // Greater than as in both direction strat - Could be long before switching

        if atsp

            atr_stop = open  + atr_stp_dst

            strategy.exit('ATR Fixed Short Stop Exit', "Short Entry", stop=atr_stop)

        if fstp

            stop = open + (open * fper)

            strategy.exit('Perc Fixed Short Stop Exit', "Short Entry", stop=stop)

  
  

strategy.close_all(when=not can_trade and ses_cls)

  

// Testing & Debug Plots

//plot(can_trade ? 1 : 0, color=purple, linewidth=2)

//plot(na(in_asa) ? 0 : 1, color=red)

//plot(na(in_eur) ? 0 : 1, color=blue)

//plot(na(in_usa) ? 0 : 1, color=green)

  
  
  
  

// --*************************- ************************* -*************************-- //

  
  

//// # ========================================================================= #

//                    // --- START My Testing --- //

//// # ========================================================================= #

//

  

bgcolor(rIsLow ? color.new(color.green, 90) : na)  

  
  
  
  
  
  
  

//

//if zerolineCross > hl2                      // 1st half SHORT,2nd half LONG

//

//

//

//

//

////if signalCross > hl2                                        // DOWNtrend

//    if signalCrossColor == red                              // STRONG DOWNtrend

//        if zerolineCross < hl2                              //

//            if CDLTRD_hullMA > hl2 and CDLTRD_hullMA >

//                if

//

//

//        else if zerolineCross ? hl2

//            if

//

//

//    else if signalCrossColor == green

//

//

//if signalCross < hl2  

//    if SMI < hl2 and VWMA < hl2 and AVSL < hl2  // 3 little are under price

//        if crossunder(signalCross, hl2)         // signal crosses under price

//            // BUY LONG

//            

//

//if crossunder(zerolineCross, hl2)         // signal crosses under price

//    if (//all 6 of the lines are < hl2

//    // BUY LONG

//

//

//if hullMA rises above (high) and (crossover(hl2) or turns red)

//    if marketTrender < hl2

//        // SELL LONG

//    else if

//

//else if hullMA falls below (low)

//

//

//// # ========================================================================= #

//                    // --- FINISH My Testing --- //

//// # ========================================================================= #
```