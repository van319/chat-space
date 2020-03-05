# README

This README would normally document whatever steps are necessary to get the
application up and running.

Things you may want to cover:

* Ruby version

* System dependencies

* Configuration

* Database creation

* Database initialization

* How to run the test suite

* Services (job queues, cache servers, search engines, etc.)

* Deployment instructions

* ...

# Chat-space DB設計
## usersテーブル

|Column|Type|Options|
|------|----|-------|
|password|string|null: false|
|email|string|null: false, unique: true|
|user_name|string|null: false｜
### Association
has_many :groups_users
has_many :groups, through: groups_users
has_many :message


## massegeテーブル

|Column|Type|Options|

|user_id|integer|null: false, foreign_key: true|
|group_id|integer|null: false, foreign_key: true|
|body|text||
|image|text||
### Association
belongs_to :groups
belongs_to :users


## groupsテーブル
|Column|Type|Options|
|group_name|string|null: false, foreign_key: true|

### Association
has_many:message
has_many :users, through: groups_users
belongs_to :users



## groups_usersテーブル
|Column|Type|Options|

|user_id|integer|null: false, foreign_key: true|
|group_id|integer|null: false, foreign_key: true|

### Association
belongs_to :groups
belongs_to :users