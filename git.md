# Git Repo Workflow Strategy
The following document contains information and tutorials for contributing to deep.ditch repositories.

## Staying In Sync
It is important to ensure that you have pulled the most recent updates from the repository before contributing. Resolving merge conflicts becomes increasingly difficult if you begin making changes without being up to date. The following commands will pull recent commits into your local master branch:
```
git checkout master
git pull origin master
```
Similarly, any branch can be updated with the following: 
```
git checkout [branchname]
git pull origin [branchname]
```
While developing within a separate [branch](#branching), it may be a good idea to periodically [merge commits added to master into your branch](#merging-changes-into-your-branch). Keeping your branch in sync will limit merge conflicts.

## Branching
A new branch should be made from the master branch when working on a feature or bug. Be sure to [pull recent changes](#staying-in-sync) before creating a branch. Direct commits to master should be avoided except during the initial stages of development.

### Features
New features should be added in feature branches. The following commands will create a new branch from master.
```
git checkout master
git checkout -b feature/[BriefDescriptionOfFeature]
```
If a feature requires significant code changes and multiple developers, it may be a good idea to create sub feature branches.
```
git checkout feature/[...]
git checkout -b feature/[BriefDescriptionOfSubFeature]
```

### Bugs
Similarly, bug fixes should be completed in a separate branch. 
```
git checkout master
git checkout -b bug/[BriefDescriptionOfBug]
```

## Making Changes
Once you have created a branch, changes can be made within that branch and committed to the repository
```
git checkout [YourBranchName]
~~~ Make changes locally ~~~
git commit -m "[descriptive commit message]"
git push origin [YourBranchName]
```
Commit messages should be informative and descriptive. Examples of unacceptable commit messages:
* "changes"
* "bug fix"
* "some work"

## Moving Your Changes To Master
Once you have finished making your changes, your code will need to be reviewed and merged into the master branch. 

### Merging Changes Into Your Branch
If commits have been made to master since you created your branch, you will need to merge those changes into your branch and resolve any merge conflicts. Run the following commands to merge changes into your branch:
```
git checkout [YourBranchName]
git pull origin master
```
If there are any merge conflicts, git will alert you. I recommend using [KDiff3](http://kdiff3.sourceforge.net/) to aid in resolving conflicts. Be sure to test your code after resolving conflicts.

### Creating a Pull Request
Once you have resolved any merge conflicts, you can initiate a pull request in github by clicking the "New Pull Request" button. Your pull request can than be either accepted or rejected, ideally by a different team member. Further changes can continue to be made on your branch while the pull request is still open. Additional commits to your branch will automatically be incorporated into the open pull request. If new commits are added to master after you have opened your pull request, you will again need to [merge those changed into your branch](#merging-changes-into-your-branch).
