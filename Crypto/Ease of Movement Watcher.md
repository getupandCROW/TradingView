---
---

# Ease of Movement Watcher

author:: 
autherLink:: [ProfitProgrammers](https://www.tradingview.com/u/ProfitProgrammers/)
subscriptionLevel:: Premium
posted:: Jun 21, 2019


Here’s a handy [Ease of Movement](https://www.tradingview.com/scripts/easeofmovement/) ( [EMV](https://www.tradingview.com/symbols/LSE-EMV/) ) Indicator. I tried to include detailed comments so that anyone that’s learning pine can follow along.  
  
The [Ease of Movement](https://www.tradingview.com/scripts/easeofmovement/) Indicator is a [volume](https://www.tradingview.com/scripts/volume/) based oscillator that is designed to measure the ease (or movability) of price movement for a security. The [EMV](https://www.tradingview.com/symbols/LSE-EMV/) is a centered oscillator, meaning that values can fluctuate above and below zero.  
  
To understand how to use and interpret the [EMV](https://www.tradingview.com/symbols/LSE-EMV/) Indicator, its crucial to first understand its two main calculations :  
Distance Moved = ((high + low) / 2) - ((high + low) / 2)  
-This is the difference between the current period’s midpoint and the previous period’s  
midpoint.  
  
Box Ratio = ( [volume](https://www.tradingview.com/scripts/volume/) / 100,000) / (high - low)  
-When calculating the Box Ratio, it is common to divide the [volume](https://www.tradingview.com/scripts/volume/) by 100,000 for a clearer visualization of the data. However, users can choose  
to modify this value with the ‘volumeDiv’ input.  
  
The [Ease of Movement](https://www.tradingview.com/scripts/easeofmovement/) Value is then pretty simple to calculate:  
[EMV](https://www.tradingview.com/symbols/LSE-EMV/) = (Distance Moved / Box Ratio)  
  
The indicator then plots a [SMA](https://www.tradingview.com/scripts/simplemovingaverage/) of the previous 24 [EMV](https://www.tradingview.com/symbols/LSE-EMV/) Values.  
  
Looking at the formula, we know that combining low [volume](https://www.tradingview.com/scripts/volume/) with a large {high, low} range will result in a relatively small box ratio value. Thus, we know that the [EMV](https://www.tradingview.com/symbols/LSE-EMV/) value for that period will be higher since [EMV](https://www.tradingview.com/symbols/LSE-EMV/) is found by dividing the Distance Moved by the Box Ratio.  
  
Here’s a simple guide to interpreting the EMV:  
- If ( [EMV](https://www.tradingview.com/symbols/LSE-EMV/) > 0)  
then price is increasing with relative ease.  
  
-If ( [EMV](https://www.tradingview.com/symbols/LSE-EMV/) < 0)  
then price is decreasing with relative ease.  
  
- If [high-low](https://www.tradingview.com/symbols/spread/LSE%3AHIGH-NYSE%3ALOW/) range is large and [volume](https://www.tradingview.com/scripts/volume/) is low  
then [ease of movement](https://www.tradingview.com/scripts/easeofmovement/) is high.  
  
-If [high-low](https://www.tradingview.com/symbols/spread/LSE%3AHIGH-NYSE%3ALOW/) range is small and [volume](https://www.tradingview.com/scripts/volume/) is high  
then [ease of movement](https://www.tradingview.com/scripts/easeofmovement/) is low.  
  
The Chart:  
-The histogram represents the [Simple Moving Average](https://www.tradingview.com/scripts/simplemovingaverage/) of [EMV](https://www.tradingview.com/symbols/LSE-EMV/) Values. The default length is 24, but users can adjust this value at the inputs menu(I've  
found 24 works best).  
  
-The teal and pink dotted lines represent the standard deviation of the [SMA](https://www.tradingview.com/scripts/simplemovingaverage/) of [EMV](https://www.tradingview.com/symbols/LSE-EMV/) values multiplied by 2.5.  
  
-The histogram turns dark green when the [EMV](https://www.tradingview.com/symbols/LSE-EMV/) [SMA](https://www.tradingview.com/scripts/simplemovingaverage/) is greater than the top teal dotted standard deviations line.  
  
-The histogram turns maroon when the [EMV](https://www.tradingview.com/symbols/LSE-EMV/) [SMA](https://www.tradingview.com/scripts/simplemovingaverage/) falls below the bottom pink standard deviation line.  
  
How To Use:  
Enter a long position when the most recent [EMV](https://www.tradingview.com/symbols/LSE-EMV/) [SMA](https://www.tradingview.com/scripts/simplemovingaverage/) value was below the lower pink stand. dev. line and the current [EMV](https://www.tradingview.com/symbols/LSE-EMV/) [SMA](https://www.tradingview.com/scripts/simplemovingaverage/) value rises above that  
same pink line. That means the previous bar was maroon and the current bar is not.  
  
If the user enables the option to show entry points, a [green dot](https://www.tradingview.com/symbols/NYSE-GDOT/) will be plotted when it is time to enter a long position.  
  
Exit the long position when the most recent [EMV](https://www.tradingview.com/symbols/LSE-EMV/) [SMA](https://www.tradingview.com/scripts/simplemovingaverage/) value was above the upper green standard deviation line and the current [EMV](https://www.tradingview.com/symbols/LSE-EMV/) [SMA](https://www.tradingview.com/scripts/simplemovingaverage/) value falls  
below that same line. If this is true, then the previous bar will be dark green, and the current will be light green.  
  
If the ‘showExits’ option is enabled, then a red dot will be plotted when it is time to exit the long position.  
  
Input Options:  
- 'volumeDiv' : Integer. Used in the calculation of Box Ratio.  
- 'lenSMA' : Integer. The length of the [Simple Moving Average](https://www.tradingview.com/scripts/simplemovingaverage/) of [Ease of Movement](https://www.tradingview.com/scripts/easeofmovement/) Values.  
- 'showStDev' : Bool. If true, dotted green and red lines will be shown at values equal to 2.5 * standard deviation of emvSMA and -2.5 * standard deviation of  
emvSMA.  
- 'showEntries' and 'showExits' : Bool. If true, a green circle will be plotted at long entry points and a red circle will be plotted at long exit points.  
- 'changeBgColor': Bool. If true, the background color will change to green when it is time to enter a long position and red when it is time to exit.  
  
Alerts:  
- When it is time to enter a long position, an alert with the message "EMV Tracker - Enter Long" is sent.  
- When it is time to exit a long position, an alert with the message "EMV Tracker - Exit Long" is sent.  
  
NOTE:  
- I usually use this indicator to confirm signals from other indicators rather than relying on it solely.  
- Most accurate signals are generated on 30 minutes with the default input values I've set in the script.  
  
Shoot me a message if you have any ideas for modifications or questions.  
  
~ Happy Trading ~