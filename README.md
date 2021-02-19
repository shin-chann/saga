# ご当地サ〜ガ

## 画像の貼り付けや画像の名称・説明、それに対してのコメントができます。

## テスト用アカウント　実装予定ではありますが現在はなしです。

## 佐賀の名所や名産・個人のお店などのPRができます。

## このアプリケーションを通して佐賀を知ってもらって行きたいと思ってもらえるようにしたかったからです。

## 現在実装したものはありません。

## 実装予定の機能　ユーザー管理機能、　ツイート新規投稿・詳細・編集・削除機能、　ツイートに対してのコメント投稿機能です。

## ER図 https://gyazo.com/a920afc539a147bd64fd679e92df9db4


# データベース設計

## usersテーブル

| Column    | Type   | options     |
| --------- | ------ | ----------  |
| email     | string | null: false |
| password  | string | null: false |
| name      | string | null: false |


### Association

- has_many :tweets
- has_many :comments

## tweetsテーブル

| Column       | Type       | Options                        |
| ------------ | ---------- | ------------------------------ |
| text         | string     | null: false                    |
| introduction | text       | null: false                    |
| user         | references | null: false, foreign_key: true |

### Association

- belongs_to :user
- has_many :comments

## comments

| Column        | Type       | Options                        |
| --------------| ---------- | ------------------------------ |
| comment_text  | text       | null: false                    |
| user          | references | null: false, foreign_key: true |
| tweet         | references | null: false, foreign_key: true |

### Association

- belongs_to :tweets
- belongs_to :user