# Bảng refreshToken

| Tên logic bảng | Tên vật lý bảng |
| - | - |
| リフレッシュトークン | refreshToken |

### Thông tin column

| No. | Tên logic | Tên vật lý | Data type | Length | Not NULL | Default |
| - | - | - | - | - | - | - |
| 1 | ID | id | bigint | - | Yes | - |
| 2 | User ID | userId | bigint | - | Yes | - |
| 3 | Refresh Token | refreshToken | varchar | 50 | bigint | - |
| 4 | Created At | createdAt | datetime | - | Yes | - |
| 5 | Updated At | updatedAt | datetime | - | Yes | - |

### Thông tin Indexes

| No. | Tên Indexes | Column list | Khóa chính | Unique | Ghi chú |
| - | - | - | - | - | - |
| 1 | PRIMARY | id | Yes | Yes | - |

### Thông tin khóa ngoại

| No. | Tên khóa ngoại | Column list | Tên bảng tham chiếu | Column list tham chiếu |
| - | - | - | - | - |
| 1 | refreshTokenUserId | userId | user | id |

### Ghi chú

| No. | Tên vật lý | Ghi chú |
| - | - | - |
| 1 | id | Auto-increment |