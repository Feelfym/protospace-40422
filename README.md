# テーブル設計

## usersテーブル
| column             | type   | options    |
| ------------------ | ------ | ---------- |
| email              | string | null:false, unique: true |
| encrypted_password | string | null:false |
| name               | string | null:false |
| profile            | text   | null:false |
| occupation         | text   | null:false |
| position           | text   | null:false |

### association
- has_many :prototypes
- has_many :comments

## prototypesテーブル
| column     | type       | options                        |
| ---------- | ---------- | ------------------------------ |
| title      | string     | null:false                     |
| catch_copy | text       | null:false                     |
| concept    | text       | null:false                     |
| user       | references | null:false, foreign_keys: true |

### association
- belongs_to :user
- has_many :comments

## commentsテーブル


| column    | type       | options                        |
| --------- | ---------- | ------------------------------ |
| content   | text       | null:false                     |
| prototype | references | null:false, foreign_keys: true |
| user      | references | null:false, foreign_keys: true |

### association
- belongs_to :user
- belongs_to :prototype


---



## ログインしていない状態では遷移できないページ

- プロトタイプ新規投稿ページ
- プロトタイプ編集ページ
- プロトタイプ削除機能（ページはありませんが、他と同様の実装方法で制限をかけましょう）

## ログインしていない状態でも遷移できるページ

- トップページ
- プロトタイプ詳細ページ
- ユーザー詳細ページ
- ユーザー新規登録ページ
- ログインページ