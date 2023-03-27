# sectionテーブル

| 論理テーブル名 | 物理テーブル名 |
| - | - |
| 部署 | section |

### カラム情報

| No. | 論理名 | 物理名 | データ型 | 桁数 | Not NULL | デフォルト |
| - | - | - | - | - | - | - |
| 1 | ID | id | bigint | - | Yes | - |
| 2 | Section Name | name | varchar | 50 | Yes | - |
| 3 | Remarks | remarks | text | - | - | - |
| 4 | Leader ID | leaderId | bigint | - | Yes | - |
| 5 | Floor Number | floorNum | int | - | Yes | - |
| 6 | Created At | createdAt | datetime | - | Yes | - |
| 7 | Updated At | updatedAt | datetime | - | Yes | - |
| 8 | Deleted At | deletedAt | datetime | - | - | - |

### インデックス情報

| No. | インデックス名 | カラムリスト | 主キー | ユニーク | 備考 |
| - | - | - | - | - | - |
| 1 | PRIMARY | id | Yes | Yes | - |

### 外部キー情報

| No. | 外部キー名 | カラムリスト | 参照先テーブル名 | 参照先カラムリスト |
| - | - | - | - | - |
| 1 | sectionLeaderId | leaderId | user | id |

### 備考

| No. | 物理名 | 備考 |
| - | - | - |
| 1 | id | 自動採番 |