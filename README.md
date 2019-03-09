# README

## Usersテーブル
|Column|Type|Options|
|------|----|-------|
|nickname|string|null: false|
|mail|string|null: false, unique: true|
|password|string|null: false|
|lastname|string|null: false|
|firstname|string|null: false|
|lastname_kana|string|null: false|
|firstname_kana|string|null: false|
|birthyear|string|null: false|
|birthmonth|string|null: false|
|birthday|string|null: false|
|sales_price|string|null: false|
|saler|reference|null: false, foreign_key: true|
|buyer|reference|null: false, foreign_key: true|
|todo|reference|null: false, foreign_key: true|
|notification|reference|null: false, foreign_key: true|
|comment|reference|null: false, foreign_key: true|
|like|reference|null: false, foreign_key: true|
|review|reference|null: false, foreign_key: true|
|point|reference|foreign_key: true|

### Association
- has_many :saler
- has_many :buyer
- has_many :items, thorough: salers
- has_many :items, thorough: buyers
- has_many :todos
- has_many :notifications
- has_many :comments
- has_many :likes
- has_many :reviews
- has_many :points



## Salersテーブル（中間テーブル）
|Column|Type|Options|
|------|----|-------|
|user|reference|null: false, foreign_key: true|
|item|reference|null: false, foreign_key: true|

### Association
- belongs_to :user
- belongs_to :item



## Buyersテーブル（中間テーブル）
|Column|Type|Options|
|------|----|-------|
|user|reference|null: false, foreign_key: true|
|item|reference|null: false, foreign_key: true|

### Association
- belongs_to :user
- belongs_to :item



## Itemsテーブル
|Column|Type|Options|
|------|----|-------|
|image|string|null: false|
|name|string|null: false|
|description|text|null: false|
|size|integer|
|state|integer|null: false|
|shipping_burden|integer|null: false|
|shipping_way|integer|null: false|
|prefecture|integer|null: false|
|shipping_day|integer|null: false|
|price|reference|null: false, foreign_key: true|
|user|reference|null: false, foreign_key: true|
|category|reference|null: false, foreign_key: true|
|brand|reference|foreign_key: true|
|prefecture|reference|null: false, foreign_key: true|
|like|reference|foreign_key: true|
|comment|reference|null: false, foreign_key: true|
|saler|reference|null: false, foreign_key: true|
|buyer|reference|null: false, foreign_key: true|

### Association
- has_many :saler
- has_many :buyer
- has_many :users, through: saler
- has_many :users, through: buyer
- has_many :prices
- has_many :categories
- has_many :brands
- has_many :prefectures
- has_many :likes
- has_many :comments



## Likesテーブル
|Column|Type|Options|
|------|----|-------|
|like|integer|null: false|
|user|reference|null: false, foreign_key: true|
|item|reference|null: false, foreign_key: true|

### Association
- belongs_to :user
- belongs_to :item



## Reviewsテーブル
|Column|Type|Options|
|------|----|-------|
|body|integer|null: false|
|user|reference|null: false, foreign_key: true|

### Association
- belongs_to :user



## Commentsテーブル
|Column|Type|Options|
|------|----|-------|
|body|text|null: false|
|user|reference|null: false, foreign_key: true|
|item|reference|null: false, foreign_key: true|

### Association
- belongs_to :user
- belongs_to :item



## Pricesテーブル
|Column|Type|Options|
|------|----|-------|
|price|integer|null: false|
|item|reference|null: false, foreign_key: true|

### Association
- belongs_to :item



## Brandsテーブル
|Column|Type|Options|
|------|----|-------|
|name|string|null: false|
|item|reference|null: false, foreign_key: true|

### Association
- belongs_to :item



## Categoriesテーブル
|Column|Type|Options|
|------|----|-------|
|name|string|null: false|
|item|reference|null: false, foreign_key: true|

### Association
-has_many: small_categories
- belongs_to :item


## Small_categoriesテーブル
|Column|Type|Options|
|------|----|-------|
|name|string|null: false|
|category|reference|null: false, foreign_key: true|

### Association
- belongs_to :category



## Pointsテーブル
|Column|Type|Options|
|------|----|-------|
|point|integer|null: false|
|history|text|null: false|
|deadline|string|null: false|
|user|reference|null: false, foreign_key: true|

- belongs_to: user



## Todosテーブル
|Column|Type|Options|
|------|----|-------|
|body|string|null: false|
|user|reference|null: false, foreign_key: true|

### Association
- belongs_to :user



## Notificationsテーブル
|Column|Type|Options|
|------|----|-------|
|body|text|null: false|
|user|reference|null: false, foreign_key: true|

### Association
- belongs_to :user


