## users table

| Column        | Type   | Option      |
| ------------- | ------ | ----------- |
| nickname      | string | null: false |
| email         | string | null: false |
| password      | string | null: false |
| name          | string | null: false |
| name_kana     | string | null: false |
| birthday      | string | null: false |

### Association

- has_many :items
- has_many :purchases


## items table

| Column        | Type         | Option             |
| ------------- | ------------ | ------------------ |
| image         | string       | null: false        |
| description   | text         | null: false        |
| category      | string       | null: false        |
| condition     | string       | null: false        |
| delivery_fee  | string       | null: false        |
| area          | string       | null: false        |
| shipping_date | string       | null: false        |
| price         | string       | null: false        |
| user_id       | references   | foreign_key: true  |

### Association

- belongs_to :users
- has_one :purchases


## purchases table

| Column        | Type         | Option             |
| ------------- | ------------ | ------------------ |
| item_id       | references   | foreign_key: true  |
| user_id       | references   | foreign_key: true  |

### Association

- belongs_to :users
- belongs_to :items
- has_one :places


## places table

| Column           | Type         | Option             |
| ---------------- | ------------ | ------------------ |
| zip_code         | string       | null: false        |
| prefecture       | string       | null: false        |
| municipality     | string       | null: false        |
| street_number    | string       | null: false        |
| building         | string       | null: false        |
| telephone_number | string       | null: false        |
| purchase_id      | references   | foreign_key: true  |

### Association

- belongs_to :purchases