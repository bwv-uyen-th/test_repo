# Common

### Người phụ trách
(Briswell Co., Ltd ) Wakaki

### Biến môi trường
* Chạy thêm xử lý khi deploy bằng circleCI
    * SECRET_ARN_{Tên môi trường}
* Chạy thêm xử lý khi khởi động server
    * Get biến từ file `.ebextensions/{Tên môi trường}/env-{Tên môi trường}.config`
    * Các biến không tồn tại trong file trên thì get như dưới đây
        * Thông tin SecretsManager
            * accessKeyId: Giá trị lưu trong biến môi trường {AWS_ACCESS_KEY_ID}
            * secretAccessKey: Giá trị lưu trong biến môi trường {AWS_SECRET_ACCESS_KEY}
            * region: Giá trị lưu trong biến môi trường {AWS_REGION}
            * secretId: Giá trị lưu trong biến môi trường {AWS_SECRET_ARN}
        * Dựa trên thông tin SecretsManager, get các thông tin dưới đây từ SecretsManager
            * SESSION_SECRET
            * HASH_SECRET
            * REDIS_HOST
            * REDIS_PORT
### Trình duyệt
Trên PC<br/>Windows (Hệ điều hành mới nhất): Google Chrome, Microsoft Edge (Tất cả trình duyệt ở version mới nhất)<br/>
Mac (Hệ điều hành mới nhất): Google Chrome (version mới nhất)<br/><br/>Trên smartphone<br/>iPhone (Hệ điều hành mới nhất): Safari<br/>
Android (Hệ điều hành mới nhất): Không có gì đặc biệt

### Đối ứng smartphone
※Tất cả màn hình

### Thiết lập công khai đến các công cụ search
Không công khai đến các công cụ search
Thêm settings dưới đây vào file robots.txt, Khi truy cập vào https://{domain}/robots.txt thì từ trên màn hình sẽ tham chiếu đến nội dung này
```
User-agent: *
Disallow: /
```

### Hạn chế truy cập
・Trang công khai "public"<br/>
※Không hạn chế địa chỉ IP.v.v.

### Quyền hạn truy cập
※Tham khảo file [画面一覧] trên Google Drive

### Thiết kế màn hình
※Tham chiếu màn hình Mock html

### Header
| No. | Tên hạng mục | Action | Spec | API(Res) | Ghi chú |
| --- | ----------- | ------------- | - | - | - |
| 0 | System icon | Khi nhấn | Chuyển sang màn hình [S101-1_HOME] | - | - |
| 1 | 動画をアップロード | Khi nhấn | Chuyển sang màn hình [S108-3_動画登録] | - | - |
| 2 | Thông tin login | Khi nhấn | Hiển thị [Tên công ty] và [Hình của login user] và [Tên của login user]<br/>(Hình của login user)<br/>　※Sau khi thay đổi profile image của mình ở màn hình [S104-2_マイ・アカウント編集] or [S201-4_ユーザー編集], thì hiển thị nội dung sau khi thay đổi ở màn hình này<br/>(Tên của login user)<br/>　Chuyển sang màn hình [S104-1_マイ・アカウント表示]<br/>　※Hiển thị ở format [userName] + [さん] |・login.Response.company.name<br/>・login.Response.imagePath ※Tham chiếu phần [Hình user, hình người đăng] của file [common.md] <br/>・login.Response.name | - |
| 3 | Logout | Khi nhấn | Chuyển sang màn hình [S100-1_ログイン] | - | - |
| 4 | 評価アップロード | Khi nhấn | Hiển thị cửa sổ window chọn file<br/>※Tham chiếu file [common.md], mục [CSV file]<br/>Chạy API [fileImport]<br/>Trường hợp failure<br/>　Dừng lại ở màn hình này, hiển thị message API trả về<br/>Trường hợp success<br/>　Hiển thị message [ec-00106] | - | [file] = file đã chọn<br/>[type] = movieRating | 

## In-screen item / Processing privileges control
| No. | Name | privileges | Content |
| --- | ---- | ---- | ---- |
| 4 | 評価アップロード | 0 (システム管理者)<br/>※Chỉ hiển thị trong trường hợp [company.skillPaletteFlag] = 1 (有効) | Không hiển thị với quyền hạn 1(組織管理者), 2(一般ユーザー) |

### Left side menu
user.authority = 0 (システム管理者) or 1 (組織管理者)

