# AI PROMPT LOG

---
### Prompt 01

**Prompt:**

> HTML Semantic là gì? Tại sao sử dụng các thẻ header, nav, main, section, article và footer lại tốt hơn việc sử dụng quá nhiều div?

**Mục đích:** Hiểu bản chất của Semantic HTML trước khi thiết kế lại website.

**Kiến thức rút ra:**

- `div` không mang ý nghĩa ngữ nghĩa cụ thể.
- Các thẻ Semantic mô tả vai trò của từng khu vực.
- HTML Semantic hỗ trợ công nghệ trợ năng và giúp công cụ tìm kiếm hiểu cấu trúc nội dung.

### Prompt 02

**Prompt:**

> Tôi đang chuyển đổi trang tin tức từ div sang Semantic HTML. Hãy giải thích sự khác nhau giữa section và article, đồng thời chỉ ra khi nào không nên dùng section.

**Mục đích:** Tránh thay thế mọi `div` bằng `section` một cách máy móc.

**Kiến thức rút ra:**

- `article` phù hợp với một bài viết hoặc đơn vị nội dung độc lập.
- `section` phù hợp với một nhóm nội dung có chủ đề riêng.
- Tiêu đề, ngày tháng và đoạn văn thông thường nên dùng `h1`–`h6`, `time`, `p`.

### Prompt 03

**Prompt:**

> Vì sao menu điều hướng nên dùng cấu trúc nav > ul > li > a thay vì đặt nhiều thẻ a cạnh nhau? Mỗi li có nên chứa nhiều liên kết điều hướng không?

**Mục đích:** Thiết kế menu theo cấu trúc danh sách dễ hiểu và phù hợp với yêu cầu bài tập.

**Kiến thức rút ra:**

- `nav` xác định vùng điều hướng chính.
- `ul` biểu diễn danh sách không có thứ tự ưu tiên.
- Mỗi mục menu độc lập nên nằm trong một `li`.
- Thẻ `a` đại diện cho liên kết có thể điều hướng.

---
### Prompt 04

**Prompt:**

> Trong một dự án Git, tại sao cần commit Legacy Code trên nhánh main trước khi tạo các nhánh feature? Nếu chưa commit mà tạo nhánh thì có rủi ro gì?

**Mục đích:** Hiểu vai trò của commit gốc và điểm xuất phát chung.

**Kiến thức rút ra:**

- Commit gốc tạo mốc lịch sử xác định.
- Các nhánh feature có thể xuất phát từ cùng một commit.
- Thay đổi chưa commit có thể đi theo khi chuyển nhánh, hoặc khiến Git từ chối chuyển nhánh nếu gây ghi đè.

### Prompt 05

**Prompt:**

> Tôi muốn tạo hai nhánh feature/nav-bar và feature/semantic-content độc lập từ main. Vì sao phải checkout về main trước khi tạo nhánh thứ hai?

**Mục đích:** Tránh nhánh Semantic vô tình kế thừa commit của nhánh Menu.

**Kiến thức rút ra:**

- Lệnh tạo nhánh mặc định dùng commit HEAD hiện tại làm điểm xuất phát.
- Nếu đang ở `feature/nav-bar`, tạo nhánh mới có thể khiến nhánh đó kế thừa lịch sử menu.
- Chuyển về `main` giúp hai nhánh có chung điểm xuất phát.

### Prompt 06

**Prompt:**

> Nếu đang sửa menu trên feature/nav-bar nhưng cần chuyển sang main để xử lý công việc gấp, tôi nên sử dụng git stash hay git commit? Hãy giải thích sự khác nhau.

**Mục đích:** Hiểu cách bảo vệ thay đổi chưa hoàn thành.

**Kiến thức rút ra:**

- `git stash` có thể lưu tạm thay đổi trong working directory.
- `git commit` ghi nhận thay đổi vào lịch sử của nhánh.
- Có thể dùng `git stash pop` để áp dụng lại thay đổi đã lưu tạm.

---
### Prompt 07

**Prompt:**

> Tôi đã chuyển top-bar thành header, main-content thành main, news-block thành article và bottom-bar thành footer. Làm thế nào để tự kiểm tra các thẻ đã đúng ngữ nghĩa mà không nhờ AI viết lại toàn bộ HTML?

