# Exclusive Node

An exclusive node allows you to put a decision point in your workflow. You can place conditions on each path branching out from the exclusive node and the it will only execute paths where the condition is `true`.

The conditions can use workflow inputs, activity outputs and datastore variables in them.

They can also be used to introduce loops into your workflow as well as error handling.

There are several key identifiers you can use to create your conditions:

| Identifier | Description |
| --- | --- |
| `&&` | AND |
