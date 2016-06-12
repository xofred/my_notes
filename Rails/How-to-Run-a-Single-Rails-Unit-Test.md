The first solution is to call this rake task:

```shell
rake test TEST=path_to_test_file
```

So the final command should look like

```shell
rake test TEST=test/unit/invitation_test.rb
```

Reference: [How to Run a Single Rails Unit Test](http://flavio.castelli.name/2010/05/28/rails_execute_single_test/)