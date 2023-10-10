# Rebasing
## Contents
- [Introduction](#introduction)
- [Warning](#warning)
- [Examples](#examples)
    - [Simple example](#simple-example)
    - [Interactive](#interactive)
    - [Multiple branches](#multiple-branches)
- [Pros and Cons of Rebasing](#pros-and-cons-of-rebasing)
- [Merge vs Rebase](#merge-vs-rebase)
- [Sources](#sources)


## Introduction
  * Git rebase is a command used to modify the commit history of a branch. 
It allows the users to reorganize and streamline the commit history by moving, 
combining, or editing commits. Rebase is commonly used to integrate changes 
from one branch into another, typically to update a local feature branch 
with changes in the main development branch. 
  
  * The main difference between merging and rebasing is that merging creates 
a new commit with both branches combined, while rebase creates a linear history 
by applying each commit from the source branch on top of the target branch. 
In other words, rebase takes the whole source branch and places it on top of the main branch.
Therefore, it is rewriting the commit history to achieve cleaner results than merge.


## Warning

**Never use rebase on public/remote branches.** As it rewrites the commit history, 
it results in nasty conflicts when other developers try to pull the rebased branch.
And it could lead to loss of work.

## Examples
### Simple example
We start with a simple example of when the feature branch and main diverged:

```
           F - G            <-- feature
         /
- A - B - C - D - E       <-- main
```

We want to integrate the changes in the main to the feature branch but do not want to create merge commit. We simple run:
```commandline
git checkout feature
git rebase main
```

It will result in a nice linear commit history.

```
                     <-- main
                   / 
- A - B - C - D - E - F - G <-- feature
```

### Interactive
Adding `-i` flag will start the interactive mode in rebasing, which allows you to change 
the commits history in a feature branch. You can use it either when incorporating changes from a main, 
with little cleanup in a feature commit history. Or you can run:
```commandline
git rebase -i HEAD~4
```
To show up the last 4 commits and be able to change them. The interactive mode looks like:

```
pick 07c5abd Fixing mistake
pick de9b1eb Adding new feature 1
pick 3e7ee36 Quick fix in feature
pick fa20af3 Adding new feature 2
```

We can see the last 4 commits, the keyword pick means that the commit will be preserved. As we can see, 
the third commit is just a fix of the second commit, therefore, we can rewrite the *pick* word into *fixup*, 
which will result in adding the third commit to the second commit. It will be similar to the squashing but 
the log message of the fixup commit will be discarded. The most important keywords:
```
pick = use commit
reword = use commit, but edit the commit message
edit = use commit, but stop for amending
squash = use commit, but meld into previous commit
fixup = like "squash", but discard this commit's log message
drop <commit> = remove commit
```

### Multiple branches
For a more complicated example, imagine that our repository looks like this:
```
- A - B - C - D - E       <-- main
          \
           - F - G        <-- database
             \ 
               - H - I    <-- server
```

You checkout from the main to create changes to the database. 
But, then quickly you release you need to make changes to the server as well.
Now you want to put the server branch on top main branch. Just run:
```commandline
git rebase --onto main database server
```
This says: "Take the server branch, find the point where it diverges from the database, 
and take these commits and put them on top of the main branch". The result will look like:
```
                     <-- main
                   /
- A - B - C - D - E - H - I   <-- server
          \
           - F - G            <-- database  
```
And now you can put the database on the top of server, using: `git rebase server database`:

```
                     <-- main
                   /
- A - B - C - D - E - H - I - F - G   <-- database 
                           \
                             <-- server
```

Resulting in a clean linear history, and of course, after the rebase it is possible,
to fast-forward merge changes into the main.

## Pros and Cons of Rebasing

### Pros
* Provides a linear commit timeline
  * Linear history is convenient because the rebased branch appears to be developed directly on top 
of the target branch. This results in a cleaner and more straightforward commit history.

* No additional commits compared to merge
  * Rebasing avoids unnecessary merge commits, which can "spam" the commit history and make it harder 
to track the logical flow of changes over time.

* Allows to clean up commit history
  * Interactive rebasing allows you to change order of commits or add some commits into one.

### Cons
* History rewrite
  * Since rebasing rewrites the commit history it can be potentially causing issues 
if the branch has been shared with other users. It can lead to confusion and synchronization problems.

* Loss of merge information
  * When you rebase, you lose information about the branch's merge points with other branches, 
which can be relevant for some projects and auditing purposes.


## Merge vs Rebase
The decision to use merging or rebasing depends on the project's needs and collaboration workflow:

Use **Merging** when:

* You want to preserve the branch's entire commit history, including merge commits. 
Self-consistent features have their commits in their branches.
* Collaboration with multiple contributors is essential, and a shared history is more straightforward.
* When working with public branch used by other developers.
* It is safer option than rebase, and could be safer when working with inexperienced developers.

Use **Rebasing** when:

* You prefer a clean and linear commit history, making it easier to review and understand changes. 
As rebase allows you to clean up your commit history and is not making additional merge commits. 
* Your branch is a local feature or topic branch, and you want to keep the history concise. 
As constant merging of changes in main into your feature would lead to polluted commits and loss of clarity. 
* When your pull request branch get out-dated with the base branch. You can rebase pull request branch onto 
tip of the base and then ff-merge it with resulting clean linear history, but simple merge is option as well.

## Sources:
https://www.atlassian.com/git/tutorials/merging-vs-rebasing#conceptual-overview  
https://git-scm.com/book/en/v2/Git-Branching-Rebasing  
https://git-scm.com/docs/git-rebase  
https://www.geeksforgeeks.org/rebasing-of-branches-in-git/  
https://thoughtbot.com/blog/git-interactive-rebase-squash-amend-rewriting-history  
