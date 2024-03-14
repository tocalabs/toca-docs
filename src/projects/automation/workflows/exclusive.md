# Exclusive Node

An exclusive node allows you to put a decision point in your workflow. You can place conditions on each path branching out from the exclusive node and the it will only execute paths where the condition is `true`.

The conditions can use workflow inputs, activity outputs and datastore variables in them.

They can also be used to introduce loops into your workflow as well as error handling.

There are several key operators you can use to create your conditions:

| Operator | Description |
| --- | --- |
| `==` | If left hand side equals right hand side then it is true |
| `!=` | If left hand side does not equal right hand side then it is true |
| `<` | If left hand side is less than right hand side then it is true |
| `>` | If left hand side is greater than right hand side then it is true |
| `<=` | If left hand side is less than or equal to right hand side then it is true |
| `>=` | If left hand side is greater than or equal to right hand side then it is true |
| `&&` | AND - allows you to chain conditions together. Will be true if ALL conditions are true |
| `\|\|` | OR - allows you to chain conditions together. Will be true if any of the conditions are true |
| `!` | NOT - allows you to reverse the value of a statement e.g. `false == !true` would evalutate to true |
| `else` | A special operator that can be used instead of specifying a condition to denote that this path should be used if no other conditions are true |

Additionally, brackets `( )` can be used to group conditions together.

## Examples

The example below checks if a datachip is equal to "failed".

:datachip-variable[Status]{type="String"} == "failed"

The example below checks if a datachip is less than 10.

:datachip-variable[LoopCount]{type="Number"} < 10

The example below checks if a datachip is less than 10 and the activity did not fail.

:datachip-variable[LoopCount]{type="Number"} < 10 && :datachip-action[activityFailed]{type="Boolean"} != false

The example below checks if a datachip is either == "JSON" or if the datachip is equal to "HTML".

:datachip-variable[ContentType]{type="String"} == "JSON" || :datachip-variable[ContentType]{type="String"} == "HTML"
