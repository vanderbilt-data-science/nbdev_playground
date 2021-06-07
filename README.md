[![Open In Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/vanderbilt-data-science/nbdev_playground)
# nbdev_playground
> A template repo for practicing collaboration with Jupyter notebooks

This repository has been generated from the nbdev_template from nbdev's repository at this location: https://github.com/fastai/nbdev_template .  Visit this link to create your own project using the template or for tips in troubleshooting as you do this on your own!

## Workshop scope
The objectives of this workshop are to provide the following:
* Brief motivation of tools to collaborate with Jupyter notebooks
* Brief hands-on use of selected nbdev command line tools
* Resolving merge conflicts with nbdev

We'll be doing this using this repo in Google Colab to standardize the environment for everyone.  Your workflow on your local machine will look slightly different, but the general set of steps to use nbdev will be very similar.  These will be discussed during the workshop.

Additionally, the nbdev package provides a tremendous amount of functionality which all cannot be addressed during this workshop.  Although many topics will be addressed, this workshop will focus primarily on collaboration, specifically through the use of building modules and using the command line merge conflict resolution.  Additionally, you'll need to be familiar with the tool set and how to use Google Colab with Google Drive.  The required preparation of the workshop is outlined in the section below.

## Workshop preparation
Come to the workshop armed with knowledge and prepared to collaborate!  During this workshop, we'll focus on building modules, so make sure to complete the sections specifically related to this activity.  Building docs will not be focused on during this workshop, but please feel free to explore this functionality if time allows.  Before coming to the workshop, complete the following assignments:
1.  Add some of the challenges you've encountered _collaborating with others_ using Jupyter notebooks (e.g., ever had a merge conflict?) here: https://docs.google.com/document/d/1vbY397SLdcXd8ySR9nf1fy37qK3zRCsG1stXY0IOJqQ/ 
2.  Read over the nbdev introduction (https://nbdev.fast.ai/), particularly examining the features.  Based on your answers from 1, identify some features of nbdev which may assist in resolving some of your issues.  Add this to the relevant section in the shared document.
3. Familiarize yourself with using nbdev in Google Colab.  Follow the instructions here: https://nbdev.fast.ai/tutorial_colab.html up to and including `Writing a New Module and the Setup Cell for Each Notebook`.
4. The `Writing a New Module and the Setup Cell for Each Notebook` contains a link to the general nbdev tutorial.  Follow the link (https://nbdev.fast.ai/tutorial.html) and complete the tutorial.  Make sure to complete everything up to (but not necessarily including) `View Docs Locally`.

## During the workshop
The activities of the workshop will be as follows:
* Brief discussion of collaborating with Jupyter notebooks
* Using the nbdev_playground template repo on Google Colab
* Brief hands-on walkthrough of generation of modules with nbdev
* Pushing to the GitHub repo
* Resolving merge conflicts using nbdev

## In-workshop activity of resolving merge conflicts
1. Choose a person whose repo will be used (Person 1).
2. Person 1:  add Person 2 as a collaborator on your GitHub project.
3. Person 2.  Clone Person 1's repo in Google Colab.
4. Person 1, Person 2:
    * P1: Create a branch `file_end`.  Change the function `append_file_ending` to append `.txt`.  Build the new module.  Commit these changes to the `file_end` branch.  Push this to GitHub.
    * P2: Create a branch `fix_file_end`. Change the function `append_file_ending` to append `.csv`.  Build the new module.  Commit these changes to the `fix_file_end` branch.  Push this to GitHub.
5.  Person 1, Person 2:  Create pull requests on GitHub on your own created branch.
6.  Person 1 and Person 2:  Review the PR on `file_end` branch.  If everything looks good, Person 1 - merge this into master.
7.  Person 1 and Person 2:  Inspect the PR on the `fix_file_end` branch.  Confirm that the code looks good.  But, it looks like there would be a merge conflict if you merged your current branch into master.  Since your objective is to merge into master, you can actually master into your current branch locally and push the changes.  Since this is Person 2's PR, they will resolve the merge conflict.
8.  Person 2: Switch to the master branch.  Pull from GitHub to update your local version of Master.  Switch over to your `fix_file_end` branch.  Pull from GitHub to make sure this is the updated version (it should be.)  Now, type `git merge master`.  Looks like there are some merge conflicts.  Type `nbdev_fix_merge 00_core.ipynb`.  Looks like you need to fix this manually.
9.  Open the conflicted notebook.  Remove Person 1's changes along with all `===`, `<<<`, and `>>>` changes.  Save your notebook.  Type `nbdev_build_lib`.  Commit the changes to complete the merge.  Push your updated branch to GitHub.
10.  Notice that the branch has been updated on GitHub and it looks like you'll be able to merge.  Merge in your PR.

## Troubleshooting Tips
This advice is from the nbdev_template repository:
-  Make sure you are using the latest version of nbdev with `pip install -U nbdev`
-  If you are using an older version of this template, see the instructions above on how to upgrade your template. 
-  It is important for you to spell the name of your user and repo correctly in `settings.ini` or the website will not have the correct address from which to source assets like CSS for your site.  When in doubt, you can open your browser's developer console and see if there are any errors related to fetching assets for your website due to an incorrect URL generated by misspelled values from `settings.ini`.
-  If you change the name of your repo, you have to make the appropriate changes in `settings.ini`
-  After you make changes to `settings.ini`, run `nbdev_build_lib && nbdev_clean_nbs && nbdev_build_docs` to make sure all changes are propagated appropriately.

