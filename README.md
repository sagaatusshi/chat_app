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

## users テーブル
| Coulumn            | Type   | Options     |
| -------------------|--------| ----------- |
| name               | string | null: false |
| email              | string | null: false |
| encrypted_password | string | null: false |

### Association
- has_many :room_users
- has_many :rooms, through :room_users
- has_many :messages

## rooms テーブル
| Coulmn | Type   | Option      |
| ------ | ------ | ----------- |
| name   | string | null: false |

### Association
- has_many :room_users
- has_many :users, through :room_users
- has_many :messages

## room_users テーブル
| Coulmn | Type       | Option                         |
| ------ | ---------- | ------------------------------ |
| user   | references | null: false, foreign_key: true |
| room   | references | null: false, foreign_key: true |

### Association
- belongs_to :user
- belongs_to :room

## messages テーブル
| Coulmn  | Type       | Option                         |
| ------- | ---------- | ------------------------------ |
| content | string     |                                |
| user    | references | null: false, foreign_key: true |
| room    | references | null: false, foreign_key: true |

### Association
- belongs_to :user 
- belongs_to :room
