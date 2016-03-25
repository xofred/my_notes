**In Rails:**

We usually have some yml config files, such as `database.yml`, `some_cloud_service_settings.yml`. They contain sensitive infos such as database's user/pass, or api's token, and we sure don't want them in the git system. Instead we make a `xxx.yml.sample` file, for development.

Here's how to batch rename the `aaa.yml.sample`, `bbb.yml.sample` files into `aaa.yml`, `bbb.yml`.

**By Zsh:**

Insert the following two lines into your .zshrc
```zsh
autoload -U zmv
alias mmv='noglob zmv -W'
```
The first line activates the zmv command, an extended move command provided by the zsh. The second line creates an alias for a simplified invocation of that command. 

All of a sudden, you can write something like `mmv *.dat *.dat_old` or `mmv foo.* bar.*` into a newly opened terminal and it will do as you expect! You can even invoke `mmv **/*2008.mp3 **/*2009.mp3` and all matching files residing in any subdirectory are renamed according to the pattern as well.

Reference: [Moving or Renaming Multiple Files – The Easy (zsh) Way](http://www.mfasold.net/blog/2008/11/moving-or-renaming-multiple-files/)