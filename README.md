## usersテーブル

| Clumn              | Type       | Options                |
|--------------------|------------|------------------------|
| email              | string     | NOT NULL, unique: true |
| encrypted_password | string     | NOT NULL               |
| name               | string     | NOT NULL               |
| profile            | text       | NOT NULL               |
| occupation         | text       | NOT NULL               |
| position           | text       | NOT NULL               |

### Association

- has_many :prototypes
- has_many :comments


## prototypesテーブル

| Clumn              | Type       | Options                     |
|--------------------|------------|-----------------------------|
| title              | string     | NOT NULL                    |
| catch_copy         | text       | NOT NULL                    |
| concept            | text       | NOT NULL                    |
| user               | references | NOT NULL, foreign_key: true |

※imageはActiveStorageで実装するため含まない

### Association

- belongs_to :use
- has_many :comments

## commentsテーブル

| Clumn              | Type       | Options                     |
|--------------------|------------|-----------------------------|
| content            | text       | NOT NULL                    |
| prototype          | references | NOT NULL, foreign_key: true |
| user               | references | NOT NULL, foreign_key: true |

### Association

- belongs_to :user
- belongs_to :prototype