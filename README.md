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
-has_many :likes

##Addresses table

| Column             | Type                | Options                        |
|--------------------|---------------------|--------------------------------|
| zip_code           | string              | null: false                    |
| prefecture_id      | integer             | null: false,foreign_key: true  |
| building           | string              | null: false                    |
| city               | string              | null: false                    |
| street             | string              | null: false                    |
| phone              | integer             | null: false                    |


##Items table

| Column             | Type                | Options                       |
|--------------------|---------------------|-------------------------------|
| name               | string              | null: false                   |
| description        | text                | null: false                   |
| category_id        | references          | null: false                   |               
| status             | string              | null: false                   |       
| shipping_charge    | integer             | null: false                   |
| prefecture_id      | integer             | null: false                   |
| shipping_days      | integer             | null: false                   |
| price              | integer             | null: false                   |
| user_id            | references          | null: false, foreign_key: true|


-belongs_to :user
-has_many_attached :images
-has_many :comments
-has_many :likes


##Comments table

| Column             | Type                | Options                       |
|--------------------|---------------------|-------------------------------|
| user_id            | references          | null: false, foreign_key: true|                   
| item_id            | references          | null: false, foreign_key: true|
| comment            | string              | null: false                   |

-belongs_to :user
-belongs_to :item

##Likes table

| Column             | Type                | Options                       |
|--------------------|---------------------|-------------------------------|               
| user               | references          | null: false, foreign_key: true|
| item               | references          | null: false, foreign_key: true|                         |

-belongs_to :user
-belongs_to :item
