### Undo a commit and redo

```
$ git commit -m "Something terribly misguided"              (1)
$ git reset --soft HEAD~                                    (2)
<< edit files as necessary >>                               (3)
$ git add ...                                               (4)
$ git commit -c ORIG_HEAD                                   (5)
```

This is what you want to undo

This is most often done when you remembered what you just committed is incomplete, or you misspelled your commit message1, or both. Leaves working tree as it was before git commit.

Make corrections to working tree files.

git add whatever changes you want to include in your new commit.

Commit the changes, reusing the old commit message. reset copied the old head to .git/ORIG_HEAD; commit with -c ORIG_HEAD will open an editor, which initially contains the log message from the old commit and allows you to edit it. If you do not need to edit the message, you could use the -C option instead.

Reference: [How do you undo the last commit?](http://stackoverflow.com/questions/927358/how-do-you-undo-the-last-commit)