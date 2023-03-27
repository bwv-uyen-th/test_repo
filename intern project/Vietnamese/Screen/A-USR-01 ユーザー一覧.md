# A-USR-01 ユーザー一覧

### Người phụ trách

Maeda

### Portrait

![](../../image/UserList.png)

## Danh sách hạng mục

### Phần điều kiện search

| No. | Tên hạng mục | Cho nhập/ Hiển thị | Chủng loại | Required | Max-length | Giới hạn nhập | Default | Request API [userSearch] |
| - | - | - | - | - | - | - | - | - |
| 1 | User Name | Cho nhập | text | - | 50 | - | - | name |
| 2 | User Flag | Cho nhập | check | - | - | 1:Admin<br/>2:User | - | userFlag |
| 3 | Joining Date From | Cho nhập | date | - | - | yyyy/mm/dd | - | joiningDateFrom |
| 4 | Joining Date To | Cho nhập | date | - | - | yyyy/mm/dd | - | joiningDateTo |
| 5 | Search | Hiển thị | button | - | - | - | - | - |
| 6 | Clear | Hiển thị | button | - | - | - | - | - |

### Phần kết quả search

| No. | Tên hạng mục | Cho nhập/ Hiển thị | Chủng loại | Required | Max-length | Giới hạn nhập | Default | Response API [userSearch] |
| - | - | - | - | - | - | - | - | - |
| 7 | User Name | Hiển thị | link | - | - | - | - | name |
| 8 | Email | Hiển thị | label | - | - | - | - | email |
| 9 | Section Name | Hiển thị | label | - | - | - | - | sectionName |
| 10 | Joining Date | Hiển thị | label | - | - | - | - | joiningDate |
| 11 | User Flag | Hiển thị | label | - | - | 0:Admin<br/>1:User | - | userFlag |

### Phần button

| No. | Tên hạng mục | Cho nhập/ Hiển thị | Chủng loại | Required | Max-length | Giới hạn nhập | Default |
| - | - | - | - | - | - | - | - |
| 12 | New | Hiển thị | button | - | - | - | - |
| 13 | Export CSV | Hiển thị | button | - | - | - | - |

## Khái quát xử lý

### Quyền hạn

| No. | Tên hạng mục | Cho nhập/ Hiển thị |
| - | - | - |
| 7 | User Name | Quyền hạn [Admin]: Hiển thị dưới dạng link<br/>Quyền hạn khác: Hiển thị dưới dạng label |
| 12 | New | Quyền hạn [Admin]: Hiển thị<br/>Quyền hạn khác: Không hiển thị |
| 13 | Export CSV | Quyền hạn [Admin]: Hiển thị<br/>Quyền hạn khác: Không hiển thị |

### Hiển thị ban đầu

| No. | Tên hạng mục | Spec |
| - | - | - |
| - | Khởi động màn hình | Call API [userSearch] bằng giá trị nhập trong phần điều kiện search, gửi limit = 20, offset = 0<br/>　Trường hợp thất bại<br/>　　Hiển thị lỗi API trả về<br/>　Trường hợp thành công<br/>　　Phản ánh data API trả về vào phần kết quả search |
| - | Phần điều kiện search | Trường hợp trong session có lưu điều kiện search, phản ánh điều kiện search lưu trong session vào phần điều kiện search<br/>Trường hợp trong session không lưu điều kiện search, hiển thị phần điều kiện search bằng giá trị default |
| - | Phần kết quả search | Trường hợp 0 record thì hiển thị message [noResults], không hiển thị header của bảng |
| 3 | Joining Date From | Hiển thị place holder text [YYYY/MM/DD] |
| 4 | Joining Date To | Hiển thị place holder text [YYYY/MM/DD] |
| 13 | Export CSV | Trường hợp 0 record, không hiển thị |

### Event nhấn nút/ nhấn link

| No. | Tên hạng mục | Spec |
| - | - | - |
| 5 | Search | 1. Thực hiện check validation bằng JS, nếu có dữ liệu không hợp lệ thì hiển thị lỗi theo xử lý chung<br/>　Check format date. Error message [formatError], truyền {1} = 日付<br/>　Nếu nhập [Joining Date From] > [Joining Date To] thì hiển thị lỗi [fromToError]<br/><br/>2. Call API [userSearch] và cập nhật lại kết quả search<br/>　Lưu điều kiện search vào session |
| 6 | Clear | Reset điều kiện search được nhập trên màn hình và trong session về default |
| 7 | User Name | Chuyển đến màn hình [A-USR-02 ユーザー新規更新削除], truyền user.id bị nhấn nút |
| 12 | New | Chuyển đến màn hình [A-USR-02 ユーザー新規更新削除], không truyền gì cả |
| 13 | Export CSV | Xuất file CSV<br/>Tham khảo phần "Export CSV Format" |

## Phần Export CSV Format

| Header | Content |
| - | - |
| ID | user.id |
| User Name | user.name |
| Email | user.email |
| Section ID | user.sectionId |
| Section Name | section.name |
| Joining Date | user.joiningDate |
| User Flag | user.userFlag |
| Created At | user.createdAt |
| Updated At | user.updatedAt |

### Xử lý

Tên file: user_yyyymmddhhmmss<br/>
　※yyyymmddhhmmss: datetime xuất file theo giờ JST<br/>
Xuất ra toàn bộ record kết quả search<br/>
Thứ tự sort data giống trên màn hình<br/>
Header và data xuất ra phải rào trong dấu 2 nháy<br/>Trường hợp không tồn tại section.id ràng buộc với user.sectionId mà chưa bị xóa logic, hiển thị rỗng vào hạng mục [Section Name]