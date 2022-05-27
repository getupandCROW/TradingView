---
date created: Friday, May 27th 2022, 5:50:34 am
date modified: Friday, May 27th 2022, 8:31:05 am
title: strategy.close()
---

# strategy.close()
## About
- It is a command to exit from the entry with the specified ID.
- If there were multiple entry orders with the same ID, all of them are exited at once.
- If there are no open entries with the specified ID by the moment the command is triggered, the command will not come into effect.
- The command uses market order. Every entry is closed by a separate market order.

## Syntax
`strategy.close(id, when, comment, qty, qty_percent, alert_message) → void`

## Example
```js
//@version=5
strategy("closeEntry Demo", overlay=false)
strategy.entry("buy", strategy.long, when = open > close)
strategy.close("buy", when = open < close, qty_percent = 50, comment = "close buy entry for 50%")
plot(strategy.position_size)
```

## Arguments
- **id** (series <mark style="background: #FFB8EBA6;">string</mark> ) *A required parameter*. The order identifier. It is possible to close an order by referencing its identifier.
- when (series <mark style="background: #FFB86CA6;">bool</mark> ) *An optional parameter*. Condition of the command.
- **qty** (series <mark style="background: #FFF3A3A6;">int</mark> /<mark style="background: #BBFABBA6;">float</mark> ) *An optional parameter*. Number of contracts/shares/lots/units to exit a trade with. The default value is 'NaN'.
	- **qty_percent** (series <mark style="background: #FFF3A3A6;">int</mark> /<mark style="background: #BBFABBA6;">float</mark> ) Defines the percentage (0-100) of the position to close. Its priority is lower than that of the 'qty' parameter. Optional. The default is 100.
- **comment** (series <mark style="background: #FFB8EBA6;">string</mark> ) *An optional parameter*. Additional notes on the order.
- **alert_message** (series <mark style="background: #FFB8EBA6;">string</mark> ) *An optional parameter* which replaces the [[{{strategy.order.alert_message}}]] placeholder when it is used in the "Create Alert" dialog box's "Message" field.

## strategy.close_all

### About
Exits the current market position, making it flat.

### Syntax
```
strategy.close_all(when, comment, alert_message) → void
```

 ### Example
```js
//@version=5
strategy("closeAll Demo", overlay=false)
strategy.entry("buy", strategy.long, when = open > close)
strategy.close_all(when = open < close, comment = "close all entries")
plot(strategy.position_size)
```

### Arguments
- **when** (series bool) An optional parameter. Condition of the command.
- **comment** (series string) An optional parameter. Additional notes on the order.
- **alert_message** (series string) An optional parameter which replaces the {{strategy.order.alert_message}} placeholder when it is used in the "Create Alert" dialog box's "Message" field.

 ## Footer

Related:: [[strategy.exit]]
