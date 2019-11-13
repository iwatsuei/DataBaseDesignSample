# chat-space DB設計
## usersテーブル
|Column|Type|Options|
|------|----|-------|
|email|string|null: false|
|password|string|null: false|
|name|string|null: false, add_index :users,:name,unique:true|
### Association
- has_many :posts
- has_many :chatgroup_users
- has_many :chatgroup,through: :chatgroup_users

## chatgroup_usersテーブル
|Column|Type|Options|
|------|----|-------|
|user_id|integer|null: false,foreign_key: true|
|chatgroup_id|integer|null: false,foreign_key: true|
### Association
- belongs_to :chatgroup
- belongs_to :users

## chatgroupテーブル
|Column|Type|Options|
|------|----|-------|
|name|string|null: false|
### Association
- has_many :posts
- has_many :chatgroup_users
- has_many :users, through: :chatgroup_users

## postsテーブル
|Column|Type|Options|
|------|----|-------|
|image|text||
|text|text||
|user_id|integer|null: false, foreign_key: true|
|chatgroup_id|integer|null: false, foreign_key: true|
### Association
- belongs_to :user
- belongs_to :chatgroup