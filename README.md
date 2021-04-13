# DB 設計

## users table

| Column             | Type                | Options                 |
|--------------------|---------------------|-------------------------|
| nickname           | string              | null: false             |
| email              | string              | unique: true            |
| encrypted_password | string              | null: false             |
| family_name        | string              | null: false             |
| last_name          | string              | null: false             |
| family_name_kana   | string              | null: false             |
| last_name_kana     | string              | null: false             |
| birthday           | date                | null: false             |

### Association

* has_many :items
* has_many :product_purchases

## item table

| Column                              | Type       | Options           |
|-------------------------------------|------------|-------------------|
| item_name                           | string     | null: false       |
| item_text                           | text       | null: false       |
| price                               | integer    | null: false       |
| category_id                         | integer    | null: false       |
| status_id                           | integer    | null: false       |
| delivery_fee_id                     | integer    | null: false       |
| burden_id                           | integer    | null: false       |
| shipping_day_id                     | integer    | null: false       |
| user                                | references  | null: false, foreign_key: user|



### Association

- belongs_to :user
- has_one :product_purchases

## addresses table

| Column               | Type       | Options           |
|----------------------|------------|-------------------|
| post_number          | string      | null: false       |
| prefecture_id        | integer     | null: false       |
| municipality         | string      | null: false       |
| address              | string      | null: false       |
| build_name           | string      |                   |
| phone_number         | integer     | null: false       |
| product_purchase     | references  | null: false, foreign_key: product_purchase|

### Association

- belongs_to :product_purchase

## product_purchases table

| Column               | Type       | Options           |
|----------------------|------------|-------------------|
| user                 | references  | null: false, foreign_key: address|
| item                 | references  | null: false, foreign_key: address|

### Association

- belongs_to :user
- belongs_to :item
- has_one :addresses