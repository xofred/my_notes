Said some of your changes from your previous commit accidentally flushed by someone else. And sure you don't want to repeat typing or copy and paste them one by one. Here's the savior!

1. `git cherry-pick (commit hash you want to apply)`

(It's very likely to have conflicts)

2. Fix merge conflicts.

3. Add fixed file(s).

4. `git cherry-pick --continue`

Reference: [How to apply an old commit on Git?](https://stackoverflow.com/questions/29934650/how-to-apply-an-old-commit-on-git)