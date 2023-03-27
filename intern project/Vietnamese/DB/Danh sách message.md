# Định nghĩa message

| Message code | Thời điểm hiển thị | Level | Nội dung | Giá trị set biến {0} | Giá trị set biến {1} | Giá trị set biến {2} | Ghi chú |
| - | - | - | - | - | - | - | - |
| noResults | Khi kết quả search bằng 0 record | INFO | No record. | | | | |
| requiredError | Khi lỗi required | ERROR | {0}は必須項目です。 | Tên hạng mục | | | |
| datatypeError | Khi lỗi kiểu dữ liệu | ERROR | {0}は{1}で入力してください。 | Tên hạng mục | Data-type | | |
| formatError | Khi lỗi format | ERROR | {0}は{1}を正しく入力してください。 | Tên hạng mục | Format | | |
| maxlengthError | Khi lỗi quá max-length | ERROR | {0}は{1}文字以下で入力してください。（現在{2}文字） | Tên hạng mục | Số ký tự giới hạn | Số ký tự hiện tại | |
| minlengthError | Khi lỗi chưa đạt min-length | ERROR | {0}は{1}文字以上で入力してください。（現在{2}文字） | Tên hạng mục | Số ký tự giới hạn | Số ký tự hiện tại | |
| loginFail | Khi login thất bại | ERROR | 入力した情報のいずれかの情報が間違っています。<br/>確認してから再度試してください。 | | | | |
| passwordError | Khi password nhập không đúng quy tắc/ số ký tự | ERROR | パスワードは半角英数字記号で8～20文字で入力してください。 | | | | |
| confirmPasswordError | Khi nội dung nhập ở password và password dùng để xác nhận không khớp | ERROR | 確認用のパスワードが間違っています。 | | | | |
| deleteConfirm | Khi nhấn nút xóa | INFO | この{0}を削除しますか？ | Chỉ định trong thiết kế màn hình | | | |
| fromToError | Khi chỉ định Date To < Date From | ERROR | {0}は{1}前を指定してください。 | Date From | Date To | | |
| filetypeError | Khi chọn file sai định dạng cho phép | ERROR | {0}ファイルを選択してください。 | Định dạng cho phép | | | |
| csvFormatError | Khi chọn file CSV sai format (header) | ERROR | 取り込みファイルの項目数が正しくありません。 |  | | | |
| notExistError | Khi không tồn tại data tương ứng | ERROR | 該当する{0}がありません。 | Tên hạng mục | | | |
| importFail | Khi import thất bại | ERROR | インポートが失敗しました。 |  | | | |
| importSuccess | Khi import thành công | INFO | インポートが成功しました。 |  | | | |
| deleteLoginAccountError | Khi chọn xóa user đang login | ERROR | ログインしているユーザーを削除できません。 |  | | | |
| createSuccess | Khi đăng ký thành công | INFO | {0}登録が成功しました。 | Chỉ định trong thiết kế màn hình | | | |
| updateSuccess | Khi cập nhật thành công | INFO | {0}更新が成功しました。 | Chỉ định trong thiết kế màn hình | | | |
| deleteSuccess | Khi xóa thành công | INFO | {0}を削除しました。 | Chỉ định trong thiết kế màn hình | | | |
| valueError | Khi chỉ định giá trị không được định nghĩa | ERROR | 有効な{0}を入力してください。 | Tên hạng mục | | | |
| invalidToken | Khi refresh token hết hạn | ERROR | INVALID_TOKEN |  | | | |
| duplicateValueError | Khi đăng ký bằng giá trị đã được đăng ký trong DB | ERROR | この{0}は既に登録されています。 | Tên hạng mục | | | |