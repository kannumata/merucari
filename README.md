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

### Association
- has_many :trade
- has_many :items, thorough: trade
- has_many :todos
- has_many :notifications
- has_many :comments
- has_many :likes
- has_many :reviews
- has_many :points



## Adressテーブル
|postal|string|null: false|
|prefecture|string|null: false|
|city|string|null: false|
|adress|string|null: false|
|building|string|null: false|

- belongs_to :user



## Trades（中間テーブル）
|Column|Type|Options|
|------|----|-------|
|user|reference|null: false, foreign_key: true|
|buyer|reference|null: false, foreign_key: { to_table: :users }|
|seller|reference|null: false, foreign_key: { to_table: :users }|
|order|reference|null: false, foreign_key: true|

### Association
- has_many: items, through: orders
- has_many: orders
- belongs_to :users


## Orders（中間テーブル）
|Column|Type|Options|
|------|----|-------|
|trade|reference|null: false, foreign_key: true|
|item|reference|null: false, foreign_key: true|

### Association
- belongs_to :item
- belongs_to :trade



## Itemsテーブル
|Column|Type|Options|
|------|----|-------|
|name|string|null: false|
|description|text|null: false|
|size|integer|
|state|integer|null: false|
|shipping_burden|integer|null: false|
|shipping_way|integer|null: false|
|prefecture|integer|null: false|
|shipping_day|integer|null: false|
|status|integer|null: false|

### Association
- has_many :seller
- has_many :buyer
- has_many :users, through: seller
- has_many :users, through: buyer
- has_many :prices
- has_many :categories
- has_many :brands
- has_many :prefectures
- has_many :likes
- has_many :comments
- has_many :orders



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



## Brandsテーブル
|Column|Type|Options|
|------|----|-------|
|name|string|null: false|
|item|reference|null: false, foreign_key: true|

### Association
- has_many :images
- belongs_to :item



## Categoriesテーブル
|Column|Type|Options|
|------|----|-------|
|name|string|null: false|
|item|reference|null: false, foreign_key: true|

### Association
- has_many: small_categories
- belongs_to :item


## Imagesテーブル
|Column|Type|Options|
|------|----|-------|
|body|string|null: false|
|item|reference|null: false, foreign_key: true|

### Association
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


