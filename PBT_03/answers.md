Phần A:
A1:
## 1. Inline CSS
 Cách viết
CSS được viết trực tiếp trong thuộc tính `style` của thẻ HTML.
<p style="color: red; font-size: 20px;">
    Xin chào
</p>
 Ưu điểm
- Nhanh, đơn giản
- Dễ thử giao diện ngay lập tức
- Không cần file riêng
 Nhược điểm
- Code khó bảo trì khi website lớn
- Lặp lại nhiều
- HTML bị rối
- Không tái sử dụng được
 Khi nên dùng
- Test nhanh
- Chỉnh riêng một phần tử nhỏ
- Debug tạm thời
 2. Internal CSS
 Cách viết
CSS được đặt trong thẻ `<style>` bên trong file HTML.
<!DOCTYPE html>
<html>
<head>
    <style>
        p {
            color: blue;
            font-size: 18px;
        }
    </style>
</head>
<body>
    <p>Hello World</p>
</body>
</html>
Ưu điểm
- Quản lý CSS tập trung hơn inline
- Không cần tạo file CSS riêng
- Phù hợp cho trang đơn
 Nhược điểm
- Không tái sử dụng cho nhiều trang
- File HTML dài hơn
- Website lớn sẽ khó quản lý
 Khi nên dùng
- Website nhỏ
- Trang đơn giản
- Bài tập thực hành
 3. External CSS
 Cách viết
CSS được viết trong file `.css` riêng rồi liên kết bằng thẻ `<link>`.
<!DOCTYPE html>
<html>
<head>
    <link rel="stylesheet" href="style.css">
</head>
<body>
    <p>Hello CSS</p>
</body>
</html>
 File `style.css`
```css
p {
    color: green;
    font-size: 22px;
}
 Ưu điểm
- Quản lý chuyên nghiệp
- Tái sử dụng cho nhiều trang
- Code gọn gàng
- Dễ bảo trì
- Tăng tốc tải trang nhờ cache
 Nhược điểm
- Phải tạo thêm file CSS
- Nếu link sai thì CSS không hoạt động
 Khi nên dùng
- Website thật
- Dự án lớn
- Nhiều trang web dùng chung giao diện

## Nếu cả 3 cách cùng áp dụng thì cách nào “thắng”?
Thứ tự ưu tiên:
Inline CSS > Internal CSS > External CSS
# Giải thích
CSS hoạt động theo cơ chế **độ ưu tiên (priority/specificity)**.
- Inline CSS có độ ưu tiên cao nhất vì nó gắn trực tiếp vào element.
- Internal CSS ưu tiên hơn External CSS nếu selector giống nhau.
- External CSS có ưu tiên thấp hơn.
Trình duyệt sẽ chọn rule có độ ưu tiên cao hơn để áp dụng cho element.


A2:

h1 → Chọn thẻ: <h1>ShopTLU</h1>
**Text content:** `ShopTLU`

`.price` → Chọn các thẻ có class `price`:
```html
<p class="price">25.990.000đ</p>
<p class="price">45.990.000đ</p>
```
**Text content:**
- `25.990.000đ`
- `45.990.000đ`

`#app header` → Chọn thẻ `<header>` nằm bên trong element có id `app`:
```html
<header class="top-bar dark">
``  
**Text content bên trong:**
- `ShopTLU`
- `Home`
- `Products`
- `About`
## 4. `nav a:first-child` → Chọn thẻ `<a>` đầu tiên bên trong `<nav>`:

```html
<a href="/" class="active">Home</a>

**Text content:** `Home`

## 5. `.product.featured h2` → Chọn thẻ `<h2>` nằm trong element có đồng thời class `product` và `featured`:

```html
<h2>MacBook Pro</h2>
```

**Text content:** `MacBook Pro`
## 6. `article > p` → Chọn tất cả thẻ `<p>` là con trực tiếp của `<article>`.

Các thẻ được chọn:

