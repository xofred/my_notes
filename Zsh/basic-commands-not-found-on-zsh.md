Yes, I messed up my `PATH`...And here is the cure:

```shell
PATH=/bin:/usr/bin:/usr/local/bin:${PATH}
export PATH
```

Reference: [commands not found on zsh](http://stackoverflow.com/questions/18428374/commands-not-found-on-zsh)