| No. | Phân loại     | Action | Spec | API(Res) | API(Param) | Ghi chú |
| --- | ----------- | ------------- | - | - | - | - |
| 0 | 画面権限 | - | Hiển thị cố định là [管理者] | login.Response.authority | - | - |
| 0-1 | ダッシュボード | Khi nhấn | Chuyển sang màn hình [S304-1_ダッシュボード] | - | - | ※Chỉ hiển thị trong trường hợp [company.skillPaletteFlag] = 1 (有効) |
| 0-2 | 動画アップロード視聴履歴 | Khi nhấn | Chuyển sang màn hình [S402-1_動画アップロード視聴履歴出力] | - | - | ※Chỉ hiển thị với quyền hạn 0 (システム管理者) |
| 1 | 動画 | Khi nhấn | ・ユーザー動画<br/>Chuyển sang màn hình [S105-1_動画一覧] ở trạng thái [Danh sách movie của user]<br/>・SkillPalette Library <br/>Chuyển sang màn hình [S105-1_動画一覧] ở trạng thái [Danh sách SkillPalette Library]<br/>・おすすめ設定<br/>Chuyển sang màn hình [S105-1_動画一覧] ở trạng thái [Danh sách recommend for you (あなたへのおすすめ一覧)]<br/>・LEAP Podcast<br/>Chuyển sang màn hình [S105-1_動画一覧] ở trạng thái [Danh sách LEAP Podcast] | - | - | - |
| 2 | ユーザー | Khi nhấn | ・ユーザー一覧<br/>Chuyển sang màn hình [S201-1_ユーザー検索] | - | - | - |
| 3 | 設定 | Khi nhấn | ・階層設定<br/>Chuyển sang màn hình [S303-1_階層設定一覧]<br/>・組織設定<br/>Chuyển sang màn hình [S204-1_組織設定一覧]<br/>・グループ設定<br/>Chuyển sang màn hình [S401-1_グループ設定一覧]<br/>・タグ設定<br/>Chuyển sang màn hình [S203-1_タグ設定一覧] | - | - | - |
| 1 | グループ | Khi nhấn | ・Khi nhấn các groupName<br/>Chuyển sang màn hình [S103-1_タグ・グループ動画一覧] | groupSearch.Response.name | - | ※Chạy API [groupSearch] mỗi lần chuyển màn hình<br/><br/>Hiển thị 10 record　|
| 1-1 | もっと⾒る... | Khi nhấn | Chuyển sang màn hình [S401-4_グループ検索] | - | - | Trường hợp tổng data [groupSearch.Response.Header X-Total-Count] từ 10 record trở xuống thì ẩn hạng mục này |
| 2 | タグ | Khi nhấn | ・Khi nhấn các tagName<br/>Chuyển sang màn hình [S103-1_タグ・グループ動画一覧] | tagSearch.Response.name | - | ※Chạy API [tagSearch] mỗi lần di chuyển màn hình<br/>[sort] = asc<br/><br/>Hiển thị 10 record |
| 3 | もっと⾒る... | Khi nhấn | Chuyển sang màn hình [S102-1_タグ検索] | - | - | Trường hợp tổng data  [tagSearch.Response.Header X-Total-Count] từ 10 record trở xuống thì ẩn hạng mục này |
| 4 | 会社登録 | Khi nhấn | Chuyển sang màn hình [S302-1_会社登録] | - | - | ※Chỉ hiển thị với quyền hạn 0 (システム管理者) |
| 5 | 会社編集 | Khi nhấn | Chuyển sang màn hình [S302-2_会社編集] | - | - | ※Chỉ hiển thị với quyền hạn 0 (システム管理者)<br/>login.Response.company.id |
| 6 | お問い合わせ | Khi nhấn | Chuyển sang màn hình [S301-1_お問い合わせ] | - | - | ※Chỉ hiển thị với quyền hạn 0 (システム管理者) |

user.authority = 2 (一般ユーザー)

