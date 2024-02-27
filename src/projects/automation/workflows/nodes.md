 # Workflow Nodes

 Workflow nodes are the steps that define what is run during a workflow and what order it is run in.

 There are 3 different types of item that you can place in a workflow and these are:
 - Nodes - Steps that control the flow of the workflow
 - Activities - GUI or Stateless automation tasks
 - Connectors - External access to running the workflow

 Nodes are mainly used for defining the direction of execution in a workflow such as where to start, where to finish and where to branch off.
Nodes are what also allow you to define flow control such as loops and error handling at a workflow level.

 | Node | Description |
 | --- | --- |
 | Start | Defines the start point of your workflow. _Can only be used once_ |
 | End | Defines the finishing point of your workflow. _Can be used multiple times_ |
 | Exclusive | Defines a decision point in the workflow |
 | Trigger | Allows you to start another workflow |
 | Label | Does not affect behaviour of workflow but allows you to add comments to your workflow |

There are some basic limitations that apply to the nodes above.
1. A Start node can only point to one other node
2. An End node can only be pointed to by one other node
