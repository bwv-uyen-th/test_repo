# Bảng user

| Tên logic bảng | Tên vật lý bảng |
| - | - |
| ユーザ | user |

### Thông tin column

| No. | Tên logic | Tên vật lý | Data type | Length | Not NULL | Default |
| - | - | - | - | - | - | - |
| 1 | ID | id | bigint | - | Yes | - |
| 2 | Email | email | varchar | 255 | Yes | - |
| 3 | Password | password | varchar | 255 | Yes | - |
| 4 | User Name | name | varchar | 50 | Yes | - |
| 5 | Section ID | sectionId | bigint | - | Yes | - |
| 6 | Joining Date | joiningDate | date | - | Yes | - |
| 7 | User Flag | userFlag | tinyint | - | Yes | - |
| 8 | Created Date | createdAt | datetime | - | Yes | - |
| 9 | Updated Date | updatedAt | datetime | - | Yes | - |
| 10 | Deleted Date | deletedAt | datetime | - | - | - |

### Thông tin Indexes

| No. | Tên Indexes | Column list | Khóa chính | Unique | Ghi chú |
| - | - | - | - | - | - |
| 1 | PRIMARY | id | Yes | Yes | - |

### Thông tin khóa ngoại

| No. | Tên khóa ngoại | Column list | Tên bảng tham chiếu | Column list tham chiếu |
| - | - | - | - | - |
| 1 | userSectionId | sectionId | section | id |

### Ghi chú

| No. | Tên vật lý | Ghi chú |
| - | - | - |
| 1 | id | Auto-increment |
| 7 | User Flag | 0:Admin<br/>1:User |