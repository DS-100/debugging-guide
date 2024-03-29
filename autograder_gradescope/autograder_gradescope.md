---
title: Autograder and Gradescope
format:
  html:
    toc: true
    toc-depth: 5
    toc-location: right
    code-fold: false
    theme:
      - cosmo
      - cerulean
    callout-icon: false
jupyter:
  jupytext:
    text_representation:
      extension: .qmd
      format_name: quarto
      format_version: '1.0'
      jupytext_version: 1.16.1
  kernelspec:
    display_name: Python 3 (ipykernel)
    language: python
    name: python3
---

<details>
    <summary>Citation</summary>
    Many of these common questions were taken and modified from the UC San Diego course DSC 10: Principles of Data Science and their [debugging guide](https://dsc10.com/debugging/).
</details>

## Autograder

### Understanding autograder error messages 
When you pass a test, you'll see a nice message and a cute emoji!

<center><img src = "passing_autograder.png" width = "200"></img></a></center>

When you don't, however, the message can be a little confusing. 

<center><img src = "autograder_error.png" width = "600"></img></a></center>
<br>

The best course of action is to find the test case that failed and use that as a starting point to debug your code. 

<center><img src = "autograder_error_annot.png" width = "700"></img></a></center>

In the example above, we see that the test case in green, `max_swing in set(bus['name'])`, is not passing. The actual output (in blue) is often hard to parse, so the best course of action is to: 

1. Make a new (temporary) cell after the `grader.check(...)` cell. Please do not make a new cell in between the given code cell and the `grader.check(...)` cell, as it could mess with the results. 
2. Copy and paste the failing test case into your temporary cell and run it. 

    a. If it's giving you an error like in the example above, look at the last line of the error and use the Debugging Guide's search functionality in the top left menu to find the corresponding guide. 
    b. If it's not giving you an error, it'll likely give you an output like `False`. This means that your code does not cause an error (yay!), but it returns an incorrect output. In these casses, inspect each individual element of the test case. The example above checks if `max_swing` is in `set(bus['name'])`, so it might be a good idea to display both variables and do a visual check. 
    c. If you're still having issues, post on Ed!
3. After your `grader.check(...)` passes, feel free to delete the temporary cell.

### Why do I get an error saying "`grader is not defined`"?
If it has been a while since you’ve worked on an assignment, the kernel will shut itself down to preserve memory. When this happens, all of your variables are forgotten, including the grader. That’s OK. The easiest way to fix this is by [restarting your kernel and rerunning all the cells](https://ds100.org/debugging-guide/jupyter101/jupyter101.html#restarting-kernel). To do this, in the top left menu, click `Kernel` -> `Restart and Run All Cells`.

### I’m positive I have the right answer, but the test fails. Is there a mistake in the test?
While you might see the correct answer displayed as the result of the cell, chances are your solution isn’t being stored in the answer variable. Make sure you are assigning the result to the answer variable and that there are no typos in the variable name. Finally, [restart your kernel and run all the cells in order](https://ds100.org/debugging-guide/jupyter101/jupyter101.html#restarting-kernel): `Kernel` -> `Restart and Run All Cells`.

### Why does the last `grader.export` cell fail if all previous tests passed?
This can happen if you “overwrite” a variable that is used in a question. For instance, say Question 1 asks you to store your answer in a variable named `stat` and, later on in the notebook, you change the value of `stat`; the test right after Question 1 will pass, but the test at the end of the notebook will fail. It is good programming practice to give your variables informative names and to avoid repeating the same variable name for more than one purpose.

### Why does a notebook test fail now when it passed before, and I didn’t change my code?
You probably ran your notebook out of order. [Re-run all previous cells](https://ds100.org/debugging-guide/jupyter101/jupyter101.html#running-cells) in order, which is how your code will be graded.

## Gradescope

When submitting to Gradescope, there are often unexpected errors that make students lose more points than expected. Thus, it is imperative that you **stay on the submission page until the autograder finishes running**, and the results are displayed. 

### Why did a Gradescope test fail when all the Jupyter notebook’s tests passed?
This can happen if you’re running your notebook’s cells out of order. The autograder runs your notebook from top-to-bottom. If you’re defining a variable at the bottom of your notebook and using it at the top, the Gradescope autograder will fail because it doesn’t recognize the variable when it encounters it.

This is why we recommend going into the top left menu and clicking `Kernel` -> `Restart` -> `Run All`. The autograder “forgets” all of the variables and runs the notebook from top-to-bottom like the Gradescope autograder does. This will highlight any issues. 

Find the first cell that raises an error. Make sure that all of the variables used in that cell have been defined above that cell, and not below.

### Why do I get a `NameError: name ___ is not defined` when I run a grader check?
This happens when you try to access a variable that has not been defined yet. Since the autograder runs all the cells in-order, if you happened to define a variable in a cell further down and accessed it before that cell, the autograder will likely throw this error. Another reason this could occur is because the notebook was not saved before the autograder tests are run. When in doubt, it is good practice to restart your kernel, run all the cells again, and save the notebook before running the cell that causes this error.



### My autograder keeps running/timed out

If your Gradescope submission page has been stuck running on this page for a while: 

<center><img src = "gradescope_loading.png" width = "350"></img></a></center>

or if it times out:

<center><img src = "gradescope_timeout.png" width = "650"></img></a></center>

it means that the Gradescope autograder failed to execute in the expected amount of time. This could be due to an inefficiency in your code or a problem on Gradescope's end, so we recommend resubmitting and letting the autograder rerun. **It is your responsibility to ensure that the autograder runs properly**, and, if it still fails, to follow up by making a private Ed post. 
