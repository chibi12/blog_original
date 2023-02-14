# Blog_originalの設計

## users テーブル

| Column             | Type   | Options     |
| ------------------ | ------ | ----------- |
| name               | string | null: false |
| email              | string | null: false |
| encrypted_password | string | null: false |
| profile            | text   | null: false |
| occupation         | text   | null: false |

### Association
- has_many :blogs
- has_many :comments

## blog テーブル

| Column    | Type       | Options              |
| --------  | ---------  | -------------------- |
| title     | string     | null: false          |
| catch_copy| text       | null: false          |
| content   | text       | null: false          |
| user      | references | null: false, 外部キー |

### Association
- has_many :users 
- has_many :messages

## comments テーブル

| Column  | Type       | Options                        |
| ------- | ---------- | ------------------------------ |
| content | string     |                                |
| user    | references | null: false, foreign_key: true |
| blog    | references | null: false, foreign_key: true |

### Association
- belongs_to :blog
- belongs_to :user