| No. | Phân loại | Action | Spec | API(Res) | Ghi chú |
| --- | ----------- | ------------- | - | - | - |
| 0-1 | ダッシュボード | Khi nhấn | Chuyển sang màn hình [S304-1_ダッシュボード] | - | ※Chỉ hiển thị trong trường hợp [company.skillPaletteFlag] = 1 (有効) |
| 1 | グループ | Khi nhấn | ・Khi nhấn các groupName<br/>Chuyển sang màn hình [S103-1_タグ・グループ動画一覧] | groupSearch.Response.name | ※ Chạy API [groupSearch] mỗi lần chuyển màn hình<br/><br/>Hiển thị 10 record　|
| 1-1 | もっと⾒る... | Khi nhấn | Chuyển sang màn hình [S401-4_グループ検索] | - | Trường hợp tổng data [groupSearch.Response.Header X-Total-Count] từ 10 record trở xuống thì ẩn hạng mục này |
| 2 | タグ | Khi nhấn | ・Khi nhấn các tagName<br/>Chuyển sang màn hình [S103-1_タグ・グループ動画一覧] | tagSearch.Response.name | ※Chạy AP [tagSearch] mỗi lần di chuyển màn hình<br/>[sort] = asc<br/><br/>Hiển thị 10 record |
| 3 | もっと⾒る... | Khi nhấn | Chuyển sang màn hình [S102-1_タグ検索] | - | Trường hợp tổng data  [tagSearch.Response.Header X-Total-Count] từ 10 record trở xuống thì ẩn hạng mục này |

### Phần bảng danh sách record
・Về phần header bảng, toàn bộ hiển thị cố định<br/>
・Khi focus vào bảng danh sách record, hiển thị màu nền record đang bị focus khác với các record không bị focus để người dùng nhận biết đang focus vào record nào

### Phân trang
・Ở màn hình search, trường hợp có nhiều kết quả search thì cần thực hiện phân trang kết quả (tiến hành chỉ định số trang và số record trên một trang bên phía API)<br/>
　→Làm giống chức năng paging từ trước đến nay<br/>
・Thanh phân trang nằm bên dưới bảng danh sách record<br/>・Số record tối đa 1 trang thì theo thiết kế trong các màn hình, nếu không có mô tả thì 1 trang hiển thị tối đa 100 record<br/>
・Hiển thị số record hiện tại (該当件数) → Ví dụ: 該当件数　X件中Y件目からZ件目までを表示中 (trong X record kết quả search, đang hiển thị từ record thứ Y - thứ Z)<br/>　※Tổng số record data thì phán đoán từ [Response.Header X-Total-Count]

### Nút [検索] (Search)
・Các màn hình có chức năng search thì có spec chung là khi nhấn [Enter] = nhấn nút search<br/>・Trường hợp kết quả search là 0 record thì hiển thị message [ec-00002]<br/>
・Khi chuyển đến màn hình khác trong trạng thái có nhập ở các hạng mục điều kiện search, rồi quay lại màn hình này lần nữa từ màn hình đã chuyển (bằng cách nhấn nút [戻る] ở các màn hình add/edit), thì lưu giữ nội dung nhập ở các hạng mục điều kiện search rồi hiển thị lại<br/>
　→Giống với nút back của trình duyệt<br>・Sau khi search xong, tự động scroll tới vị trí hạng mục [該当件数] (không quay lại đầu trang)

### Nút [クリア] (Clear)
・Reset về trạng thái default của màn hình

### Khi Submit
・Trong thiết kế các màn hình, những hạng mục có đánh dấu [Y] ở cột Required thì ngoài lúc focus-out, khi submit cũng phải check validate required lần nữa<br/>
　→Khi xảy ra lỗi required thì focus-in vào ô nhập chưa điền (※Thứ tự ưu tiên focus-in là các hạng mục màn hình từ trên xuống dưới)

### Về dữ liệu đang chỉnh sửa
・**Không cần** làm chức năng lock này: Khi truy cập vào dữ liệu đang bị chỉnh sửa bởi người khác, hiển thị message [現在〇〇〇さんが編集中です。], cho chuyển sang màn hình hiển thị thay vì chỉnh sửa

### Chuyển màn hình từ trạng thái đang chỉnh sửa
・Khi chuyển đến màn hình khác trong trạng thái có dữ liệu đang chỉnh sửa dở dang, hiển thị dialog xác nhận [編集中の情報は保存されませんが、よろしいですか？] có 2 button [はい] và [いいえ]. (Chọn [はい] thì chuyển màn hình còn chọn [いいえ] thì đóng dialog, không làm gì cả)<br/>
※Ngoài nhấn nút chuyển màn hình nằm trong hệ thống này, phải làm cho cả trường hợp nhấn nút back, nút đóng tab của browser

