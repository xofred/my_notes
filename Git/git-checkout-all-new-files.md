I intent to rollback to a very old commit, thus produces a lot of new untracked files...

Thankfully, there is a fast way to check them all out:

```shell
git clean -f -d
```

Reference: [git: undo all working dir changes including new files](http://stackoverflow.com/questions/1090309/git-undo-all-working-dir-changes-including-new-files)