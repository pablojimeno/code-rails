### Failure:

    Expected "...<snip>..." to include "Project could not be saved".
  - Right, we didn't set a flash message to indicate the failure, so let's do that now.
  - Just add a line right above the render statement:

        flash.now[:error] =  "Project could not be saved."
