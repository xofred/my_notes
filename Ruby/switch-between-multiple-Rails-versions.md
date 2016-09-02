```shell
$ rvm gemset create rails410 rails320
Gemset 'rails410' created.
Gemset 'rails320' created.

$ rvm 2.1.1@rails410
$ gem install rails -v 4.1.0

$ rvm 2.1.1@rails320
$ gem install rails -v 3.2.0
```

Then add a .rvmrc file in project folder
```shell
rvm 2.1.1@rails410
```

Reference: [Named Gem Sets](https://rvm.io/gemsets/basics)