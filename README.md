# DB設計


## usersテーブル

|Column|Type|Options|
|------|----|-------|
|id|integer| |
|name|string|null: false,unique:true, index|
|email|string|null: false,unique:true |
|password|string|null: false |


### Association
- has_many :messages
- has_many :groups,through::groups_users



## groupsテーブル

|Column|Type|Options|
|------|----|-------|
|id|integer| |
|name|string|null: false,unique:true, index|


### Association
- has_many :messages
- has_many :users,through::groups_users



## messagesテーブル

|Column|Type|Options|
|------|----|-------|
|id|integer| |
|body|text|null: false|
|image|string||
|date|daytime||
|user_id|integer|foreign_key: true|
|group_id|integer|foreign_key: true|


### Association
- belongs_to :group
- belongs_to :user



## groups_usersテーブル

|Column|Type|Options|
|------|----|-------|
|user_id|integer|null: false, foreign_key: true|
|group_id|integer|null: false, foreign_key: true|

### Association
- belongs_to :group
- belongs_to :user