```html
<p class="price">25.990.000đ</p>
<p>Mô tả sản phẩm...</p>

<p class="price">45.990.000đ</p>
<p>Mô tả sản phẩm...</p>

**Text content:**
- `25.990.000đ`
- `Mô tả sản phẩm...`
- `45.990.000đ`
- `Mô tả sản phẩm...`
## 7. `a[href="/"]` → Chọn thẻ `<a>` có thuộc tính `href="/"`:

```html
<a href="/" class="active">Home</a>
```

**Text content:** `Home`
## 8. `.top-bar.dark h1` → Chọn thẻ `<h1>` nằm trong element có đồng thời class `top-bar` và `dark`.

```html
<h1>ShopTLU</h1>
```
**Text content:** `ShopTLU`


A3:
## Trường hợp 1: `content-box` (mặc định)

```css
.box-1 {
    width: 400px;
    padding: 20px;
    border: 5px solid black;
    margin: 10px;
}
```

### Phân tích

Trong `content-box`:

```text
width = chỉ tính phần content
```

Kích thước thực tế:

- Content = `400px`
- Padding trái + phải = `20px + 20px = 40px`
- Border trái + phải = `5px + 5px = 10px`

## Chiều rộng hiển thị
400 + 40 + 10 = 450px
→ **Chiều rộng hiển thị = 450px**
## Không gian chiếm trên trang
Cộng thêm margin:
450 + 10 + 10 = 470px

→ **Không gian chiếm trên trang = 470px**
# Trường hợp 2: `border-box`
.box-2 {
    box-sizing: border-box;
    width: 400px;
    padding: 20px;
    border: 5px solid black;
    margin: 10px;
}
## Phân tích
Trong `border-box`:
width = content + padding + border
Tổng width luôn là:
400px
## Chiều rộng hiển thị
→ **Chiều rộng hiển thị = 400px**
## Kích thước content thực tế
Trừ padding và border:
400 - 40 - 10 = 350px
→ **Kích thước content thực tế = 350px**
## Không gian chiếm trên trang
Cộng margin:
400 + 10 + 10 = 420px

→ **Không gian chiếm trên trang = 420px**
# Trường hợp 3: Margin Collapse
.box-a { margin-bottom: 25px; }
.box-b { margin-top: 40px; }
## Khoảng cách giữa box-a và box-b = 40px

## Giải thích tại sao KHÔNG PHẢI 65px

Margin dọc (`margin-top`, `margin-bottom`) giữa hai block liền kề sẽ xảy ra hiện tượng:
Margin Collapse
Browser KHÔNG cộng:25 + 40
mà chỉ lấy:margin lớn hơn = 40px

# Nâng cao

```css
.box-a { margin-bottom: -10px; }
.box-b { margin-top: 40px; }
## Khoảng cách thực tế
Khi có margin âm:40 + (-10) = 30px
→ **Khoảng cách = 30px**

A4:

Cho element:
```html
<p class="price" id="main-price">
```
và các CSS rules:

```css
p { color: black; }                    /* Rule A */
.price { color: blue; }               /* Rule B */
#main-price { color: red; }           /* Rule C */
p.price { color: green; }             /* Rule D */
```

---

# 1. Tính Specificity Score

Specificity được tính theo dạng:

```text
(a, b, c)
```

Trong đó:

- `a` = số lượng ID selector
- `b` = số lượng class, attribute, pseudo-class
- `c` = số lượng tag selector, pseudo-element

---

## Rule A

```css
p
```

- ID = 0
- Class = 0
- Tag = 1

→ Specificity:

```text
(0, 0, 1)
```

---

## Rule B

```css
.price
```

- ID = 0
- Class = 1
- Tag = 0

→ Specificity:

```text
(0, 1, 0)
```

---

## Rule C

```css
#main-price
```

- ID = 1
- Class = 0
- Tag = 0

→ Specificity:

```text
(1, 0, 0)
```

---

## Rule D

```css
p.price
```

- ID = 0
- Class = 1
- Tag = 1

→ Specificity:

```text
(0, 1, 1)
```

---

# 2. Element sẽ có màu gì?

So sánh specificity:
Rule mạnh nhất là:
```css
#main-price
```
vì có ID selector.
→ Element sẽ có màu:
```text
red
```
# Giải thích
CSS ưu tiên:

```text
ID > Class > Tag
```
Nên dù Rule D có cả `p` và `.price`, nó vẫn yếu hơn selector chứa ID.
# 3. Nếu thêm inline style
```html
<p class="price" id="main-price" style="color: orange;">
```
→ Element sẽ có màu:
```text
orange
```
# Giải thích
Inline CSS có độ ưu tiên cao hơn CSS thường.
Thứ tự ưu tiên:
```text
Inline style > ID > Class > Tag
```
# 4. Nếu Rule A thêm `!important`

```css
p { color: black !important; }
```
→ Element sẽ có màu:
```text
black
```
`!important` ưu tiên cao hơn specificity thông thường.

Nên:

```css
p { color: black !important; }
sẽ thắng:
#main-price { color: red; }
dù Rule C có specificity cao hơn.
# Thứ tự ưu tiên tổng quát
```text
!important > Inline style > ID selector > Class selector >  Tag selector
```


Phần C:
C1
# Phân tích Layout bị vỡ

```css
.container {
    width: 960px;
    margin: 0 auto;
}

.sidebar {
    width: 300px;
    padding: 20px;
    border: 1px solid #ccc;
    float: left;
}

