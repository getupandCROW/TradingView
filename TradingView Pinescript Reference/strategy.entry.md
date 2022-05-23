### strategy.entry

> strategy.entry(id, direction, qty, limit, stop, oca_name, oca_type, comment, when, alert_message) → void

- It is a command to enter market position. 
- If an order with the same ID is already pending, it is possible to modify the order. 
- If there is no order with the specified ID, a new order is placed. 
- To deactivate an entry order, the command [strategy.cancel](https://www.tradingview.com/pine-script-reference/v5/#fun_strategy{dot}cancel) or [strategy.cancel_all](https://www.tradingview.com/pine-script-reference/v5/#fun_strategy{dot}cancel_all) should be used. 
- In comparison to the function [strategy.order](https://www.tradingview.com/pine-script-reference/v5/#fun_strategy{dot}order), the function [strategy.entry](https://www.tradingview.com/pine-script-reference/v5/#fun_strategy{dot}entry) is affected by pyramiding and it can reverse market position correctly. 
- If both 'limit' and 'stop' parameters are 'NaN', the order type is market order.



## Example

```js
//@version=5
strategy(title = "simple strategy entry example")
strategy.entry("enter long", strategy.long, 1, when = open > high[1]) 
	// enter long by market if current open great then previous high
strategy.entry("enter short", strategy.short, 1, when = open < low[1]) 
	// enter short by market if current open less then previous low
```

## Arguments

- **id** (series string) A required parameter. The order identifier. It is possible to cancel or modify an order by referencing its identifier.
- **direction** (strategy_direction) A required parameter. Market position direction: 'strategy.long' is for long, 'strategy.short' is for short.
- **qty** (series int/float) An optional parameter. Number of contracts/shares/lots/units to trade. The default value is 'NaN'.
- **limit** (series int/float) An optional parameter. Limit price of the order. If it is specified, the order type is either 'limit', or 'stop-limit'. 'NaN' should be specified for any other order type.
- **stop** (series int/float) An optional parameter. Stop price of the order. If it is specified, the order type is either 'stop', or 'stop-limit'. 'NaN' should be specified for any other order type.
- **oca_name** (series string) An optional parameter. Name of the OCA group the order belongs to. If the order should not belong to any particular OCA group, there should be an empty string.
- **oca_type** (input string) An optional parameter. Type of the OCA group. The allowed values are: [strategy.oca.none](https://www.tradingview.com/pine-script-reference/v5/#var_strategy{dot}oca{dot}none) - the order should not belong to any particular OCA group; [strategy.oca.cancel](https://www.tradingview.com/pine-script-reference/v5/#var_strategy{dot}oca{dot}cancel) - the order should belong to an OCA group, where as soon as an order is filled, all other orders of the same group are cancelled; [strategy.oca.reduce](https://www.tradingview.com/pine-script-reference/v5/#var_strategy{dot}oca{dot}reduce) - the order should belong to an OCA group, where if X number of contracts of an order is filled, number of contracts for each other order of the same OCA group is decreased by X.
- **comment** (series string) An optional parameter. Additional notes on the order.
- **when** (series bool) An optional parameter. Condition of the order. The order is placed if condition is 'true'. If condition is 'false', nothing happens (the previously placed order with the same ID is not cancelled). Default value is 'true'.
- **alert_message** (series string) An optional parameter which replaces the {{strategy.order.alert_message}} placeholder when it is used in the "Create Alert" dialog box's "Message" field.