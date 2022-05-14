# ADR% / ATR / LoD dist. Table

[ArmerSchlucker](https://www.tradingview.com/u/ArmerSchlucker/) Jun 14, 2021
tags:: AverageTrueRange, ATR, ADR, AverageDailyRange
Displays the following values in a table in the upper right corner of the chart:  
  

-   ADR%: Average daily range (in percent).  
    
-   ATR: [Average true range](https://www.tradingview.com/scripts/averagetruerange/) (hidden by default).  
    
-   LoD [dist](https://www.tradingview.com/symbols/OMXSTO-DIST/) .: Distance of current price to low of the day as a percentage of ATR.  
    

  
All values are calculated based on daily bars, no matter what time frame you are currently viewing. Doesn't work for time frames >1D, which is why the table is not shown on weekly/monthly charts.  
  
Credit to MikeC / TheScrutiniser and GlinckEastwoot for ADR% formula