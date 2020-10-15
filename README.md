# README

## DB 設計

## users table

| Column             | Type                | Options                 |
|--------------------|---------------------|-------------------------|
| id(PK)             | デフォルト          | null: false             |
| nickname           | devise のデフォルト | null: false,index: true |
| email              | devise のデフォルト | null: false             |
| encrypted_password | integer             | null: false             |
| first_name         | string              | null: false             |
| last_name          | string              | null: false             |
| first_name_kana    | string              | null: false             |
| last_name_kana     | string              | null: false             |
| birth_date         | integer             | null: false             |

### Association

* has_many :items
* has_many :item_transactions
* has_many :cards

## addresses table

| Column       | Type    | Options           |
|--------------|---------|-------------------|
| postal_code  | integer | null: false       |
| prefecture   | integer | null: false       |
| city         | string  | null: false       |
| address      | string  | null: false       |
| building     | string  |                   |
| phone_number | string  | null: false       |
| item_id(FK)  | integer | foreign_key: true |

### Association

* belongs_to :item

## items table

| Column                              | Type       | Options           |
|-------------------------------------|------------|-------------------|
| id(PK)                              | デフォルト | null: false       |
| name                                | string     | null: false       |
| price                               | integer    | null: false       |
| info                                | text       | null: false       |
| scheduled_delivery_id(acitve_hash)  | integer    | null: false       |
| shipping_fee_status_id(acitve_hash) | integer    | null: false       |
| prefecture_id(acitve_hash)          | integer    | null: false       |
| sales_status_id(acitve_hash)        | integer    | null: false       |
| category_id(acitve_hash)            | integer    | null: false       |
| user_id(FK)                         | integer    | foreign_key: true |

### Association

- belongs_to :user
- has_one :item_transaction
- has_one :address

## item_transactions table

| Column      | Type    | Options           |
|-------------|---------|-------------------|
| item_id(FK) | integer | foreign_key: true |
| user_id(FK) | integer | foreign_key: true |

### Association

- belongs_to :item
- belongs_to :user