### Timeout màn hình
・Thời gian time-out là 2 tiếng<br/>
・Sau khi time-out, hiển thị message [ec-00006]<br/>
※Luồng thao tác sau khi time-out như sau:<br/>
Ví dụ: Trên màn hình đã time-out nhấn submit<br/>
　　　↓<br/>
　　　Chuyển đến màn hình [login]<br/>
　　　↓<br/>
　　　Login lại<br/>
　　　↓Truy cập trực tiếp đến màn hình bị time-out ban nãy

### Hiển thị giá trị số
・Phần số nguyên (trước dấu chấm) hiển thị dấu phẩy [,] ngăn cách mỗi 3 chữ số<br/>
Ví dụ: 1,000,000.00

### Phòng ngừa vỡ CSS do số ký tự vượt quá vùng hiển thị
・Trường hợp UI trở nên không phù hợp nữa vì nguyên nhân CSS vỡ do số ký tự vượt quá vùng hiển thị, lược bỏ phần vượt quá vùng hiển thị và thêm dấu ba chấm (…) vào sau

### Khi lưu hoặc update dữ liệu
・Khi lưu hoặc update ở các màn hình, thì phải thực hiện check validation trước rồi mới chạy API lưu hoặc API update<br/>
・Khi bị lỗi check validation thì hiển thị message lỗi ngay dưới tên hạng mục<br/>
・Về nội dung message hiển thị khi bị lỗi check validation thì tham khảo file [メッセージ一覧] trên Google Drive (Tên hạng mục/ số ký tự/ loại ký tự thì tham khảo ở Item list có trong các thiết kế màn hình)<br/>
・Khi lưu hoặc update mà có lỗi ở hạng mục nhập nào đó thì focus vào hạng mục bị lỗi<br/>
・Khi lưu hoặc update thành công thì hiển thị [登録しました。] (đã đăng kí) or [更新しました。] (đã update) lên màn hình<br/>
・Hiển thị message [登録しました。] or [更新しました。] ở ngay dưới header màn hình (phần trên cùng của Body)

### Hiển thị thời gian
・Thời gian lưu trong DB toàn bộ đều là giờ UTC, khi hiển thị lên màn hìnhphải format sang dạng ngắn hơn (ví dụ YYYY/MM/DD, YYYY/MM.v.v.) thì cần chú ý để chuyển đổi cho chính xác

### Dấu check
・Khi chọn dấu check toàn bộ, chuyển sang trạng thái check toàn bộ/uncheck toàn bộ<br/>・Khi chọn dấu check ở đơn vị từng dòng, chuyển sang trạng thái check/uncheck dòng bị chọn

### Message hiển thị màn hình (※Bao gồm cả message đặc thù của màn hình)
※Tham khảo file [メッセージ一覧] trên Google Drive

### Image file
・Hiển thị tên file bên trên button chọn file <br>・Loại file là [jpeg], [jpg], [png]<br/>
　→Trường hợp chọn file khác với quy định (※Chỉ phán đoán bằng đuôi file xem có phải là file có thể chọn không), hiển thị message [ec-00059]<br/>
・Có thể đính kèm tối đa 1 file<br/>
・Khi chọn file max size là 2MB<br/>
　→Trường hợp vượt quá size thì hiển thị message [ec-00075]

### Movie file
・Hiển thị tên file bên trên button chọn file <br>・Loại file là [mp4], [mov], [MOV]<br>
　→Trường hợp chọn file khác với quy định (※Chỉ phán đoán bằng đuôi file xem có phải là file có thể chọn không), hiển thị message [ec-00086]<br>
・Có thể đính kèm tối đa 1 file<br>
・Khi chọn file max size là 6000MB<br>
　→Trường hợp vượt quá size thì hiển thị message [ec-00087]

### CSV file
・Set loại file là [CSV]<br>
　→Trường hợp lựa chọn loại file khác cái đã quy định (chỉ phán đoán theo đuôi file để xem có phải là file support không), hiển thị message [ec-00105], set parameter [{1:CSV}]
・Có thể đính kèm tối đa 1 file<br>
・Chọn file có file size tối đa là 2MB<br>
　→Trường hợp vượt quá giới hạn file size, hiển thị message [ec-00075]

