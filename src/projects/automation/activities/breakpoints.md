# Automation Breakpoints

Breakpoints are markers which denote a point where an automation should pause. When an activity hits a breakpoint you should be able to either resume from that point or stop the automation entirely. Adding a breakpoint is as simple as clicking the hollow red dot which appears when hovering your cursor over an action. An active breakpoint will appear as a filled red dot.

All breakpoints in the activity will be visible inside the breakpoints tab (in the same section as the console). This also allows you to temporarily deactivate breakpoints without fully deleting them.

Breakpoints are particularly useful if you need data from actions at the beginning of your activity to be in context whilst you continue to develop. They are also a useful tool for debugging your activities in a step by step manner. A breakpoint nested underneath a looping action e.g 'repeat', will continue to pause on each iteration of that loop.

> N.B. Breakpoints will be ignored when an activity is run in a workflow
