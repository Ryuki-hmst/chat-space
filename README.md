# ChatSpace DB設計
## usersテーブル

|Column|Type|Options|
|------|----|-------|
|username|string|null: false|
|email|string|null: false|
|password|string|null: false| 

### Association
- has-many :groups, through: groups_users
- has-many :groups_users
- has-many :messages


## groupsテーブル

|Column|Type|Options|
|------|----|-------|
|title|text|null: false|
|user_id|integer|null: false, foreign_key: true|

### Association
- has-many :users, through: groups_users
- has-many :groups_users
- has-many :messages

## groups_usersテーブル

|Column|Type|Options|
|------|----|-------|
|user_id|integer|null: false, foreign_key: true|
|group_id|integer|null: false, foreign_key: true|

### Association
- belongs_to :group
- belongs_to :user

## messagesテーブル

|Column|Type|Options|
|------|----|-------|
|body|text|null: false|
|image|string|
|group_id|integer|null: false, foreign_key: true|
|user_id|integer|null: false, foreign_key: true|

### Association
- belongs_to :user
- belongs_to :group
