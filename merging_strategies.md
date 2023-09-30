# TODO:
* Introduction
  * what merge is and its purpose
* Basic merging algorithms
  * fast-forward
  * three-way
* Advanced
  * resolve
  * recursive
  * ort
  * octopus
  * ours
  * subtree

# Advanced merging strategies

<two-three sentences about merging>

## Contents

<contents>

## Fundamental techniques

<two-three sentence intro to fund m.t.>

### Fast-Forward 

Fast-forward merging is a straightforward process occuring when there are no new commits on the target branch since the divergence point. Git simply moves the branch 
pointer of the target branch forward to the tip of the source branch, effectively incorporating the changes. This results in a linear commit history and 
is often used for simple feature branches or bug fixes.

```bash
git merge source_branch
```

On the figure `[Figure 1](#before-ff-merge)` is the git graph before calling the merge. Please note that the changes are only on the dev branch. `[Figure 2](#after-ff-merge)` then shows the 
situation after the fast-forward merge occured, a linear commit history with moved branch pointer. 

```bash
<figure id="before-ff-merge" align="center">
  <img src="images/before_ff_merge.png" alt="Before Fast-Forward Merge" width="400"/>
  <figcaption>Figure 1: Before Fast-Forward Merge</figcaption>
</figure>
<figure id="after-ff-merge" align="center">
  <img src="images/after_ff_merge.png" alt="After Fast-Forward Merge" width="400"/>
  <figcaption>Figure 2: After Fast-Forward Merge</figcaption>
</figure>
```


### Three-Way


## Advanced techniques





## Sources: 
https://git-scm.com/docs/git-merge  
https://git-scm.com/docs/merge-strategies  
https://www.atlassian.com/git/tutorials/using-branches/git-merge
https://www.atlassian.com/git/tutorials/using-branches/merge-strategy  
https://www.geeksforgeeks.org/merge-strategies-in-git/  

