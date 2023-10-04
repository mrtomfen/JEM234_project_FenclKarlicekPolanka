# Rebasing
  * Git rebase is a command used to modify the commit history of a branch. It allows the users to reorganize and streamline the commit history by moving, combining, or editing commits. Rebase is commonly used to integrate changes from one branch into another, typically from a feature branch into a main development branch. 
  
  * The main difference between merging and rebasing is that merging creates a new commit with both branches combined, while rebase creates a linear history by applying each commit from the source branch on top of the target branch. In other words, rebase takes the whole source branch and places it on top of the main branch.
  
## Contents
* TBD
<contents>


## Examples
TBD
  * basic and some more complicated



## Pros and Cons of Rebasing

### Pros
* Provides a linear commit timeline
  * Linear history is covenient because the rebased branch appears to be developed directly on top of the target branch. This results in a cleaner and more straightforward commit history.

* No additional commits compared to merge
  * Rebasing avoids unnecessary merge commits, which can "spam" the commit history and make it harder to track the logical flow of changes over time.

### Cons
* History rewrite
  * Since rebasing rewrites the commit history it can be potentially causing issues if the branch has been shared with other users. It can lead to confusion and synchronization problems.

* Loss of merge information
  * When you rebase, you lose information about the branch's merge points with other branches, which can be relevant for some projects and auditing purposes.


## Merge vs Rebase
The decision to use merging or rebasing depends on the project's needs and collaboration workflow:

Use **Merging** when:

* You want to preserve the branch's entire commit history, including merge commits.
* Collaboration with multiple contributors is essential, and a shared history is more straightforward.

Use **Rebasing** when:

* You prefer a clean and linear commit history, making it easier to review and understand changes.
* Your branch is a feature or topic branch, and you want to keep the history concise.
* Collaboration primarily occurs through pull requests or merge requests, where a linear history is more suitable.


## Sources:
https://www.atlassian.com/git/tutorials/merging-vs-rebasing#conceptual-overview  
https://git-scm.com/book/en/v2/Git-Branching-Rebasing  
https://git-scm.com/docs/git-rebase  
https://www.geeksforgeeks.org/rebasing-of-branches-in-git/  
