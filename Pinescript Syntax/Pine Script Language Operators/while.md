# while

The [[while]] statement allows the conditional iteration of a local code block.

```js
variable_declaration = while boolean_expression
  …  
  continue  
  …  
  break  
  …  
  return_expression
```

## where:

**variable_declaration** - An optional variable declaration. The `return expression` can provide the initialization value for this variable.

**boolean_expression** - when true, the local block of the `while` statement is executed. When false, execution of the script resumes after the `while` statement.

**continue** - The `continue` keyword causes the loop to branch to its next iteration.

**break** - The `break` keyword causes the loop to terminate. The script's execution resumes after the `while` statement.

**return_expression** - An optional line providing the `while` statement's returning value.

## Example

```js
//@version=5
indicator("while")
// This is a simple example of calculating a factorial using a while loop.
int i_n = input.int(10, "Factorial Size", minval=0)
int counter   = i_n
int factorial = 1
while counter > 0
	factorial := factorial * counter
	counter   := counter - 1

plot(factorial)
```

## Remarks

The local code block after the initial `while` line must be indented with four spaces or a tab. For the `while` loop to terminate, the boolean expression following `while` must eventually become false, or a `break` must be executed.