### Hình user, hình người đăng
・Trường hợp được set thì hiển thị hình tương ứng, trường hợp chưa được set thì hiển thị hình default của màn hình Mock<br/>
・Khi get data , add Cookie gắn chữ kí Common (cloudFrontPolicy, cloudFrontSignature, cloudFrontKeyPairId) vào Header của Request rồi get <br/>	→Đối với các API.Response.imagePath <br/>・Cookie có gắn chữ kí Common sẽ lưu vào Cookie hay Session khi gọi API [login], [refreshToken] để sử dụng<br/>・Chi tiết về cách chỉ định Cookie có gắn chữ kí được hiển thị bên dưới<br/>　Cookie:CloudFront-Policy=XXXXX<br/>　Cookie:CloudFront-Signature=XXXXX<br/>　Cookie:CloudFront-Key-Pair-Id=XXXXX

### Movie
・Khi get data, add Cookie gắn chữ kí Movie (cloudFrontPolicy, cloudFrontSignature, cloudFrontKeyPairId) vào Header của Request rồi get <br/>　→Đối với movieSearchId.Response.movie.moviePath<br/>・Cookie gắn chữ kí Movie thì sẽ sử dụng movieSearchId.Response.movieSignatureCookie (cloudFrontPolicy, cloudFrontSignature, cloudFrontKeyPairId) mỗi lần <br/>　※**Không lưu** vào Cookie hay Session như [Hình user, hình người đăng]<br/>
・Chi tiết về cách chỉ định Cookie có gắn chữ kí được hiển thị bên dưới (**※Giống** với cách chỉ định của [Hình user, hình người đăng] đã nêu trên)<br/>　Cookie:CloudFront-Policy=XXXXX<br/>　Cookie:CloudFront-Signature=XXXXX<br/>　Cookie:CloudFront-Key-Pair-Id=XXXXX

### Nút [削除] (Delete)
・Trước khi chạy API xóa thì hiển thị dialog xác nhận [ec-00045] có hai nút 2 button (削除) (キャンセル)<br/>
　→Chọn [削除] thì chạy API xóa, chọn [キャンセル] thì đóng dialog, không làm gì cả<br/>・Sau khi chạy API xóa thì hiển thị message [ec-00037]<br/>　※Về thiết kế của POPUP thì xem hình của [タグ削除 (tag-delete-popup.md)]<br/>　※Chỉ trong trường hợp chỉ định cử động sau khi xóa ở các màn hình thì gắn cử động giống như dưới đây rồi xóa <br/>　　Hình dung như Sample2 dưới đây (※Suy cho cùng đây là mẫu)<br/>　　　https://webcake.stars.ne.jp/demo/jquery/jquery-animation-sample/

### POPUP
・Sau khi khởi động POPUP, nếu nhấn nút [×] trên POPUP hoặc nhấn ra ngoài POPUP thì đóng POPUP lại

### Các lỗi ngoại lệ
※Khi phát sinh lỗi ngoại lệ, chuyển sang màn hình lỗi chung mà hiển thị các message dưới đây<br/><br/>
・Khi không có quyền truy cập (Lỗi 403)<br/>
　Hiển thị message [アクセスしようとした画面の権限がありません。]<br/>
・Khi không tồn tại màn hình (Lỗi 404)<br/>
　Hiển thị message [アクセスしようとした画面が見つかりません。]<br/>
　※Khi lỗi do truy cập vào id không tồn tại cũng chuyển đến màn hình này<br/>
・Khi phát sinh lỗi quan trọng (Lỗi 500)<br/>
　Hiển thị message [システムエラーが発生しました、システム管理者へお問い合わせください。]

### Xử lý không đồng bộ
・Phương thức truyền đi là [Multipart upload]<br/>・Đối với [preSignedUrl] thì chia file ra rồi upload<br>　→Chia theo đơn vị 10MB (nghĩa là, nếu file nặng 100MB thì khi upload chia thành 10 file)<br>・Insert/update movie thì xử lý không đồng bộ, có thể rời khỏi màn hình thực hiện insert/update<br>
　※Image thì tham chiếu dưới đây<br>
　　![](./image/common1.jpg)<br>

