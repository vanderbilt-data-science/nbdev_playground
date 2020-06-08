# nbdev_playground

The purpose of this repo is to explore a data science workflow with nbdev and reviewed pull requests on GitHub.

## What has already been done
Some steps have already been executed with nbdev.  First, a new repository was created from the command line using `nbdev_new`.  This populates a new directory with all of the files required for an nbdev project. Secondly, the `settings.ini` file was filled out.  This essentially consists of filling out all of the commented fields in the first section of the file.  Additionally, a `no_test` flag was added to the line `tst_flags` (which was also uncommented), so that some analysis cells can be ignored.

Additionally, one notebook `00_core.ipynb` has already been filled out and a function implemented to generate the `nbdev_playground` module.  This contains all of the project source, extracted from the notebook cells.  There may be other notebooks added as well.

## Your workflow
You should have already tried out the tutorials on nbdev to understand what is the general workflow of nbdev.  If you haven't you'll need to make sure you have an environment with `nbdev` already installed.  Your life will be better if you create a pip or conda virtual environment prior to installing `nbdev`.  Make sure to activate your nbdev conda virtual environment before moving forward.

### Feature branching workflow (GitHub Flow)
After you've cloned this repository, `cd` inside the repo and run `nbdev_install_git_hooks`.  This will create some git hooks that remove unwanted metadata (e.g., execution counts) and also make your notebooks trusted.  Then, create a new git branch and check it out.  You can create a branch called `new_branch` using the following command.  Note that you should change the name of `new_branch` to something more descriptive:

`git checkout -b new_branch`

Now, you should add a notebook with at least one exported cell, one markdown cell, and one `no_test` cell.  *Make sure your save your notebook.*  **Is your notebook saved?  Save it.**  Now, go back to the command line and type `nbdev_build_lib`.  Thsi will make sure that your built modules will match what's in your notebook cells.

This should have made some changes in both the built module and in your new notebook.  Type `git status` to find out exactly the files that have changed.

Now, you'll add these files to the git staging area by using the following command:

`git add filename_1 filename_2 filename_3`

nbdev also generates some other files that we don't particularly need for the analysis.  Now, commit your files to the local repo using a descriptive message (e.g., `added functions for numerical analysis` below) using the command:

`git commit -m "added functions for numerical analysis"`

Now, push your branch to the remote repo using the following command:

`git push origin new_branch`

substituting whatever the name of the branch in that you created into `new_branch`.

### GitHub and Pull Requests
Now, you'll create a pull request.  Go to the GitHub for this repository and you should see a message indicating that you've pushed a new branch, and click the green button for creating a pull request.  In the first empty cell, write a description of what you've done.  Your GitHub is set up so that one reviewer is required to look at the pull requests and give approval to merge it in.  In the sidebar, indicate the reviewer and submit your pull request.

### Collaboration and merge conflicts
It will be the case that while you're working on your own branch, someone else will submit a pull request for review.  If this pull request is approved, this will change `master`, making it different than the branch that you're working on.  You always want to work with the most current code.  The best time to update your code is when you've committed all of your changes and your working tree is clean.  If you're in the midst of working and have uncommitted changes, you can run `git stash`, and then execute the following steps.  After you're finished with these steps, you can then run `git stash pop` to retrieve your uncommitted changes.

To update your code to the most recent `master` version, first, make sure you're on the branch you've been developing on (e.g. `new_branch`); you can check what branch you're on by typing `git branch`.  If you're not on your own branch, type `git checkout new_branch` (or whatever the name of your branch is) and type `git pull origin master`.  This will pull down the code on master from the repo.  Git will now tell you if you have merge conflicts.  If it seems that you do, run `git status`, and look at where it says `both modified:`.  If the error **only** occurs in any of the auto-generated modules (e.g., `nbdev_playground/_nbdev.py`) or python files, simply run `nbdev_build_lib`.  This will resolve your issues, updating the modules with the code from the notebooks that you've pulled.

If the problem is in the notebooks, first try to run `nbdev_fix_merge notebook_name`, where `notebook_name` is the name of the notebook which has the merge conflicts.  This will assist in resolving conflicts at the notebook level.

Once you've resolved the conflicts, you can now add a merge commit.  Follow the normal steps for staging and commiting files (e.g., `git add filename1 filename2`, `git commit -m "msg"`).  If you're done with all your work, type `git push origin new_branch` (substituting the name of your branch in for `new_branch`), which will now push it up to the repo.

## Troubleshooting
**My build failed in the Actions.  What should I do?**  Don't worry, this happens to everyone.  Go to the `Actions` tab, click on your commit, and in the resulting window, click on `build` in the side bar.  If it failed in the diff, go back to your local Jupyter lab and save the notebooks that you were working on and any other notebooks that you've accidentally opened or run.  Run `nbdev_build_lib` at the command line.  Additionally, you can run `nbdev_diff_libs` to see if anything is produced which would cause your build to fail.  If this function generates output, you'll need to go back and save/fix the notebooks of interest and re-run `nbdev_build_lib`.

If it fails in the tests, either it truly failed a test or you might have left a cell in the notebook that you didn't want to run as a test.  Go back and look at your notebook; all non-flagged cells are run as tests.  Make sure you add the custom flag `no_test` to all cells you don't want to evaluate during the GitHub Action.

**The build still fails!!  What is going on?!**  If the step above didn't fix things for you, go and look at your built modules.  Are there any old modules there that shouldn't be there?  Delete them.  This can occur if you made a notebook, ran it and built some modules, and then went on to delete or rename the module or notebook to something else.  The old module will still be there, but there will be no matching notebook.  This may cause the build to fail.

**When I try to run nbdev commmand line functions, it says nbdev not found.  What's up?**  Sounds like you're not in an environment which has nbdev loaded.  If you've already started Jupyter notebook or Jupyter lab, end the session and then start up in your nbdev environment.



