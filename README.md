Chiến dịch Tái thiết Portal TechBugs
Repository: https://github.com/dieppham999/portal_techbugs

Bài thực hành mô tả hai nhánh tính năng độc lập, hợp nhất bằng Git merge và nâng cấp cấu trúc HTML theo ngữ nghĩa. Các đường dẫn commit dưới đây là bằng chứng có thật được đối chiếu trên GitHub ngày 12/11/2026, không phải sơ đồ dự kiến.
1. Bằng chứng lịch sử Git
Sự kiện	Commit	Kiểm chứng
Commit gốc chứa Legacy Code	128e2461d	Xem commit
Nhánh feature/nav-bar: menu	284c351c1	Xem commit
Nhánh feature/semantic-content: nội dung	1668177e8	Xem commit
Merge menu vào main (2 parents)	ca35ea9a5	Xem merge commit
Merge nội dung vào main (2 parents)	7e493c2e1	Xem merge commit
Sửa lỗi phát sinh sau merge	7f371d1a6	Xem commit


Branches: feature/nav-bar · feature/semantic-content · main

Quan hệ nhánh đã được xác minh: hai commit 284c351c1 và 1668177e8 đều có parent là 128e2461d. Merge ca35ea9a5 có parents 128e2461d và 284c351c1; merge 7e493c2e1 có parents ca35ea9a5 và 1668177e8.

Lưu ý: Đồ thị ở trên là minh họa rút gọn. Để tạo ảnh bằng chứng đúng định dạng và đúng thứ tự, chạy lệnh sau trong bản clone của repository, sau đó chụp màn hình terminal:
git fetch --all --prune
git log --all --oneline --graph --decorate
git branch -a
Xem thêm GitHub network graph.
2. Chuyển đổi HTML semantic
Legacy HTML	Phần tử thay thế	Lý do
.top-bar	<header>	Phần đầu trang
.menu	<nav><ul><li><a>	Điều hướng chính và danh sách liên kết
.main-content	<main>	Nội dung chính duy nhất
Nhóm tin có tiêu đề	<section>	Nhóm nội dung liên quan
.news-block	<article>	Tin có thể đứng độc lập
.title	<h3>	Heading đúng cấp trong nhóm tin
.author, .text	<p>, <time>	Nội dung dạng đoạn và ngày máy đọc được
.bottom-bar	<footer>	Thông tin cuối trang


Mỗi mục menu là một <li> chứa một <a>; không đặt nhiều link trong cùng một <li>. CSS đặt trong styles.css; không dùng style inline. Các liên kết nội bộ được trỏ tới ID có thật trên trang. Phần sản phẩm, tuyển dụng và liên hệ là nội dung minh họa, chưa phải thông tin doanh nghiệp chính thức.
3. Giải thích vấn đáp
Tại sao chọn <ul> thay vì <ol>? Menu chỉ là tập hợp các liên kết, thứ tự không quyết định ý nghĩa. <ol> phù hợp khi thứ tự là dữ kiện quan trọng, ví dụ các bước cần thực hiện tuần tự.

Tại sao <nav> bọc ngoài <ul>? <nav> cung cấp landmark điều hướng cho công nghệ hỗ trợ; <ul> biểu thị các mục có quan hệ danh sách. Không phải tất cả nhóm liên kết đều nhất thiết đặt trong <nav>, chỉ các khu vực điều hướng quan trọng.

Vì sao tạo nhánh thứ hai từ main? Hai nhánh cùng bắt đầu từ commit 128e2461d. Nếu tạo nhánh semantic trong lúc đang đứng ở nhánh menu, nhánh mới sẽ kế thừa cả commit menu, không còn độc lập.

git merge hoạt động như thế nào? Khi có lịch sử phân nhánh, Git thường thực hiện three-way merge: tìm merge-base (tổ tiên chung), so sánh với hai đầu nhánh và kết hợp thay đổi. --no-ff yêu cầu tạo merge commit ngay cả khi có thể fast-forward; đây không phải một lệnh Git khác bí mật được chạy ngầm.

Nếu hai nhánh sửa cùng dòng? Chạy git status, mở file bị đánh dấu conflict; giữ nội dung mong muốn và xóa <<<<<<<, =======, >>>>>>>. Kiểm tra HTML, chạy git add index.html và git commit để hoàn tất merge. Có thể kiểm tra tổ tiên chung bằng git merge-base main feature/nav-bar (thời điểm trước merge) hoặc dùng commit SHA cụ thể trong lịch sử.

Nếu đang làm dở phải sửa gấp ở main? Có thể dùng git stash push -m "WIP nav", chuyển nhánh git switch main, sửa/commit, quay lại nhánh tính năng rồi git stash pop. Nếu thay đổi dở có giá trị lâu dài, tạo commit WIP trên nhánh riêng cũng là lựa chọn.
4. Kiểm thử và hồ sơ nộp
- [x] Đã xác minh 3 nhánh trên GitHub ngày 12/11/2026.
- [x] Đã xác minh 2 merge commit thực tế với 2 parent.
- [x] Có commit gốc chứa Legacy Code.
- [x ] Sau khi cập nhật, kiểm tra index.html trên main có đầy đủ HTML semantic.
- [ x] Chụp ảnh git log --all --oneline --graph --decorate và đưa vào repository.
- [x ] Bổ sung các prompt thực tế trong ai_prompt_log.md nếu có lịch sử chat trước đây.
- [ x] Mở trình duyệt kiểm tra giao diện và menu sau khi cập nhật.
Hồ sơ: Repository · index.html · styles.css · ai_prompt_log.md · README này.