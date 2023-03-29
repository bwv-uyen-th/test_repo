# refreshTokenテーブル

| 論理テーブル名 | 物理テーブル名 |
| - | - |
| リフレッシュトークン | refreshToken |

### カラム情報

| No. | Tên logic | 物理名 | データ型 | 桁数 | Not NULL | デフォルト |
| - | - | - | - | - | - | - |
| 1 | ID | id | bigint | - | Yes | - |
| 2 | User ID | userId | bigint | - | Yes | - |
| 3 | Refresh Token | refreshToken | varchar | 50 | bigint | - |
| 4 | Created At | createdAt | datetime | - | Yes | - |
| 5 | Updated At | updatedAt | datetime | - | Yes | - |

### インデックス情報

| No. | インデックス名 | カラムリスト | 主キー | ユニーク | 備考 |
| - | - | - | - | - | - |
| 1 | PRIMARY | id | Yes | Yes | - |

### 外部キー情報

| No. | 外部キー名 | カラムリスト | 参照先テーブル名 | 参照先カラムリスト |
| - | - | - | - | - |
| 1 | refreshTokenUserId | userId | user | id |

### 備考

| No. | 物理名 | 備考 |
| - | - | - |
| 1 | id | 自動採番 |
