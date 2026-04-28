Phần A:
A1:
1. type="email" → Ô nhập text, trình duyệt kiểm tra có dạng email (có @, domain) → Dùng cho đăng ký tài khoản / nhập email khách hàng

2. type="password" → Ô nhập ký tự bị ẩn (hiện dấu •••) → Không có validation đặc biệt (trừ required/minlength) → Dùng cho đăng nhập / tạo mật khẩu

3. type="text" → Ô nhập văn bản bình thường → Không có validation mặc định → Dùng cho tên sản phẩm, tên người dùng

4. type="number" → Ô nhập số, có nút tăng/giảm → Chỉ cho nhập số, có thể giới hạn min/max → Dùng cho số lượng sản phẩm

5. type="tel" → Ô nhập số điện thoại → Không kiểm tra chặt nhưng hỗ trợ bàn phím số trên mobile → Dùng cho nhập số điện thoại giao hàng

6. type="url" → Ô nhập link → Tự kiểm tra định dạng URL (http/https) → Dùng cho nhập website (ví dụ shop đối tác)

7. type="date" → Giao diện chọn ngày (calendar) → Chỉ cho chọn ngày hợp lệ → Dùng cho chọn ngày giao hàng / ngày sinh

8. type="radio" → Nút chọn tròn (chỉ chọn 1 trong nhiều) → Không có validation riêng (thường dùng required) → Dùng cho chọn phương thức thanh toán

9. type="checkbox" → Ô vuông tích chọn (có thể chọn nhiều) → Không có validation riêng → Dùng cho chọn nhiều sản phẩm / điều khoản

10. type="file" → Nút chọn file từ máy → Có thể giới hạn loại file (accept) → Dùng cho upload ảnh sản phẩm / avatar

A2:

1. type="text" required value="" →  Không submit
→ Vì thuộc tính required bắt buộc phải có giá trị, nhưng ô đang trống → trình duyệt chặn và báo “Please fill out this field”.

2. type="email" value="abc" →  Không submit
→ Vì "abc" không đúng định dạng email (thiếu @ và domain) → HTML5 tự validate email và chặn submit.

3. type="number" min="1" max="10" value="15" →  Không submit
→ Vì 15 > max (10) → vi phạm ràng buộc phạm vi → trình duyệt báo lỗi kiểu “Value must be ≤ 10”.

4. type="text" pattern="[0-9]{10}" value="abc123" →  Không submit
→ Pattern yêu cầu đúng 10 chữ số, nhưng "abc123" vừa có chữ vừa không đủ 10 số → không khớp regex → bị chặn.

5. type="password" minlength="8" value="123" →  Không submit
→ Độ dài chỉ 3 ký tự < minlength (8) → không đạt yêu cầu độ dài → trình duyệt chặn và báo lỗi.

-> sau khi validation thì cho kết quả đúng dự đoán 

A3:
<label for="email"> quan trọng vì nó liên kết trực tiếp với ô input, giúp screen reader đọc đúng tên của trường nhập liệu. Khi người dùng dùng công cụ hỗ trợ (ví dụ người khiếm thị), họ sẽ nghe được “Email, edit text” thay vì chỉ “edit text” không rõ ý nghĩa. Ngoài ra, khi click vào <label> thì con trỏ cũng tự động focus vào input, giúp tăng trải nghiệm sử dụng.

<fieldset> và <legend> được dùng khi cần nhóm nhiều input liên quan lại với nhau, đặc biệt trong form có nhiều lựa chọn. <legend> đóng vai trò như tiêu đề của nhóm, giúp screen reader hiểu ngữ cảnh chung của các input bên trong.
 ví dụ:
<fieldset>
  <legend>Phương thức thanh toán</legend>
  <input type="radio" name="pay" id="cod">
  <label for="cod">Thanh toán khi nhận hàng</label>

  <input type="radio" name="pay" id="card">
  <label for="card">Thẻ ngân hàng</label>
</fieldset>

aria-label được dùng khi không có nội dung hiển thị rõ ràng để mô tả element, ví dụ icon button (nút chỉ có hình kính lúp). Nó cung cấp “tên” cho screen reader mà người dùng không nhìn thấy.
Không nên dùng aria-label khi đã có <label> vì sẽ gây trùng lặp hoặc xung đột thông tin. Trình đọc màn hình có thể đọc hai lần hoặc ưu tiên aria-label và bỏ qua <label>, làm giảm tính rõ ràng.


A4:
loading="lazy" trì hoãn việc tải ảnh cho đến khi ảnh gần xuất hiện trong viewport (khi người dùng cuộn tới). Nhờ đó trang tải nhanh hơn ban đầu, giảm băng thông và cải thiện hiệu năng (đặc biệt trên mobile).
Không nên dùng cho:
Ảnh above-the-fold (ảnh hero/banner đầu trang) vì có thể gây trễ hiển thị
Ảnh quan trọng ảnh hưởng LCP (Largest Contentful Paint)
Ảnh nhỏ nhưng cần hiển thị ngay (logo, icon quan trọng)

