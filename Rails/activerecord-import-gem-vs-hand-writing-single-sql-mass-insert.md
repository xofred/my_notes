### Similarity

- use one sql to perform mass records insert, so the benchmarks should be on the same level.

### Differences

- activerecord import (as 'import') will cover the timestamp fields (created_at, updated_at), which hand-writing single sql mass insert (as 'insert') doesn't. I have to specify value for those two.

- import can choose whether or not use rails model validation, which insert will always skip.

ps: all the options of import

```ruby
# == Options
    # * +validate+ - true|false, tells import whether or not to use
    #    ActiveRecord validations. Validations are enforced by default.

    # * +ignore+ - true|false, tells import to use MySQL's INSERT IGNORE
    #    to discard records that contain duplicate keys.

    # * +on_duplicate_key_ignore+ - true|false, tells import to use
    #    Postgres 9.5+ ON CONFLICT DO NOTHING.

    # * +on_duplicate_key_update+ - an Array or Hash, tells import to
    #    use MySQL's ON DUPLICATE KEY UPDATE or Postgres 9.5+ ON CONFLICT
    #    DO UPDATE ability. See On Duplicate Key Update below.

    # * +synchronize+ - an array of ActiveRecord instances for the model
    #   that you are currently importing data into. This synchronizes
    #   existing model instances in memory with updates from the import.

    # * +timestamps+ - true|false, tells import to not add timestamps
    #   (if false) even if record timestamps is disabled in ActiveRecord::Base

    # * +recursive+ - true|false, tells import to import all has_many/has_one
    #   associations if the adapter supports setting the primary keys of the
    #   newly imported objects.

    # * +batch_size+ - an integer value to specify the max number of records to
    #   include per insert. Defaults to the total number of records to import.
```

Reference: 

- [activerecord-import's import method](https://github.com/zdennis/activerecord-import/blob/3a29edae8a9ea576e350cc31b844320517510f02/lib/activerecord-import/import.rb)

- [activerecord-import's wiki](https://github.com/zdennis/activerecord-import/wiki)