**Mục đích:** Xây dựng quy trình tự kiểm tra và phát hiện lỗi Semantic HTML.

**Kiến thức rút ra:**

- Mỗi trang nên xác định rõ nội dung chính.
- Các bài viết độc lập có thể dùng `article`.
- Không nên dùng `section` chỉ để thay thế một dòng văn bản.
- Có thể kiểm tra cấu trúc bằng trình duyệt và HTML Validator.

### Prompt 08

**Prompt:**

> Sau khi commit trên hai nhánh feature/nav-bar và feature/semantic-content, tôi dùng lệnh Git nào để chứng minh rằng chúng được phát triển độc lập từ cùng một commit gốc?

**Mục đích:** Biết cách kiểm tra lịch sử Git trước khi merge.

**Kiến thức rút ra:**

Các lệnh hữu ích:

- `git log --graph --oneline --all --decorate`
- `git merge-base feature/nav-bar feature/semantic-content`
- `git diff main..feature/nav-bar`
- `git diff main..feature/semantic-content`

---

### Prompt 09

**Prompt:**

> Khi thực hiện git merge feature/nav-bar vào main, Git sử dụng cơ chế gì để kết hợp các thay đổi? Hãy giải thích merge-base và three-way merge bằng ví dụ đơn giản.

**Mục đích:** Hiểu nguyên lý merge thay vì chỉ ghi nhớ cú pháp.

**Kiến thức rút ra:**

Git sử dụng lịch sử chung để xác định điểm xuất phát. Khi cần three-way merge, Git so sánh phiên bản gốc với hai phía thay đổi để tạo ra kết quả hợp nhất.

Lệnh `git merge --no-ff` giúp duy trì merge commit riêng khi hợp nhất thành công.

### Prompt 10

**Prompt:**

> Hãy đưa ra một tình huống giả định trong đó feature/nav-bar và feature/semantic-content cùng chỉnh sửa một vùng HTML khiến Git không thể tự merge. Tôi cần nhận biết và giải quyết conflict như thế nào?

**Mục đích:** Chuẩn bị cho tình huống xung đột trong quá trình tích hợp mã nguồn.

**Kiến thức rút ra:**

Khi có conflict, Git có thể chèn các dấu:

- `<<<<<<< HEAD`
- `=======`
- `>>>>>>> feature/semantic-content`

Quy trình xử lý:

1. Dùng `git status` để xác định file bị conflict.
2. Mở file và đối chiếu thay đổi của hai phía.
3. Chỉnh sửa để giữ nội dung phù hợp.
4. Xóa toàn bộ dấu conflict.
5. Dùng `git add` và hoàn tất merge.

### Prompt 11 

**Prompt:**

> Sau khi merge cả hai nhánh vào main, tôi cần kiểm tra những gì để chứng minh lịch sử Git có phân nhánh và merge thực sự? Merge commit khác commit thông thường ở điểm nào?

**Mục đích:** Chuẩn bị bằng chứng Git để nộp và giải thích với Tech Lead.

**Kiến thức rút ra:**

- Commit thông thường thường có một parent.
- Merge commit thường có từ hai parent.
- `git log --graph --all --decorate --oneline` giúp kiểm tra cấu trúc phân nhánh.
- `git show --pretty=raw <commit>` cho phép kiểm tra parent của commit.

---

### Prompt 12 – Phân tích kết quả chấm bài

**Prompt:**

> Tôi đã nộp repository TechBugs nhưng chỉ đạt 32/100. Giảng viên nhận xét HTML sai cấu trúc li, dùng section không đúng, README thiếu bằng chứng và thiếu ai_prompt_log.md. Hãy giúp tôi phân tích nguyên nhân và xây dựng kế hoạch khắc phục mà không viết lại toàn bộ bài hộ tôi.

**Mục đích:** Xác định nguyên nhân mất điểm theo từng tiêu chí đánh giá.

**Kiến thức rút ra:**

- Cần phân biệt giữa lịch sử Git thực tế và tài liệu mô tả lịch sử Git.
- Mỗi liên kết menu độc lập cần đặt trong một `li` riêng theo cấu trúc bài tập.
- Không sử dụng `section` thay cho `h2`, `p` hoặc `time`.
- README phải phản ánh trạng thái thực tế của repository.
- Prompt log cần thể hiện quá trình tìm hiểu, phân tích và sửa lỗi.



