## users table

| Column             | Type   | Option        |
| ------------------ | ------ | ------------- |
| nickname           | string | null: false   |
| e-mail             | string | unique: true  |
| encrypted_password | string | null: false   |
| last_name          | string | null: false   |
| first_name         | string | null: false   |
| birthday           | date   | null: false   |

### Association

- has_many :item
- has_many :purchase


## items table

| Column        | Type         | Option                          |
| ------------- | ------------ | ------------------------------- |
| description   | text         | null: false                     |
| category      | integer      | null: false                     |
| condition     | integer      | null: false                     |
| delivery_fee  | integer      | null: false                     |
| area          | integer      | null: false                     |
| shipping_date | integer      | null: false                     |
| price         | integer      | null: false                     |
| user          | references   | null: false, foreign_key: true  |

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
| area             | integer      | null: false                     |
| municipality     | string       | null: false                     |
| street_number    | string       | null: false                     |
| building         | string       | null: false                     |
| telephone_number | string       | null: false                     |
| purchase         | references   | null: false, foreign_key: true  |

### Association

- belongs_to :purchase