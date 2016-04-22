I want to bundle open some gem, and I soon get an error:

`To open a bundled gem, set $EDITOR or $BUNDLER_EDITOR`

Add this to ~/.zshrc:

`export EDITOR=<editor name>`

For Vim:

`export EDITOR='vi'`

Source the .rc file and open a new tab, bundle open should be find.

Reference: [Setting 'EDITOR' or 'BUNDLER_EDITOR' environment variable](http://stackoverflow.com/questions/25084035/setting-editor-or-bundler-editor-environment-variable)