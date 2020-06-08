# nbdev_playground

The purpose of this repo is to explore a data science workflow with nbdev and reviewed pull requests on GitHub.

## What has already been done
Some steps have already been executed with nbdev.  First, a new repository was created from the command line using `nbdev_new`.  This populates a new directory with all of the files required for an nbdev project.  Secondly, the command line function `nbdev_install_git_hooks` was run, which enforces that your notebooks are both trusted and removes unwanted metadata (e.g., execution counts).  The relevant git hooks are now in the repo.  Lastly, the `settings.ini` file was filled out.  This essentially consists of filling out all of the commented fields in the first section of the file.  Additionally, a `no_test` flag was added to the line `tst_flags` (which was also uncommented), so that some analysis cells can be ignored.

Additionally, one notebook `00_core.ipynb` has already been filled out and a function implemented to generate the `nbdev_playground` module.  This contains all of the project source, extracted from the notebook cells.

## Your workflow
You should have already tried out the tutorials on nbdev to understand what is the general workflow of nbdev. 

### Feature branching workflow (GitHub Flow)
After you've cloned this repository, create a new git branch and check it out.  You can create a branch called `new_branch` using the following command.  Note that you should change the name of `new_branch` to something more descriptive:

`git checkout -b new_branch`

Now, you should add a notebook with at least one exported cell, one markdown cell, and one `no_test` cell.  Make sure you run `notebook2script()` in your notebook or run `nbdev_build_lib` at the command line in order to make sure that your built modules will match what is exported.  *Before running either of these functions, MAKE SURE YOUR HAVE SAVED YOUR NOTEBOOK*.

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




