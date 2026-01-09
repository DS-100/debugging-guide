---
title: Autograder and Gradescope / Pensieve
---

:::{seealso} Citation
    Many of these common questions were taken and modified from the UC San Diego course DSC 10: Principles of Data Science and their [debugging guide](https://dsc10.com/debugging/).
:::

## Autograder

### Understanding autograder error messages

When you pass a test, you'll see a nice message and a cute emoji!

```{image} images/passing_autograder.png
:width: 200
:alt: Screenshot of a grader cell for question q2a with cell ouput 'q2a passed'
```

When you don't, however, the message can be a little confusing.

```{image} images/autograder_error.png
:width: 600
:alt: Example of a cell output for a failing autograder test showing what test failed, what the code that was evaluated was, the expected output, and an error that was raised during the course of the test.
```

The best course of action is to find the test case that failed and use that as a starting point to debug your code.

```{image} images/autograder_error_annot.png
:width: 700
:alt: An annotated version of the previous image which includes the note 'The most useful error message is usually at the bottom'
```

In the example above, we see that the test case in green, `max_swing in set(bus['name'])`, is not passing. The actual output (in blue) is often hard to parse, so the best course of action is to:

1. Make a new (temporary) cell after the `grader.check(...)` cell. Please do not make a new cell in between the given code cell and the `grader.check(...)` cell, as it could mess with the results.
2. Copy and paste the failing test case into your temporary cell and run it.

   a. If it's giving you an error like in the example above, look at the last line of the error and use the Debugging Guide's search functionality in the top left menu to find the corresponding guide.
   b. If it's not giving you an error, it'll likely give you an output like `False`. This means that your code does not cause an error (yay!), but it returns an incorrect output. In these casses, inspect each individual element of the test case. The example above checks if `max_swing` is in `set(bus['name'])`, so it might be a good idea to display both variables and do a visual check.
   c. If you're still having issues, post on Ed!

3. After your `grader.check(...)` passes, feel free to delete the temporary cell.

### Why do I get an error saying "`grader is not defined`"?

If it has been a while since you’ve worked on an assignment, the kernel will shut itself down to preserve memory. When this happens, all of your variables are forgotten, including the grader. That’s OK. The easiest way to fix this is by [restarting your kernel and rerunning all the cells](#restarting-kernel). To do this, in the top left menu, click `Kernel` -> `Restart and Run All Cells`.

### I’m positive I have the right answer, but the test fails. Is there a mistake in the test?

While you might see the correct answer displayed as the result of the cell, chances are your solution isn’t being stored in the answer variable. Make sure you are assigning the result to the answer variable and that there are no typos in the variable name. Finally, [restart your kernel and run all the cells in order](#restarting-kernel): `Kernel` -> `Restart and Run All Cells`.

### Why does the last `grader.export` cell fail if all previous tests passed?

This can happen if you “overwrite” a variable that is used in a question. For instance, say Question 1 asks you to store your answer in a variable named `stat` and, later on in the notebook, you change the value of `stat`; the test right after Question 1 will pass, but the test at the end of the notebook will fail. It is good programming practice to give your variables informative names and to avoid repeating the same variable name for more than one purpose.

### Why does a notebook test fail now when it passed before, and I didn’t change my code?

You probably ran your notebook out of order. [Re-run all previous cells](#running-cells) in order, which is how your code will be graded.

## Gradescope/Pensieve

When submitting to Gradescope or Pensieve, there are often unexpected errors that make students lose more points than expected. Thus, it is imperative that you **stay on the submission page until the autograder finishes running**, and the results are displayed.

### Why did a Gradescope/Pensieve test fail when all the Jupyter notebook’s tests passed?

This can happen if you’re running your notebook’s cells out of order. The autograder runs your notebook from top-to-bottom. If you’re defining a variable at the bottom of your notebook and using it at the top, the Gradescope/Pensieve autograder will fail because it doesn’t recognize the variable when it encounters it.

Another scenario where this can happen is if you defined a variable in an earlier cell but later changed its name or deleted it. While your current session's kernel will "remember" the variable, the Gradescope/Pensieve autograder will not, because it runs the notebook from top to bottom with no variables pre-stored. As a result, it will not recognize the variable if it has been deleted or renamed, and will throw an error.

The third scenario where this can happen is if you do not save your notebook before running the final export cell, which generates a zip file containing your notebook and the necessary files. If you run the export cell without saving, the autograder will not have access to the most recent version of your notebook, which can lead to unexpected errors. It will rely on the state of the notebook at the time of the last save, so any changes made afterward will not be reflected in the autograder’s execution.

This is why we recommend first saving and then going into the top left menu and clicking `Kernel` -> `Restart` -> `Run All`. The autograder “forgets” all of the variables and runs the notebook from top-to-bottom like the Gradescope/Pensieve autograder does. This will highlight any issues.

Find the first cell that raises an error. Make sure that all of the variables used in that cell have been defined above that cell, and not below.

### Why do I get a `NameError: name ___ is not defined` when I run a grader check?

This happens when you try to access a variable that has not been defined yet. Since the autograder runs all the cells in-order, if you happened to define a variable in a cell further down and accessed it before that cell, the autograder will likely throw this error. Another reason this could occur is because the notebook was not saved before the autograder tests are run. When in doubt, it is good practice to restart your kernel, run all the cells again, and save the notebook before running the cell that causes this error.

### Why do I see multiple `NameError: name ___ is not defined` errors for all questions after a certain point on Gradescope/Pensieve?

This can happen if you import external packages when you are not instructed to do so. The base image on Gradescope/Pensieve includes only a specific list of pre-installed packages, defined by the course staff in the autograder. If you import a package that is not on this list, it will not be available to the autograder, even if you download the package correctly on your local Jupyter notebook environment. As a result, it will first encounter a `ModuleNotFoundError` when trying to import the package (though this error may not be shown to you), and then a `NameError` for every question afterward. Although this behavior is unintuitive, it’s a limitation of the autograder—only course staff can view certain output messages from your notebook to prevent cheating. If you encounter this issue, review your notebook’s imports and ensure you are not using any packages not included in the autograder environment.

### My autograder keeps running/timed out

If your Gradescope submission page has been stuck running on this page for a while:

```{image} images/gradescope_loading.png
:width: 359
:alt: Autograder Results. The autograder hasn't finish running yet.
```

or if it times out:

```{image} images/gradescope_timeout.png
:width: 650
:alt: Autograder Results. In a red box 'The autograder failed to respond in the expected amount of time. If the autograder continues to fail, contact your course staff for help in debugging this issue. Make sure to include a link to this page so they can help you most effectively.
```

it means that the Gradescope autograder failed to execute in the expected amount of time. TThis could be due to an inefficiency in your code or an issue on Gradescope's end, so we recommend resubmitting and allowing the autograder to rerun. If the issue persists after a few attempts, you may need to investigate your code for inefficiencies.

For example, if you rerun all cells in your Jupyter notebook and notice that some cells take significantly longer to run than others, you might need to optimize those cells. Keep in mind that the time it takes to run all tests in your Jupyter notebook is not equivalent to the time it takes on Gradescope/Pensieve. However, it is proportional—if your notebook runs slowly on Datahub, it will likely run even more slowly on Gradescope/Pensieve, as the difference in runtime is amplified.

**It is your responsibility to ensure that the autograder runs properly**, and if it still fails, you should follow up by making a private Ed post.
