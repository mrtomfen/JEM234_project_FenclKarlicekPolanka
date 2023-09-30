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

Fast-forward merging is a straightforward process occurring when there are no new commits on the target branch since the divergence point. Git simply moves the branch 
pointer of the target branch forward to the tip of the source branch, effectively incorporating the changes. This results in a linear commit history and 
is often used for simple feature branches or bug fixes.

```bash
git merge source_branch
```

On the [Figure 1](#before-ff-merge) is the git graph before calling the merge. Please note that the changes are only on the dev branch. [Figure 2](#after-ff-merge) then shows the situation after the fast-forward merge occurred, a linear commit history with a moved branch pointer. 

<div style="display: flex; justify-content: space-between; align-items: flex-start;">
  <figure id="before-ff-merge" style="text-align: center;">
    <img src="images/before_ff_merge.png" alt="Before Fast-Forward Merge" width="250"/>
    <figcaption>Figure 1: Before Fast-Forward</figcaption>
  </figure>
  <figure id="after-ff-merge" style="text-align: center;">
    <img src="images/after_ff_merge.png" alt="After Fast-Forward Merge" width="250"/>
    <figcaption>Figure 2: After Fast-Forward</figcaption>
  </figure>
</div>

Additionally, merge commit can be forced even if a fast-forward merge is possible by the call below. However, this doesn't change the fundamental decision-making process of Git.

```bash
git merge --no-ff source_branch
```

### Three-Way

Unlike fast-forward merges, three-way merges are employed when both the source and target branches have received new commits since their divergence. This scenario requires Git to perform a more 
complex merge, taking into account the common ancestor of the branches. Git then compares the changes introduced in each branch since that point. It then creates a
new merge commit that reconciles these changes.

```bash
git merge -s recursive source_branch target_branch
```

Below you can find [Figure 3](#before-tw-merge) and [Figure 4](#after-tw-merge) to see the before and after git graphs of three-way merge.
  
<div style="display: flex; justify-content: space-between; align-items: flex-start;">
  <figure id="before-tw-merge" style="text-align: center;">
    <img src="images/before_tw_merge.png" alt="Before Three-Way Merge" width="250"/>
    <figcaption>Figure 3: Before Three-Way</figcaption>
  </figure>
  <figure id="after-tw-merge" style="text-align: center;">
    <img src="images/after_tw_merge.png" alt="After Three-Way Merge" width="250"/>
    <figcaption>Figure 4: After Three-Way</figcaption>
  </figure>
</div>







## Advanced techniques





## Sources: 
https://git-scm.com/docs/git-merge  
https://git-scm.com/docs/merge-strategies  
https://www.atlassian.com/git/tutorials/using-branches/git-merge
https://www.atlassian.com/git/tutorials/using-branches/merge-strategy  
https://www.geeksforgeeks.org/merge-strategies-in-git/  