.content {
    width: 660px;
    padding: 30px;
    border: 1px solid #ccc;
    float: left;
}
```
# 1. Tính chiều rộng thực tế
## Sidebar
Vì đang dùng:
content-box (mặc định)
nên width thực tế:
300
+ 20 + 20
+ 1 + 1
= 342px
→ Sidebar thực tế:
342px
## Content
Width thực tế:
660
+ 30 + 30
+ 1 + 1
= 722px
→ Content thực tế: 722px
## Tổng chiều rộng  342 + 722 = 1064px
Trong khi container chỉ:960px
# 2. Tại sao layout bị vỡ?
Hai phần tử đều:

```css
float: left;
```
Muốn nằm cạnh nhau thì tổng width phải nhỏ hơn hoặc bằng container.
Nhưng:
```text
1064px > 960px
```

nên browser không đủ chỗ đặt `.content` cùng dòng.

Kết quả:

```text
.content bị đẩy xuống dòng mới
```

---

# 3. Hai cách sửa

# Cách 1 — Dùng `border-box`

## CSS sửa

```css
.sidebar,
.content {
    box-sizing: border-box;
}
```

---

## Giải thích

Khi dùng:

```css
box-sizing: border-box;
```

thì:

```text
width = content + padding + border
```

Nghĩa là:

- Sidebar luôn đúng `300px`
- Content luôn đúng `660px`

Tổng:

```text
300 + 660 = 960px
```

Layout sẽ không vỡ.

---

# Cách 2 — Không dùng `border-box`

Phải tự giảm width content.

---

## Sidebar thực tế

```text
300 + 40 + 2 = 342px
```

---

## Container

```text
960px
```

---

## Width còn lại cho content

```text
960 - 342 = 618px
```

Nhưng content còn:

```text
padding: 30px + 30px = 60px
border: 1px + 1px = 2px
```

Nên width content phải là:

```text
618 - 60 - 2 = 556px
```

## CSS sửa

```css
.content {
    width: 556px;
    padding: 30px;
    border: 1px solid #ccc;
    float: left;
}
```

C2:
# Phân tích Cascade + Inheritance

## CSS

```css
body { font-size: 16px; color: #333; }

.container { font-size: 14px; }

.card { color: blue; }

.card .title { font-size: 20px; }

.card p { color: inherit; }

#featured .title { color: red; }

.highlight { color: green !important; }
```

---

# HTML

```html
<body>
    <div class="container">
        <div class="card" id="featured">
            <h2 class="title highlight">Sản phẩm A</h2>
            <p>Mô tả sản phẩm</p>
        </div>

        <div class="card">
            <h2 class="title">Sản phẩm B</h2>
            <p class="highlight">Mô tả sản phẩm B</p>
        </div>
    </div>
</body>
```

---

# 1. "Sản phẩm A" (h2)

```html
<h2 class="title highlight">Sản phẩm A</h2>
```

---

## Font-size = ?

### Rule áp dụng

```css
.container { font-size: 14px; }
```

`font-size` được inheritance xuống.

Nhưng có rule mạnh hơn:

```css
.card .title { font-size: 20px; }
```

Selector này target trực tiếp h2.

→ Font-size cuối cùng:

```text
20px
```

---

## Color = ?

### Các rule liên quan

```css
.card { color: blue; }
```

→ h2 inherit màu xanh.

---

```css
#featured .title { color: red; }
```

→ target trực tiếp h2.

Specificity:

```text
#featured .title
= (1,1,0)
```

---

```css
.highlight { color: green !important; }
```

Specificity:

```text
(0,1,0)
```

Nhưng có:

```text
!important
```

---

## Kết quả

`!important` thắng tất cả rule thường.

→ Color cuối cùng:

```text
green
```

# 2. "Mô tả sản phẩm" (p trong featured)

```html
<p>Mô tả sản phẩm</p>
```

---

## Rule liên quan

Card cha:

```css
.card { color: blue; }
```

→ div.card có màu blue.

---

Rule cho p:

```css
.card p { color: inherit; }
```

`inherit` nghĩa là:

```text
lấy màu từ parent
```

Parent là:

```html
<div class="card" id="featured">
```

đang có:

```text
color: blue
```

---

## Kết quả

```text
blue
```
# 3. "Sản phẩm B" (h2)

```html
<h2 class="title">Sản phẩm B</h2>
```

---

## Font-size

Rule:

```css
.card .title { font-size: 20px; }
```

→ áp dụng trực tiếp.

Kết quả:

```text
20px
```

---

## Color

Không có rule riêng cho h2 này.

Nó inherit từ:

```css
.card { color: blue; }
```

→ Color:

```text
blue
```

# 4. "Mô tả sản phẩm B"

```html
<p class="highlight">Mô tả sản phẩm B</p>
```

---

## Rule liên quan

```css
.card p { color: inherit; }
```

→ color từ parent = blue.

---

Nhưng:

```css
.highlight { color: green !important; }
```

target trực tiếp p.

Có:

```text
!important
```

nên thắng.
# Kết quả

```text
green
```
# Tổng kết

| Element | Font-size | Color |
|---|---|---|
| "Sản phẩm A" | `20px` | `green` |
| "Mô tả sản phẩm" | — | `blue` |
| "Sản phẩm B" | `20px` | `blue` |
| "Mô tả sản phẩm B" | — | `green` |

Phần B:
B1:
# Các loại selectors đã sử dụng trong file CSS

| Loại selector | Ví dụ trong CSS | Ý nghĩa |
|---|---|---|
| Element selector | `body`, `header`, `table`, `footer` | Chọn theo tên thẻ HTML |
| Class selector | `.active`, `.container` | Chọn theo class |
| ID selector | `#contact`, `#skills` | Chọn theo id |
| Descendant selector | `nav a`, `#contact p` | Chọn phần tử con bên trong phần tử khác |
| Pseudo-class selector | `a:hover`, `tr:nth-child(even)` | Chọn theo trạng thái / vị trí |
| Group selector | `table, th, td` | Chọn nhiều selector cùng lúc |

B2:
# Kết quả đo từ DevTools
## Hộp 1 — `content-box`
```css
width: 300px;
padding: 20px;
border: 5px solid;
box-sizing: content-box;
```
### Chiều rộng thực tế
```text
350px
```
### Cách tính
```text
300
+ 20 + 20
+ 5 + 5
= 350px
# Hộp 2 — `border-box`

```css
width: 300px;
padding: 20px;
border: 5px solid;
box-sizing: border-box;

### Chiều rộng thực tế
```text
300px
```
# Giải thích sự khác biệt
## `content-box`
Trong chế độ mặc định:

```text
width chỉ tính phần content
```

Padding và border được cộng thêm bên ngoài width.

Nên:

```text
300 + padding + border = 350px
## `border-box`

Trong `border-box`:

```text
width đã bao gồm:
- content
- padding
- border
Nên tổng width vẫn giữ nguyên:
```text
300px
Content bên trong sẽ tự co lại để nhường chỗ cho padding và border.

B3:
# 1. Liệt kê 10 rules + specificity score

/* Rule 1 */
p {
    color: black;
}
/* Specificity: (0,0,1) */

/* Rule 2 */
body p {
    color: gray;
}
/* Specificity: (0,0,2) */

/* Rule 3 */
.text {
    color: blue;
}
/* Specificity: (0,1,0) */

/* Rule 4 */
.highlight {
    color: green;
}
/* Specificity: (0,1,0) */

/* Rule 5 */
p.text {
    color: orange;
}
/* Specificity: (0,1,1) */

/* Rule 6 */
.text.highlight {
    color: purple;
}
/* Specificity: (0,2,0) */

/* Rule 7 */
body .text.highlight {
    color: brown;
}
/* Specificity: (0,2,1) */

/* Rule 8 */
#demo {
    color: red;
}
/* Specificity: (1,0,0) */

/* Rule 9 */
p#demo {
    color: pink;
}
/* Specificity: (1,0,1) */

/* Rule 10 */
#demo.text.highlight {
    color: gold;
}
/* Specificity: (1,2,0) */
```
# 2. Element cuối cùng hiển thị màu gì?
HTML:

```html
<p id="demo" class="text highlight">
    Hello World
</p>
## Kết quả cuối cùng
```text
gold
```
Rule mạnh nhất là:

```css
#demo.text.highlight {
    color: gold;
}
```
Specificity:
```text
(1,2,0)
```
CSS ưu tiên:
```text
ID > Class > Element
```
nên rule có:

- 1 ID
- 2 class

sẽ thắng tất cả các rule còn lại.
# 3. Nếu thay đổi thứ tự rules trong file CSS thì sao?

Kết quả KHÔNG đổi

Element vẫn màu: gold
# Giải thích

Vì:
```css
#demo.text.highlight
```
có specificity cao nhất.
CSS luôn ưu tiên:
```text
specificity cao hơn
```

trước khi xét:

```text
thứ tự xuất hiện
```
Thứ tự chỉ ảnh hưởng khi:
```text
2 rules có specificity bằng nhau
```

Ví dụ:

```css
.text {
    color: blue;
}

.highlight {
    color: green;
}
```

Cả hai đều:

```text
(0,1,0)
```

Nếu element có cả 2 class:

```html
<p class="text highlight">
```

thì:

```text
rule viết SAU sẽ thắng




