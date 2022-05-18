# bgcolor()

## PineScript Examples

```Javascript
//@version=5

indicator("bgcolor example", overlay=true)
bgcolor(close < open ? color.new(color.red,70) : color.new(color.green, 70))
```

