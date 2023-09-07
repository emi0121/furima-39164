# DB 設計

##Users table

| Column             | Type                | Options                   |
|--------------------|---------------------|---------------------------|
| nickname           | string              | null: false               |
| email              | string              | null: false, unique: true |
| encrypted_password | string              | null: false               |
| first_name         | string              | null: false               |
| last_name          | string              | null: false               |
| first_name_kana    | string              | null: false               |
| last_name_kana     | string              | null: false               |
| birthday           | date                | null: false               |

-has_many :items
-has_many :orders
-has_many :comments

##Payments table

| Column             | Type                | Options                        |
|--------------------|---------------------|--------------------------------|
| order_id           | references          | null: false,foreign_key: true  |
| zip_code           | string              | null: false                    |
| prefecture_id      | integer             | null: false                    |
| city               | string              | null: false                    |
| street             | string              | null: false                    |
| building           | string              |                                |
| phone              | string              | null: false                    |

-belongs_to :order


##Orders table

| Column             | Type                | Options                        |
|--------------------|---------------------|--------------------------------|
| user               | references          | null: false,foreign_key: true  |
| item               | references          | null: false,foreign_key: true  |

-belongs_to :user
-belongs_to :item
-has_one :payment



##Items table

| Column             | Type                | Options                       |
|--------------------|---------------------|-------------------------------|
| user               | references          | null: false, foreign_key: true|
| name               | string              | null: false                   |
| description        | text                | null: false                   |
| category_id        | integer             | null: false                   |               
| status_id          | integer             | null: false                   |       
| shipping_charge_id | integer             | null: false                   |
| prefecture_id      | integer             | null: false                   |
| shipping_date_id   | integer             | null: false                   |
| price              | integer             | null: false                   |

-belongs_to :user
-has_one :order
-has_many :comments


##Comments table

| Column             | Type                | Options                       |
|--------------------|---------------------|-------------------------------|
| user               | references          | null: false, foreign_key: true|                   
| item               | references          | null: false, foreign_key: true|
| comment            | text                | null: false                   |

-belongs_to :user
-belongs_to :item
