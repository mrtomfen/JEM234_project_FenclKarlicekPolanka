# Merging strategies
  * When people collaborate on one project in Git, they often use different branches. This approach is convenient because it allows for isolation of changes and organised parallel development process. Each branch works on its own part of the project and together they form the whole outcome. But to be able to come up with only one final version of the project, they need to merge their parts of code (branches) together, and there are many ways to achieve this goal.

  * This GitHub repository describes both fundamental and advanced merging methods in git.
  
## Contents
* Fundamental merging algorithms
  * Fast-forward
  * Three-way
* Advanced merging algorithms
  * Resolve
  * Recursive
  * Ort
  * Octopus
  * Ours
  * Subtree
<contents>

## Fundamental merging algorithms
In Git, there are two basic merging algorithms: fast-forward merging and three-way merging. These algorithms are used to combine changes from one branch into another branch. The choice of merging algorithm depends on the branch histories and whether there are any conflicts between the branches being merged.

### Fast-Forward 

Fast-forward merging is a straightforward process occurring when there are no new commits on the target branch since the divergence point. Git simply moves the branch pointer of the target branch forward to the tip of the source branch, effectively incorporating the changes. This results in a linear commit history and is often used for simple feature branches or bug fixes.

```bash
git merge source_branch
```

On the [Figure 1](#ff-merge) is the git graph before and after calling the merge. You can see the main branch in blue and dev branch in green. Please note that the changes are only on the dev branch. After the fast-forward merge occurred, a linear commit history with a moved branch pointer has been created. Thus, the changes in the dev branch were incorporated into the main branch. 

<figure id="ff-merge" style="text-align: center;">
  <img src="images/ff_merge.png" alt="Fast-Forward Merge" width="250"/>
  <figcaption>Figure 1: Fast-Forward merging</figcaption>
</figure>
<p style="text-align: center;">
  Image source: www.bogotobogo.com 
</p>
<https://www.bogotobogo.com/DevOps/SCM/Git/Git_GitHub_Fast-Forward_Merge.php>


<!--TBD nechapu co se timhle odstavcem snazime rict, bud bych to preformuloval nebo vynechal-Martin--> 

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

Below you can find [Figure 3](#tw-merge) to see the before and after git graphs of three-way merge.
  
<figure id="tw-merge" style="text-align: center;">
  <img src="images/three-way-merge.png" alt="Three-way Merge" width="500"/>
  <figcaption>Figure 2: Three-way merging</figcaption>
</figure>
<p style="text-align: center;">
  Image source: www.dev.to
</p>
<https://dev.to/neshaz/how-to-use-git-merge-the-correctway-25pd>


## Advanced merging strategies
It might happen that the branch structure is more complex than in the previously mentioned fundamental merging strategies. For such situations Git provides a range of sophisticated merging algorithms that go beyond the basic fast-forward and three-way merges. These advanced merging strategies are designed to handle complex development workflows. As software projects grow in size and complexity, mastering these advanced merging techniques becomes increasingly essential for developers and teams striving for efficient code management, collaboration, and version control.

### Resolve

### Recursive
### Ort
### Octopus
### Ours
### Subtree


## Sources: 
https://git-scm.com/docs/git-merge  
https://git-scm.com/docs/merge-strategies  
https://www.atlassian.com/git/tutorials/using-branches/git-merge
https://www.atlassian.com/git/tutorials/using-branches/merge-strategy  
https://www.geeksforgeeks.org/merge-strategies-in-git/  

