---
title: "TradingView"
alias:
type: "Tool"
knowledge-topic: 
  - "Cryptocurrency"
  - "Day Trading"
keywords: "Crypto", "Chart"
URL: "https://tradingview.com"
author: 
publisher: 
publisher-url: 
published-date: 

synonym:
plural:
acronym:
language: 
abbreviation:

reference:
see-also:
recommended-by: 

date-created: 2022-05-12 • 00:24:12
date-modified: 2022-05-12 • 00:24:42
status: 
  - current: ("editing", "researching")
  - history: 
    - [[2022-05-12]]: "markdownload-extract"
---

# TradingView

## Search Embed
<iframe border=0 frameborder=0 height=250 width=500 src="https://www.tradingview.com/pine-script-docs/en/v5/search.html"></iframe>

***

## How to use a variable value in alert 

You can use special placeholders to access variable values in alert’s message. For example, you can create an alert on NASDAQ:AAPL and type in a message box: 

_{{exchange}}:{{ticker}}, price = {{close}}, volume = {{volume}}_

![](https://s3.amazonaws.com/cdn.freshdesk.com/data/helpdesk/attachments/production/43081305797/original/oeJ9srVr2wib7R277BknSB65GIJTMZZMiA.png?1572432796)

After the alert is triggered, you’ll get corresponding values:

![](https://s3.amazonaws.com/cdn.freshdesk.com/data/helpdesk/attachments/production/43190233787/original/Tl-G2hWLB1RrKYyKQrYYiS7dtGR5dg5YDg.png?1611135857)

Here is a list of available placeholders:

1. _{{ticker}}_ - ticker of the symbol used in alert (AAPL, BTCUSD, etc.).

2. _{{exchange}}_ - exchange of the symbol used in alert (NASDAQ, NYSE, MOEX, etc). Note that for delayed symbols, the exchange will end with “_DL” or “_DLY.” For example, “NYMEX_DL.”

3. _{{close}}, {{open}}, {{high}}, {{low}}, {{time}}, {{volume}}_ - corresponding values of the bar on which the alert has been triggered. Note that alerts on indicators, non-standard charts and drawings depends on a resolution, while simple price alerts (e.g., price crossing some value) are always calculated on 1-minute bars. {{time}} is in UTC, formatted as yyyy-MM-ddTHH:mm:ssZ. For example, 2019-08-27T09:56:00Z. Other values are fixed-point numbers with a decimal point separating the integral and fractional parts. For example, 1245.25.

4. _{{timenow}}_ - current fire time of the alert, formatted in the same way as {{time}}. Return time to the nearest second, regardless of the resolution.

5. _{{plot_0}}, {{plot_1}}, ... {{plot_19}}_ - corresponding output series of an indicator used in the alert. **Note that the plots are numbered from zero. The highest plot ID is 19 (you can access only 20 first output series)**. Output series are the values of an indicator you can see on a chart. For example, the built-in volume indicator has two output series: Volume and Volume MA. You can create an alert on it and type in a message box something like this:

_Volume: {{plot_0}}, Volume average: {{plot_1}}_

6. _{{interval}}_ - returns the interval (i.e. timeframe/resolution) of the chart that the alert is created on. Note that, for technical reasons, in some cases, this placeholder will return “1” instead of the timeframe on the chart. Regular price-based alerts (with conditions such as “AAPL Crossing 120” or “AMZN Greater Than 3600”) are all based on the symbol’s last value, so the timeframe of the chart is not relevant for the alert. Because of that, all price-based alerts are actually calculated on the 1m timeframe and the placeholder will always return “1” accordingly. Additionally, Range charts are also calculated based on 1m data so the {{interval}} placeholder will always return “1” on any alert created on a Range chart. With alerts created on drawings and indicators, this placeholder will function as expected.

Placeholders with the "strategy" prefix can only be used in [strategy alerts](https://www.tradingview.com/chart/?solution=43000481368):

-   _{{strategy.position_size}}_ - returns the value of the same keyword in Pine, i.e., the size of the current position.
-   _{{strategy.order.action}}_ - returns the string “buy” or “sell” for the executed order.
-   _{{strategy.order.contracts}}_ - returns the number of contracts of the executed order.
-   _{{strategy.order.price}}_ - returns the price at which the order was executed.
-   _{{strategy.order.id}}_ - returns the ID of the executed order (the string used as the first parameter in one of the function calls generating orders: strategy.entry, strategy.exit or strategy.order).
-   _{{strategy.order.comment}}_ - returns the comment of the executed order (the string used in the comment parameter in one of the function calls generating orders: strategy.entry, strategy.exit or strategy.order). If no comment is specified, then the value of _strategy.order.id_ will be used.
-   _{{strategy.order.alert_message}}_ - returns the value of the alert_message parameter which can be used in the strategy's Pine code when calling one of the functions used to place orders: strategy.entry, strategy.exit or strategy.order. This feature is only supported in Pine v4.
-   _{{strategy.market_position}}_ - returns the current position of the strategy in string form: “long”, “flat”, or “short”.
-   _{{strategy.market_position_size}}_ - returns the size of the current position as an absolute value, i.e. a non-negative number.
-   _{{strategy.prev_market_position}}_ - returns the previous position of the strategy in string form: “long”, “flat”, or “short”.
-   _{{strategy.prev_market_position_size}}_ - returns the size of the previous position as an absolute value, i.e. a non-negative number.

After the alert is triggered, you’ll see the corresponding values:

![](https://s3.amazonaws.com/cdn.freshdesk.com/data/helpdesk/attachments/production/43190233867/original/IzZd2g0gnedB7-PjxPLoFyj-sIYihP42Eg.png?1611135875)

The same rules apply to scripts written in Pine. Series are counted based on their calling order in the code. See the list of functions below. Their series can be used in notification messages:

-   plot;
-   plotshape;
-   plotchar;
-   plotarrow;
-   plotbar;
-   plotcandle.

If the series argument of such functions contains a Boolean value, 0 or 1 will be substituted in the notification message. Keep in mind that certain functions - plotcandle and plotbar - display 4 series each, and every one of them will be taken into account in the numbering logic.

However, this method of accessing plots is not always convenient. To make things easier, we added support for calling plots using their names. To do this, use the placeholder {{plot("Name")}}, where Name is the name of the series.

For built-in indicators, the only names that are supported are the ones that are used in the English version. In the example with the Volume indicator for accessing series using their names, you would include the following in the message:

_Volume: {{plot("Volume")}}, Volume average: {{plot("Volume MA")}}_

Similarly, for Pine Script to access the series, you should specify the name from the title argument of the corresponding functions, (supported for all plot functions except plotcandle and plotbar), and the language will no longer matter. If you do not have access to the code, the name can be seen in the style settings.

For example, to access the values of this script:

```js
//@version=4
study("My script")
plot(close, title="series")
```

Include _{{plot("series")}}_ in the alert message.

The same name is shown in the script settings:

![](https://s3.amazonaws.com/cdn.freshdesk.com/data/helpdesk/attachments/production/43081307198/original/8ipMDKYbYfRD6zNLvQwOKvnPeegnN7hhlQ.png?1572433072)

When using several indicators in a single alert, you can refer to the values of the first one - the one indicated in the first drop-down list. See example below.

![](https://s3.amazonaws.com/cdn.freshdesk.com/data/helpdesk/attachments/production/43081307334/original/JN7qnNfVr-6Ru2HXndOk_JR7JRHd8Ek_2Q.png?1572433089)

When an alert includes these settings, you can only refer to the MA values. To access the values of the script “My script,” you need to select it in the first drop-down list.

You can also specify new placeholders in the message argument of the alertcondition function. For example:

```js
//@version=4
study("My script")
alertcondition(close>open, message="price {{ticker}} = {{close}}")
```

The message from the argument is automatically pulled into the message window in the alert creation dialog.

_Please note that when creating an alert with a condition from the alertcondition function, the value substitution will only work for v4 scripts or higher._

Values from triggered alerts can be used together with webhooks by sending variable values from a message to the desired addresses. Or by using external 3rd party apps like TradingView Alerts to MT4/MT5, which already utilizes dynamic values usage. Some syntax use-cases can be found in [this example script](https://www.tradingview.com/script/9MJO3AgE-TradingView-Alerts-to-MT4-MT5-dynamic-variables-NON-REPAINTING/). This opens up even more possibilities for those of you who use alerts.

## Keyboard Shortcuts #hotkeys 
### Chart

![Image from Gyazo](https://i.gyazo.com/579c309f9a3dd7c57f42b888dfe70179.png)

---
![Image from Gyazo](https://i.gyazo.com/ecdcea2d7efa7cc598b999e724314792.png)

---
[![Image from Gyazo](https://i.gyazo.com/42845e941e1d11f8141e17044adb1ea9.png)](https://gyazo.com/42845e941e1d11f8141e17044adb1ea9)

### Indicators & Drawings

![Image from Gyazo](https://i.gyazo.com/d0752f597d8f90c1099ded529b9b3b20.png)

---
![Image from Gyazo](https://i.gyazo.com/95771705ff5e17990709f3310b4f77fd.png)

### Watchlist & Screener

![Image from Gyazo](https://i.gyazo.com/4f7c9c0308495ab2d704a4f5961cf971.png)

### Pine Editor

![Image from Gyazo](https://i.gyazo.com/c1646b223632fb143aa3e07997f2328b.png)

---
![Image from Gyazo](https://i.gyazo.com/afeba50372adf1a9f926077487c59d1c.png)

---
![Image from Gyazo](https://i.gyazo.com/f6d8e6168630d92641bbf6d9ed3085ef.png)

### Trading

[![Image from Gyazo](https://i.gyazo.com/d7eb7d133a3bc00edb82d631c76d4c88.png)](https://gyazo.com/d7eb7d133a3bc00edb82d631c76d4c88)

### Alerts

[![Image from Gyazo](https://i.gyazo.com/0f1c9a397a1964f65f19d3382dabbd4a.png)](https://gyazo.com/0f1c9a397a1964f65f19d3382dabbd4a)

### Desktop App

[![Image from Gyazo](https://i.gyazo.com/59190fb41bb3b21b2fec80bb1e87450b.png)](https://gyazo.com/59190fb41bb3b21b2fec80bb1e87450b)


---
---

***
# Footer

