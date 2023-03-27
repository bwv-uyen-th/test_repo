# Bảng section

| Tên logic bảng | Tên vật lý bảng |
| - | - |
| 部署 | section |

### Thông tin column

| No. | Tên logic | Tên vật lý | Data type | Length | Not NULL | Default |
| - | - | - | - | - | - | - |
| 1 | ID | id | bigint(unsigned) | - | Yes | - |
| 2 | Section Name | name | varchar | 255 | Yes | - |
| 3 | Remarks | remarks | text | - | - | - |
| 4 | Leader ID | leaderId | bigint(unsigned) | - | Yes | - |
| 5 | Floor Number | floorNum | int(unsigned) | - | Yes | - |
| 6 | Created At | createdAt | datetime | - | Yes | - |
| 7 | Updated At | updatedAt | datetime | - | Yes | - |
| 8 | Deleted At | deletedAt | datetime | - | - | - |

### Thông tin Indexes

| No. | Tên Indexes | Column list | Khóa chính | Unique | Ghi chú |
| - | - | - | - | - | - |
| 1 | PRIMARY | id | Yes | Yes | - |

### Thông tin khóa ngoại

| No. | Tên khóa ngoại | Column list | Tên bảng tham chiếu | Column list tham chiếu |
| - | - | - | - | - |
| 1 | sectionLeaderId | leaderId | user | id |

### Ghi chú

| No. | Tên vật lý | Ghi chú |
| - | - | - |
| 1 | id | Auto-increment |