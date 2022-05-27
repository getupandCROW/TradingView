# strategy.exit()

## Syntax
> strategy.exit(id, from_entry, qty, qty_percent, profit, limit, loss, stop, trail_price, trail_points, trail_offset, oca_name, comment, when, alert_message) → void

## About
- It is a command to exit either a specific entry, or whole market position. 
- If an order with the same ID is already pending, it is possible to modify the order. 
- If an entry order was not filled, but an exit order is generated, the exit order will wait till entry order is filled and then the exit order is placed. 
- To deactivate an exit order, the command [strategy.cancel](https://www.tradingview.com/pine-script-reference/v5/#fun_strategy{dot}cancel) or [strategy.cancel_all](https://www.tradingview.com/pine-script-reference/v5/#fun_strategy{dot}cancel_all) should be used. 
- If the function [strategy.exit](https://www.tradingview.com/pine-script-reference/v5/#fun_strategy{dot}exit) is called once, it exits a position only once. 
- If you want to exit multiple times, the command [strategy.exit](https://www.tradingview.com/pine-script-reference/v5/#fun_strategy{dot}exit) should be called multiple times. 
- If you use a stop loss and a trailing stop, their order type is 'stop', so only one of them is placed (the one that is supposed to be filled first). 
- If all the following parameters 'profit', 'limit', 'loss', 'stop', 'trail_points', 'trail_offset' are 'NaN', the command will fail. 
- To use market order to exit, the command [strategy.close](https://www.tradingview.com/pine-script-reference/v5/#fun_strategy{dot}close) or [strategy.close_all](https://www.tradingview.com/pine-script-reference/v5/#fun_strategy{dot}close_all) should be used.


## Example

```js
//@version=5
strategy(title = "simple strategy exit example")
strategy.entry("long", strategy.long, 1, when = open > high[1]) 
	// enter long by market if current open great then previous high
strategy.exit("exit", "long", profit = 10, loss = 5) 
	// generate full exit bracket (profit 10 points, loss 5 points per contract) from entry with name "long"
```

## Arguments

- **id** (series string) A required parameter. The order identifier. It is possible to cancel or modify an order by referencing its identifier.
- **from_entry** (series string) An optional parameter. The identifier of a specific entry order to exit from it. To exit all entries an empty string should be used. The default values is empty string.
- **qty** (series int/float) An optional parameter. Number of contracts/shares/lots/units to exit a trade with. The default value is 'NaN'.
- **qty_percent** (series int/float) Defines the percentage of (0-100) the position to close. Its priority is lower than that of the 'qty' parameter. Optional. The default is 100.
- **profit** (series int/float) An optional parameter. Profit target (specified in ticks). If it is specified, a limit order is placed to exit market position when the specified amount of profit (in ticks) is reached. The default value is 'NaN'.
- **limit** (series int/float) An optional parameter. Profit target (requires a specific price). If it is specified, a limit order is placed to exit market position at the specified price (or better). Priority of the parameter 'limit' is higher than priority of the parameter 'profit' ('limit' is used instead of 'profit', if its value is not 'NaN'). The default value is 'NaN'.
- **loss** (series int/float) An optional parameter. Stop loss (specified in ticks). If it is specified, a stop order is placed to exit market position when the specified amount of loss (in ticks) is reached. The default value is 'NaN'.
- **stop** (series int/float) An optional parameter. Stop loss (requires a specific price). If it is specified, a stop order is placed to exit market position at the specified price (or worse). Priority of the parameter 'stop' is higher than priority of the parameter 'loss' ('stop' is used instead of 'loss', if its value is not 'NaN'). The default value is 'NaN'.
- **trail_price** (series int/float) An optional parameter. Trailing stop activation level (requires a specific price). If it is specified, a trailing stop order will be placed when the specified price level is reached. The offset (in ticks) to determine initial price of the trailing stop order is specified in the 'trail_offset' parameter: X ticks lower than activation level to exit long position; X ticks higher than activation level to exit short position. The default value is 'NaN'.
- **trail_points** (series int/float) An optional parameter. Trailing stop activation level (profit specified in ticks). If it is specified, a trailing stop order will be placed when the calculated price level (specified amount of profit) is reached. The offset (in ticks) to determine initial price of the trailing stop order is specified in the 'trail_offset' parameter: X ticks lower than activation level to exit long position; X ticks higher than activation level to exit short position. The default value is 'NaN'.
- **trail_offset** (series int/float) An optional parameter. Trailing stop price (specified in ticks). The offset in ticks to determine initial price of the trailing stop order: X ticks lower than 'trail_price' or 'trail_points' to exit long position; X ticks higher than 'trail_price' or 'trail_points' to exit short position. The default value is 'NaN'.
- **oca_name** (series string) An optional parameter. Name of the OCA group (oca_type = [strategy.oca.reduce](https://www.tradingview.com/pine-script-reference/v5/#var_strategy{dot}oca{dot}reduce)) the profit target, the stop loss / the trailing stop orders belong to. If the name is not specified, it will be generated automatically.
- **comment** (series string) An optional parameter. Additional notes on the order.
- **when** (series bool) An optional parameter. Condition of the order. The order is placed if condition is 'true'. If condition is 'false', nothing happens (the previously placed order with the same ID is not cancelled). Default value is 'true'.
- **alert_message** (series string) An optional parameter which replaces the {{strategy.order.alert_message}} placeholder when it is used in the "Create Alert" dialog box's "Message" field.

Related:: [[strategy.close]]
