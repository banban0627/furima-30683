# DB 設計

## users table

| Column             | Type                | Options                 |
|--------------------|---------------------|-------------------------|
| nickname           | string              | null: false             |
| email              | string              | null: false             |
| password           | string              | null: false             |
| family_name        | string              | null: false             |
| last_name          | string              | null: false             |
| family_name_kana   | string              | null: false             |
| last_name_kana     | string              | null: false             |
| birthday           | text                | null: false             |

### Association

* has_many :items
* has_many :listings

## item table

| Column                              | Type       | Options           |
|-------------------------------------|------------|-------------------|
| item_name                           | string     | null: false       |
| item_text                           | text       | null: false       |
| price                               | text       | null: false       |
| category                            | text       | null: false       |
| status                              | text       | null: false       |
| delivery_fee                        | text       | null: false       |

### Association

- belongs_to :user
- belongs_to :listing
- has_one :item

## listing table

| Column               | Type       | Options           |
|----------------------|------------|-------------------|
| listing_username    | string      | null: false       |
| shipment_source      | string     | null: false       |
| date                 | text       | null: false       |

### Association

- belongs_to :user
- belongs_to :item
- has_one :item