# Error handling

When performing an automated task, sometimes things go wrong. As there often won't be a human around to handle this eventuality, it's important that we design our automation to handle error cases accordingly.

## Unrecoverable errors

Often, it is the case that, when an error occurs, we simply want our automation to terminate. Toca assumes that by default, we want to do this after an error occurs in any action in an activity, and any activity in a workflow. 

## Recoverable errors

### Actions

If we deem an error to not require that its entire activity/workflow terminates, we can set the "Fail on error" boolean of an action to False (this defaults to True). The next action can use the $$LastActionStatus$$ action result to respond to the error.

### Activities

In the workflow designer, activities also have "Fail on error" booleans. 
  - :docs-link[Unrecoverable Errors]{id="book/error_handling/unrecoverable_errors"}
  - :docs-link[Recoverable Errors]{id="book/error_handling/recoverable_errors"}
  - :docs-link[To fail or not to fail?]{id="book/error_handling/fail_or_not"}
  - :docs-link[Handling Errors in Apps]{id="book/error_handling/app_errors"}
