Phần A:
Câu A1 :
I.
1.Trình duyệt thực hiện DNS lookup để chuyển tên miền shopee.vn thành địa chỉ IP của server.
2.Trình duyệt thiết lập kết nối TCP với server thông qua quá trình bắt tay 3 bước (3-way handshake).
3.Trình duyệt thực hiện TLS handshake (do dùng HTTPS) để thiết lập kết nối bảo mật.
4.Trình duyệt gửi HTTP request (thường là GET) đến server.
5.Server xử lý yêu cầu và trả về HTTP response (bao gồm HTML, CSS, JavaScript, hình ảnh, …).
6.Trình duyệt tải và phân tích các tài nguyên (HTML, CSS, JS, ảnh…).
7.Trình duyệt tiến hành render trang web (tạo DOM, CSSOM, render tree, layout, paint) và hiển thị nội dung lên màn hình.
II.
tab Network cho thấy thông tin:
Tên file (HTML, CSS, JS, ảnh…)
Status Code (200, 404, 500…)
Loại tài nguyên (document, stylesheet, script…)
Thời gian tải (Time)
Kích thước (Size)
Timeline (Waterfall – quá trình tải)

Câu A2:
Sử dụng thẻ <div> thay cho các thẻ semantic như <header>, <main>, <footer>
→ Làm mất ý nghĩa cấu trúc của trang web.
Không sử dụng thẻ <nav> cho menu điều hướng
→ Google không nhận diện được khu vực điều hướng.
Không dùng thẻ heading (<h1>, <h2>, ...) cho tiêu đề sản phẩm
→ Nội dung quan trọng không được ưu tiên trong SEO.
Không sử dụng <article> hoặc <section> để định nghĩa nội dung chính
→ Không thể hiện rõ đây là một sản phẩm/bài viết độc lập.
Lỗi 1: Không dùng <header>
Lỗi 2: Logo không dùng thẻ semantic
Lỗi 3: Menu không dùng <nav>
Lỗi 4:Nội dung chính không dùng <main>
Lỗi 5: Sản phẩm không dùng <article>
sửa lại:
<header>
    <h1 class="logo">ShopTLU</h1>
    <nav>
        <a href="/">Trang chủ</a>
        <a href="/products">Sản phẩm</a>
    </nav>
</header>
<main>
    <article>
        <h2 class="title">iPhone 16 Pro</h2>
        <p class="price">25.990.000đ</p>
        <img src="iphone.jpg" alt="iPhone 16 Pro">
    </article>
</main>
<footer>
    © 2026 ShopTLU
</footer>

Câu A3:
Hộp 1
Text A Text B
Hộp 2
Text C Text D
Hộp 3
Giải thích:
1. <div> là block element
Chiếm toàn bộ chiều ngang
Luôn xuống dòng trước và sau nó
2. <span> và <strong> là inline element
Không xuống dòng
Nằm trên cùng một dòng nếu còn chỗ


Câu A4:
 Sự khác nhau giữa <thead>, <tbody>, <tfoot>

<thead> (Table Head)
Chứa phần tiêu đề của bảng
Thường gồm các hàng <tr> với ô tiêu đề <th>
Giúp trình duyệt và công cụ tìm kiếm hiểu cấu trúc bảng
<tbody> (Table Body)
Chứa nội dung chính của bảng
Bao gồm các hàng dữ liệu <tr> với ô <td>
Là phần lớn nhất của bảng
<tfoot> (Table Footer)
Chứa phần cuối bảng
Thường dùng để hiển thị tổng, ghi chú hoặc kết luận


Không nên dùng table tạo layout vì :

Không đúng ngữ nghĩa (semantic sai)
<table> предназначен cho dữ liệu dạng bảng, không phải để bố cục
Làm giảm khả năng hiểu nội dung của Google → SEO kém

Khó bảo trì và mở rộng
Layout bằng table thường lồng nhiều tầng → code rối

Khó chỉnh sửa khi thay đổi giao diện
Hiệu năng kém

Trình duyệt phải render toàn bộ bảng rồi mới hiển thị
Làm trang load chậm hơn so với dùng CSS (Flexbox, Grid)
Không responsive tốt

