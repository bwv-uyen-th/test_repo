# userテーブル

| 論理テーブル名 | 物理テーブル名 |
| - | - |
| ユーザ | user |

### カラム情報

| No. | 論理名 | 物理名 | データ型 | 桁数 | Not NULL | デフォルト |
| - | - | - | - | - | - | - |
| 1 | ID | id | bigint | - | Yes | - |
| 2 | Email | email | varchar | 255 | Yes | - |
| 3 | Password | password | varchar | 255 | Yes | - |
| 4 | User Name | name | varchar | 50 | Yes | - |
| 5 | Section ID | sectionId | bigint | - | Yes | - |
| 6 | Joining Date | joiningDate | date | - | Yes | - |
| 7 | User Flag | userFlag | tinyint | - | Yes | - |
| 8 | Created At | createdAt | datetime | - | Yes | - |
| 9 | Updated At | updatedAt | datetime | - | Yes | - |
| 10 | Deleted At | deletedAt | datetime | - | - | - |

### インデックス情報

| No. | インデックス名 | カラムリスト | 主キー | ユニーク | 備考 |
| - | - | - | - | - | - |
| 1 | PRIMARY | id | Yes | Yes | - |

### 外部キー情報

| No. | 外部キー名 | カラムリスト | 参照先テーブル名 | 参照先カラムリスト |
| - | - | - | - | - |
| 1 | userSectionId | sectionId | section | id |

### 備考

| No. | 物理名 | 備考 |
| - | - | - |
| 1 | id | 自動採番 |
| 7 | User Flag | 0:Admin<br/>1:User |