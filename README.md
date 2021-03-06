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

# ChatSpace DB設計
## usersテーブル
|Column|Type|Options|
|------|----|-------|
|name|srting|index:true,null:false,unique:true|
|email|string|null:false|
|password|string|null: false|

### Association
- has_many :groups, through :groups_users
- has_many :groups_users
- has_many :chat_texts


## groupsテーブル
|Column|Type|Options|
|------|----|-------|
|name|srting|index:true,null:false,unique:true|

### Association
- has_many :users, through :groups_users
- has_many :groups_users
- has_many :chat_texts


## group_usersテーブル
|Column|Type|Options|
|------|----|-------|
|user|references|null: false, foreign_key: true|
|group|references|null: false, foreign_key: true|

### Association
- belongs_to :group
- belongs_to :user


## chat_textsテーブル
|Column|Type|Options|
|------|----|-------|
|text|srting|
|image|string|
|user|references|null: false, foreign_key: true|
|group|references|null: false, foreign_key: true|

### Association
- belongs_to :group
- belongs_to :user