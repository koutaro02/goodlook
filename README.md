# テーブル設計

## users

| Column | Type | Options |
| ------ | ---- | ------- |
| family_name | string | null: false |
| last_name | string | null: false |
| phone_number | string | null: false |
| email | string | null: false |
| encrypted_password | string | null: false |
| company | references | null: false, foreign_key: true |

### Association

- belongs_to :company
- has_many :user_spots
- has_many :spots, through: user_spots
- has_many :plans

## spots

| Column | Type | Options |
| ------ | ---- | ------- |
| spot_name | string | null: false |
| address | string | null: false |
| latitude | float | null: false |
| longitude | float | null: false |
| text | text |        |

### Association

- has_many :user_spots
- has_many :users, through: user_spots
- has_many :plans

## user_spots

| Column | Type | Options |
| ------ | ---- | ------- |
| user | references | null: false, foreign_key: true |
| spot | references | null: false, foreign_key: true |

### Association

belongs_to :user
belongs_to :spot

## plans

| Column | Type | Options |
| ------ | ---- | ------- |
| content | text |  |
| user | references | null: false, foreign_key: true |
| spot | references | null: false, foreign_key: true |

### Association

- belongs_to :user
- belongs_to :spot

## companys

| Column | Type | Options |
| ------ | ---- | ------- |
| company | string | null: false |
| occupation | string | null: false |
| position | integer | null: false |
| user | references | null: false, foreign_key: true |

### Association

- has_many :user