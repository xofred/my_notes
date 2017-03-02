Here is the fix, no development required.
All you have to do is to change the clientid key in the Bundles editor:

* open Sequel Pro application
* go to Bundles -> Bundle Editor
* Use left pane, Select "Input field" (Show), choose Format SQL
* find the following row in the "Command" textarea:
* replace the value of the input to "dpriver-9094-8133-2031", so the new line is:
* Click "Save"

Change line 149 from
```
<input type="hidden" name="clientid" value="4149-9094-8133-2031" />
```
to
```
<input type="hidden" name="clientid" value="dpriver-9094-8133-2031" />
```

Reference: [Update SQL formatter bundle for new API](https://github.com/sequelpro/sequelpro/issues/1988)