Table khó thích ứng với nhiều kích thước màn hình (mobile, tablet)
Gây vỡ layout trên thiết bị nhỏ
Khó kết hợp với CSS hiện đại
Flexbox và Grid linh hoạt hơn rất nhiều
Table bị hạn chế trong việc căn chỉnh layout phức tạp

Phần C:
C1:

<header> <!-- header: chứa phần đầu trang (logo, menu điều hướng) -->
    <div class="logo">Logo</div> <!-- div: nhóm nội dung logo, không mang ý nghĩa semantic riêng -->
    <nav> <!-- nav: khu vực điều hướng chính của website -->
        <ul> <!-- ul: danh sách các mục menu -->
            <li><a href="#">Trang chủ</a></li> <!-- li: từng mục trong menu -->
            <li><a href="#">Sản phẩm</a></li>
        </ul>
    </nav>
</header>

<nav aria-label="breadcrumb"> <!-- nav: điều hướng breadcrumb -->
    <ol> <!-- ol: breadcrumb có thứ tự phân cấp -->
        <li><a href="#">Trang chủ</a></li>
        <li><a href="#">Điện thoại</a></li>
        <li>iPhone 16</li> <!-- phần cuối không cần link -->
    </ol>
</nav>

<main> <!-- main: nội dung chính của trang -->
    <section class="product-detail"> <!-- section: nhóm toàn bộ nội dung chi tiết sản phẩm -->
        <section class="product-images"> <!-- section: nhóm các ảnh sản phẩm -->
            <img src="#" alt="Ảnh sản phẩm 1"> <!-- img: hiển thị ảnh, alt giúp SEO -->
            <img src="#" alt="Ảnh sản phẩm 2">
            <img src="#" alt="Ảnh sản phẩm 3">
            <img src="#" alt="Ảnh sản phẩm 4">
            <img src="#" alt="Ảnh sản phẩm 5">
        </section>
        <article class="product-info"> <!-- article: thông tin sản phẩm là nội dung độc lập -->
            <h1>Tên sản phẩm</h1> <!-- h1: tiêu đề chính quan trọng nhất -->
            <p class="price">Giá</p> <!-- p: hiển thị giá -->
            <p class="rating">Đánh giá sao</p> <!-- p: hiển thị đánh giá -->
            <p class="description">Mô tả sản phẩm</p> <!-- p: mô tả -->
        </article>
    </section>
    <section class="specifications"> <!-- section: nhóm thông số kỹ thuật -->
        <h2>Thông số kỹ thuật</h2> <!-- h2: tiêu đề phụ -->
        <table> <!-- table: dữ liệu dạng bảng -->
            <thead> <!-- thead: phần tiêu đề bảng -->
                <tr>
                    <th>Thông số</th> <!-- th: tiêu đề cột -->
                    <th>Giá trị</th>
                </tr>
            </thead>
            <tbody> <!-- tbody: dữ liệu chính -->
                <tr>
                    <td>...</td> <!-- td: dữ liệu -->
                    <td>...</td>
                </tr>
            </tbody>
        </table>
    </section>
    <section class="reviews"> <!-- section: khu vực đánh giá -->
        <h2>Đánh giá</h2>
        <article class="review"> <!-- article: mỗi bình luận là nội dung độc lập -->
            <p>Người dùng</p>
            <p>Nội dung đánh giá</p>
        </article>
        <article class="review">
            <p>Người dùng</p>
            <p>Nội dung đánh giá</p>
        </article>
    </section>
    <aside class="sidebar"> <!-- aside: nội dung phụ (sản phẩm tương tự) -->
        <h2>Sản phẩm tương tự</h2>
        <ul> <!-- ul: danh sách sản phẩm -->
            <li><a href="#">Sản phẩm 1</a></li>
            <li><a href="#">Sản phẩm 2</a></li>
        </ul>
    </aside>

</main>

<footer> <!-- footer: phần cuối trang -->
    <p>© 2026</p>
</footer>


