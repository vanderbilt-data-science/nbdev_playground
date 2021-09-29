[![Open In Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/vanderbilt-data-science/nbdev_playground)
# nbdev_playground
> A template repo for practicing collaboration with Jupyter notebooks

This repository has been generated from the nbdev_template from nbdev's repository at this location: https://github.com/fastai/nbdev_template .  Visit this link to create your own project using the template or for tips in troubleshooting as you do this on your own!

# Workshop scope
The nbdev package provides a tremendous amount of functionality for exploratory programming and collaboration using Jupyter notebooks.  These all cannot be addressed during this workshop.  Although many topics will be addressed, this workshop will focus primarily on collaboration, specifically through the use of building modules and using the command line merge conflict resolution.  The schedule for the workshop is outlined below.  

**Day 1 - Collaborating with nbdev: Code reuse across notebooks**  
* Brief motivation of tools to collaborate with Jupyter notebooks
* Brief hands-on use of selected nbdev command line tools  

**Day 2 - Collaborating with nbdev: Resolving merge conflicts**  
* Resolving merge conflicts with nbdev

You'll be using your own local machine, so make sure you have the pre-requisites below installed!

# Day 1: Code reuse and modularization
Come to the workshop armed with knowledge and prepared to collaborate!  During this workshop, we'll focus on motivating nbdev and packaging notebook code for reusability across notebooks.  Prior to coming to the workshop, make sure that you have the following available:
## Pre-requisites:
### GitHub account and Personal Access Token
One of the first things we'll do is create our own repository and clone it!  To follow along during the workshop, you'll need a GitHub account to do this.  You can sign up for GitHub here: [https://github.com](https://github.com), and click the green button to sign up.

You will also **need** a personal access token for cloning the repository.  Make sure that after you create the token, you save it somewhere in case you need it again.  Also, make sure you _at least_ click **repo** (and all of the sub-permission of repo) when assigning your permissions.  Here are instructions on how to create the token from GitHub: https://docs.github.com/en/authentication/keeping-your-account-and-data-secure/creating-a-personal-access-token .  Note that you can also create an SSH key, and if you've done this for GitHub in the past on your current computer, you don't need to do this again now.  If you're not sure, create a personal access token.

### Installation of Jupyter notebook and Python
You'll need to be able to use Jupyter notebooks during this session.  The easiest way to get access to everything you'll need is through installing Anaconda.  You can do this by following the instructions here: https://www.anaconda.com/products/individual or if that does not show the your correct operating system, you can pick the correct one from the list here: https://docs.anaconda.com/anaconda/install/

### Installing nbdev
We'll be working with nbdev today!  Once you have an installation of Anaconda or access to `pip` through a Python installation, you can install it using the instructions here: https://nbdev.fast.ai/tutorial.html#Install-nbdev

# Day 2: Resolving merge conflicts with nbdev using GitHub Flow
## Missed Day 1?
If you missed Day 1, you'll need to familiarize yourself with nbdev.  Perform the following activities to get yourself caught up:
1.  Add some of the challenges you've encountered _collaborating with others_ using Jupyter notebooks (e.g., ever had a merge conflict?) here: https://docs.google.com/document/d/1iOCXTNAsiYZmWVBhcuJS09qeGdZsxcEbUC7dlS11bXw/edit  
2.  Read over the nbdev introduction (https://nbdev.fast.ai/), particularly examining the features.  Based on your answers from 1, identify some features of nbdev which may assist in resolving some of your issues.  Add this to the relevant section in the shared document.
3. Make sure you have the applicable pre-requisites from Day 1 installed.
4. Familiarize yourself with nbdev.  Follow the link (https://nbdev.fast.ai/tutorial.html) and complete the tutorial.  Make sure to complete everything up to (but not necessarily including) `View Docs Locally`.

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

## Gemfiles and Security
When using docs, you'll notice Gemfiles which allow you to run Jekyll locally (described below).  Sometimes, this introduces security issues if you commit them to the repository.  On this topic, this advice is from the nbdev_template repository:
### Previewing Documents Locally 

It is often desirable to preview nbdev generated documentation locally before having it built and rendered by GitHub Pages.  This requires you to run Jekyll locally, which requires installing Ruby and Jekyll. Instructions on how to install Jekyll are provided [on Jekyll's site](https://jekyllrb.com/). You can run the command `make docs_serve` from the root of your repo to serve the documentation locally after calling `nbdev_build_docs` to generate the docs. 

In order to allow you to run Jekyll locally this project contains manifest files, called Gem files, that specify all Ruby dependencies for Jekyll & nbdev. **If you do not plan to preview documentation locally**, you can choose to delete `docs/Gemfile` and `docs/Gemfile.lock` from your nbdev project (for example, after creating a new repo from this template). 