| No. | Tên hạng mục | Action | Spec | 備考 |
| --- | ----------- | ------------- | - | - |
| 1 | Số record upload | - | Tính tổng số file đang upload multipart (số file đang xử lý không đồng bộ bằng browser), rồi hiển thị như dưới đây<br/>→ [◯/◯ 件をアップロードしています] (nghĩa là "Đang upload ◯/◯ file") | - |
| 2 | Thời gian còn lại | - | Tính toán thời gian cần tốn còn lại, rồi hiển thị như dưới đây<br/>→ [残り ◯◯時間] (trường hợp đơn vị giờ), [残り ◯◯分] (trường hợp đơn vị phút) | - |
| 3 | Tên file | - | Hiển thị tên file hiện tại đang upload (※Là tên file lúc upload) |  |
| 4 | Trạng thái xử lý | - | Tính toán tiến độ hiện tại đã hoàn thành được bao nhiêu % trong tổng thể (100%), rồi hiển thị như dưới đây<br/>→  Hiển thị [◯◯% アップロード済み] (nghĩa là "Đã upload xong ◯◯%")<br/>※**Lý tưởng là chia nhỏ tới 1%**, tuy nhiên nếu khó làm thì tính theo [tổng số file đã upload xong / tổng số file cần upload] | - |
| 5 | Dừng upload | Khi nhấn | ・Chạy API [movieUploadFinish]**(※Tuy nhiên, không chạy sau khi phát sinh case [Trường hợp thực hiện duplicate trình duyệt hay duplicate tab trong khi upload])**<br/>　[id] = movie.id của movie bị nhấn nút dừng<br/>　[stop] = 1 (キャンセル)<br/>Trường hợp failure<br/>　Hiển thị message API trả về<br/>Trường hợp success<br/>　Hiển thị message [ec-00091]<br /><br />・Đóng task xử lý đồng bộ của đối tượng nhấn<br />　→Trường hợp tất cả task xử lý đồng bộ không có, ẩn vùng hiển thị xử lý không động bộ khỏi màn hình | - |
| 6 | Lỗi upload | Khi bị lỗi | Trong lúc upload mà phát sinh vấn đề do màn hình, S3, khác...thì hiển thị message [ec-00089] ở phân trên cùng của màn hình<br>Hiển thị message [ec-00103] + button 再開 (đặt bên trái button ×) ở phần Tình trạng xử lý của xử lý bất đồng bộ | - |
| 7 | Upload lại | Khi nhấn | Thực hiện lại xử lý upload của phần chưa được hoàn thành và hiển thị (%) tiến độ hiện tại giống với hạng mục [Tình trạng xử lý]<br>　・Ví dụ (Trường hợp part 3): Trường hợp trước khi bị gián đoạn thì part1=100%, part2=50%, part3=0%, sau đó nhấn nút 再開, hiển thị tiến độ là 33%<br>　　・Part chưa được xử lý xong thì sẽ được thực hiện xử lý lại từ 0% nên part1=100%, part2=0%, part3=0%<br><br>Trường hợp không thể thực hiện lại xử lý upload thì chạy như bên dưới<br>・Chạy [movieUploadFinish]<br/>[id] = movie.id của movie bị dừng<br />　[stop] = 2 (エラー)<br/> Trường hợp failure<br/>　　Hiển thị message API trả về<br/>Trường hợp success<br/>Hiển thị message [ec-00107]<br/><br/>・Hiển thị message [ec-00108] trong Trạng thái xử lý của xử lý bất đồng bộ (Button 再開 không cần, button × thì cần) | - |
・Trong lúc upload, nếu định đóng tab trình duyệt hoặc đóng hẳn trình duyệt, hiển thị dialog xác nhận gồm message [ec-00093] và button [はい] [いいえ]<br>>Trường hợp success<br/>・Trường hợp thực hiện duplicate trình duyệt hay duplicate tab trong khi upload, chạy [movieUploadFinish]<br/>　[id] = movie.id của movie bị dừng upload<br />　[stop] = 2 (エラー)<br/>Trường hợp failure<br/>　　Hiển thị message API trả về<br/>Trường hợp success<br/>　　Hiển thị message [ec-00108] trong Trạng thái xử lý của xử lý bất đồng bộ (Button 再開 không cần, button × thì cần)<br><br>・Sau khi upload xong toàn bộ part, chạy API [movieUploadFinish]<br>　[id] = movie.id của movie đã upload xong<br/>　[uploadId] = movieCreate(movieReUpload).Response.uploadId<br/>　[s3PreMovieFilePath] = movieCreate(movieReUpload).Response.S3PreMovieFilePath<br/>　[parts.eTag] = [eTag mà S3 trả về sau khi upload xong<br/>　[parts.partNumber] = 1... (giản lược)<br/>Trường hợp failure<br/>　　Hiển thị message API trả về<br/>Trường hợp success<br/>　　Hiển thị message [ec-00092]
