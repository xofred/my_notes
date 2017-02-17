```ruby
# db/schema.rb
ActiveRecord::Schema.define(version: 20170216080933) do

  # These are extensions that must be enabled in order to support this database
  enable_extension "plpgsql"

  create_table "chatrooms", force: :cascade do |t|
    t.string   "topic"
    t.string   "slug"
    t.datetime "created_at", null: false
    t.datetime "updated_at", null: false
  end

  create_table "messages", force: :cascade do |t|
    t.string   "content"
    t.integer  "user_id"
    t.integer  "chatroom_id"
    t.datetime "created_at",  null: false
    t.datetime "updated_at",  null: false
    t.index ["chatroom_id"], name: "index_messages_on_chatroom_id", using: :btree
    t.index ["user_id"], name: "index_messages_on_user_id", using: :btree
  end

  create_table "users", force: :cascade do |t|
    t.string   "username"
    t.datetime "created_at", null: false
    t.datetime "updated_at", null: false
  end

  add_foreign_key "messages", "chatrooms"
  add_foreign_key "messages", "users"
end
```

```ruby
# db/migrate/20170216073711_create_messages.rb
class CreateMessages < ActiveRecord::Migration[5.0]
  def change
    create_table :messages do |t|
      t.string :content
      t.references :user
      t.references :chatroom

      t.timestamps
    end
  end
end
```

```ruby
# db/migrate/20170216080933_add_fk_to_messages.rb
class AddFkToMessages < ActiveRecord::Migration[5.0]
  def change
    add_foreign_key :messages, :chatrooms
    add_foreign_key :messages, :users
  end
end

```