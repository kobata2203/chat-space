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

## group_usersテーブル
|Column|Type|Options|
|------|----|-------|
|group_name|srting|index:true,null:false,unique:true|
|chat_member|srting|index:true,null:false,unique:true|

## chat_textテーブル
|Column|Type|Options|
|------|----|-------|
|text|srting|
|image|string|
|user|references|null: false, foreign_key: true|
|group|references|null: false, foreign_key: true|

### Association
- belongs_to :group
- belongs_to :user
- has_many :group_names, through: chat_members
- has_many :texts