C2:
Quan điểm “dùng <div> cho mọi thứ” nghe tiện nhưng gây hại về lâu dài. Thứ nhất, SEO: các công cụ tìm kiếm dựa vào cấu trúc semantic để hiểu nội dung trang. Khi bạn dùng <header>, <nav>, <main>, <article>, <h1>…, bot có thể xác định đâu là tiêu đề chính, đâu là nội dung quan trọng. Nếu tất cả đều là <div>, trang trở thành “khối vô nghĩa”, khó được lập chỉ mục và xếp hạng tốt.

Thứ hai, Accessibility (khả năng truy cập): người dùng sử dụng screen reader cần các “landmark” để điều hướng nhanh. Các thẻ semantic cung cấp sẵn vai trò (role) giúp họ nhảy tới menu, nội dung chính, hay footer. Nếu chỉ dùng <div>, bạn phải gán ARIA thủ công và vẫn dễ sai sót, làm trải nghiệm kém hơn.

Ví dụ cụ thể: một trang sản phẩm. Dùng <article> cho sản phẩm, <h1> cho tên, <section> cho mô tả, <nav> cho breadcrumb. Khi đó Google hiểu rõ cấu trúc, còn screen reader có thể đọc “heading level 1: iPhone 16 Pro” và cho phép người dùng nhảy giữa các phần. Nếu thay bằng <div class="title">, thông tin này không được nhận diện đúng.

Tuy vậy, <div> vẫn phù hợp trong các trường hợp không mang ý nghĩa nội dung, ví dụ: bọc layout, chia cột, hoặc làm container cho CSS/JS (grid, flex). Tóm lại, semantic HTML không phải “tốn thời gian”, mà là đầu tư để trang web dễ hiểu, dễ truy cập và tối ưu hơn.

B3:
Lỗi 1: Dòng 1 — <!DOCTYPE> sai cú pháp — Sửa thành <!DOCTYPE html>

Lỗi 2: Dòng 2 — Thiếu thuộc tính lang — Thêm lang="vi" vào thẻ html

Lỗi 3: Dòng 4 — Thẻ <title> không đóng — Thêm </title>

Lỗi 4: Dòng 5 — charset viết sai (utf8) — Sửa thành UTF-8

Lỗi 5: Dòng 8 — Thẻ <h1> không đóng đúng — Sửa thành </h1>

Lỗi 6: Dòng 12 — Thẻ <a> không đóng — Sửa thành </a>

Lỗi 7: Dòng 19 — src không có dấu "" — Thêm dấu "iphone.jpg"

Lỗi 8: Dòng 21 — Thẻ <b> đóng sai vị trí — Sửa thành <strong>...</strong>

Lỗi 9: Dòng 26 — Table thiếu thead/tbody — Thêm cấu trúc chuẩn

Lỗi 10: Dòng 28 — Dùng <td> cho header — Sửa thành <th>

Lỗi 11: Dòng 36 — Dùng 2 thẻ <main> — Chỉ được dùng 1, thay cái thứ 2 bằng <aside>

Lỗi 12: Dòng 41 — Thẻ <p> trong footer không đóng — Thêm </p>

Lỗi 13: Semantic — Thiếu <article> cho sản phẩm — Thêm <article>

Lỗi 14: Semantic — Ảnh thiếu alt — Thêm thuộc tính alt

Lỗi 15: Semantic — Dùng <h3> không hợp lý — Sửa thành <h2>


B4:
1. Các thẻ semantic HTML5 tìm thấy (trên tiki.vn)
 <header>
Vị trí: Phần đầu trang (logo Tiki, thanh tìm kiếm, tài khoản, giỏ hàng)
Chức năng: Chứa phần giới thiệu + điều hướng chính của website
 <main>
Vị trí: Khu vực nội dung chính (banner, flash sale, sản phẩm nổi bật,…)
Chức năng: Chứa toàn bộ nội dung chính của trang web
 <footer>
Vị trí: Cuối trang web
Chức năng: Chứa thông tin liên hệ, chính sách, bản quyền, ứng dụng,...

2. Không thấy table nào trong trang do trang sử dụng flex box và Grid
3.
action="/search"
Khi bấm “Tìm kiếm”, trình duyệt chuyển sang trang /search
method="get"
Dữ liệu tìm kiếm được gửi qua URL

<input type="text" ...> được dùng