Các trình duyệt hỗ trợ codec khác nhau, nên đưa nhiều nguồn giúp tăng khả năng phát được trên mọi trình duyệt/thiết bị. Trình duyệt sẽ tự chọn định dạng nó hỗ trợ. Ngoài ra còn có thể tối ưu chất lượng/băng thông (fallback).
ví dụ:
<video controls>
  <source src="video.mp4" type="video/mp4">
  <source src="video.webm" type="video/webm">
  <source src="video.ogv" type="video/ogg">
</video>

alt cung cấp mô tả thay thế cho hình ảnh, giúp:
Screen reader đọc cho người khiếm thị (accessibility)
Hiển thị khi ảnh lỗi
Hỗ trợ SEO (hiểu nội dung ảnh)

Ảnh sản phẩm iPhone 16
→ alt="iPhone 16 màu Titan, mặt trước và sau"
Ảnh trang trí (decorative)
→ alt="" (để rỗng để screen reader bỏ qua)
Ảnh biểu đồ doanh thu Q1/2026
→ alt="Biểu đồ doanh thu quý 1 năm 2026 tăng từ tháng 1 đến tháng 3"

A5:
Cách 1: chỉ dùng alt trong <img>
Dùng khi:
Ảnh không cần chú thích hiển thị
Chỉ cần mô tả cho accessibility/SEO
Ảnh nhỏ, đơn giản (icon, avatar, thumbnail)
ví dụ:
<img src="iphone16.jpg" alt="iPhone 16 màu đen">
Người dùng nhìn ảnh là hiểu
Không cần thêm dòng mô tả dưới ảnh
Cách 2: dùng <figure> + <figcaption> (kèm alt)
Dùng khi:
Ảnh cần chú thích rõ ràng hiển thị cho người dùng
Nội dung ảnh cần giải thích thêm
Ảnh mang tính thông tin/quan trọng (sản phẩm, biểu đồ, minh họa)
<figure>
  <img src="iphone16.jpg" alt="iPhone 16 Pro Max 256GB Titan">
  <figcaption>iPhone 16 Pro Max — 25.990.000đ</figcaption>
</figure>

Phần C:
C1:
Lỗi 1: Dòng 2 — Input "Tên" không có <label for="...">, vi phạm accessibility
Sửa: <label for="name">Tên:</label> <input type="text" id="name" name="name" required>
Lỗi 2: Dòng 4 — Input email không có <label>, chỉ dùng placeholder (không thay thế label)
Sửa: <label for="email">Email:</label> <input type="email" id="email" name="email" required>
Lỗi 3: Dòng 6 — Password không có label và không có validation (minlength)
Sửa: <label for="password">Mật khẩu:</label> <input type="password" id="password" name="password" minlength="8" required>
Lỗi 4: Dòng 7 — Ô "Nhập lại mật khẩu" không có label và không xác nhận khớp password
Sửa: <label for="confirm">Nhập lại mật khẩu:</label> <input type="password" id="confirm" name="confirm" required>
Lỗi 5: Dòng 9 — Phone dùng type="text" thay vì type="tel"
Sửa: <label for="phone">Phone:</label> <input type="tel" id="phone" name="phone" pattern="[0-9]{10}" required>
Lỗi 6: Dòng 9 — Không nên dùng value mặc định cho số điện thoại (dữ liệu giả)
Sửa: bỏ value="0901234567"
Lỗi 7: Dòng 11 — <select> không có label và không có name
Sửa: <label for="city">Thành phố:</label>
      <select id="city" name="city" required>
          <option value="">Chọn thành phố</option>
          <option value="hn">Hà Nội</option>
          <option value="hcm">TP.HCM</option>
      </select>
Lỗi 8: Dòng 16 — Checkbox điều khoản thiếu input type="checkbox" và không liên kết label
Sửa: <input type="checkbox" id="terms" name="terms" required>
      <label for="terms">Tôi đồng ý điều khoản</label>

C2:
1. CCCD: <input type="text" pattern="^[0-9]{12}$" required>
  Số tài khoản <input type="text" pattern="^[0-9]{10,15}$" required>
2. Không đủ an toàn 
HTML5 validation:
Chỉ chạy ở trình duyệt (client-side)
Có thể bị bypass dễ dàng (tắt JS, sửa request, dùng tool như Postman)
Không kiểm soát được logic nghiệp vụ phức tạp
3. 3 loại validation HTML5 KHÔNG làm được
Kiểm tra dữ liệu với database
Ví dụ: Email đã tồn tại chưa

So sánh nhiều trường
Ví dụ: Password = Confirm password

Logic nghiệp vụ phức tạp
Ví dụ:
CMND có hợp lệ theo quy tắc nhà nước không
4. 
 Rủi ro 1: Bypass validation
Hacker có thể:
Gửi request trực tiếp (API, Postman)
Bỏ qua toàn bộ HTML validation
->Dữ liệu sai vẫn vào hệ thống
 Rủi ro 2: Injection (tấn công dữ liệu)
Ví dụ:
SQL Injection
XSS (chèn script)
-> Có thể:
Lấy cắp dữ liệu
Phá hệ thống
