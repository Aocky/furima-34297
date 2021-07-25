## users table

| Column             | Type   | Option                     |
| ------------------ | ------ | -------------------------- |
| nickname           | string | null: false                |
| email              | string | null: false, unique: true  |
| encrypted_password | string | null: false                |
| last_name          | string | null: false                |
| first_name         | string | null: false                |
| last_name_kana     | string | null: false                |
| first_name_kana    | string | null: false                |
| birthday           | date   | null: false                |

### Association

- has_many :items
- has_many :purchases


## items table

| Column           | Type         | Option                          |
| ---------------- | ------------ | ------------------------------- |
| product_name     | string       | null: false                     |
| description      | text         | null: false                     |
| category_id      | integer      | null: false                     |
| condition_id     | integer      | null: false                     |
| delivery_fee_id  | integer      | null: false                     |
| area_id          | integer      | null: false                     |
| shipping_date_id | integer      | null: false                     |
| price            | integer      | null: false                     |
| user             | references   | null: false, foreign_key: true  |

### Association

- belongs_to :user
- has_one :purchase


## purchases table

| Column        | Type         | Option                          |
| ------------- | ------------ | ------------------------------- |
| item          | references   | null: false, foreign_key: true  |
| user          | references   | null: false, foreign_key: true  |

### Association

- belongs_to :user
- belongs_to :item
- has_one :place


## places table

| Column           | Type         | Option                          |
| ---------------- | ------------ | ------------------------------- |
| zip_code         | string       | null: false                     |
| area_id          | integer      | null: false                     |
| municipality     | string       | null: false                     |
| street_number    | string       | null: false                     |
| building         | string       |                                 |
| telephone_number | string       | null: false                     |
| purchase         | references   | null: false, foreign_key: true  |

### Association

- belongs_to :purchase