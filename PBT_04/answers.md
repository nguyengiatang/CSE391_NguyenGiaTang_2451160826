Phần A:
A1:
# CSS `position`

| Position     | Vẫn chiếm chỗ trong flow? | Tham chiếu vị trí | Cuộn theo trang? | Use case |
|--------------|---------------------------|-------------------|------------------|----------|
| `static`     | Có | Theo flow mặc định của document | Có | Layout bình thường |
| `relative`   | Có | So với vị trí gốc của chính nó | Có | Dịch nhẹ phần tử nhưng vẫn giữ chỗ |
| `absolute`   | Không | So với tổ tiên gần nhất có `position != static` | Có | Overlay, badge, icon, menu |
| `fixed`      | Không | So với viewport (màn hình trình duyệt) | Không | Navbar cố định, nút chat |
| `sticky`     | Có | Ban đầu theo flow, sau đó bám theo viewport | Một phần | Header dính khi cuộn |

---

# Giải thích thêm

## 1. `absolute` khi nào tham chiếu `body`?

`absolute` sẽ tham chiếu:

- Parent gần nhất có `position` khác `static`
  (`relative`, `absolute`, `fixed`, `sticky`)
- Nếu không có ancestor nào positioned
  → nó sẽ tham chiếu tới `body`

Ví dụ:

```html
<div class="parent">
    <div class="child"></div>
</div>
```

```css
.parent {
    position: relative;
}

.child {
    position: absolute;
    top: 0;
    right: 0;
}
```

→ `.child` sẽ nằm góc phải của `.parent`.

---

Nếu bỏ:

```css
.parent {
    position: relative;
}
```

thì `.child` sẽ tìm ancestor khác.

Nếu không tìm thấy ancestor positioned nào  
→ nó bám theo `body`.

---

# 2. "Nearest positioned ancestor" là gì?

Là:

> Phần tử cha gần nhất có `position`
> KHÁC `static`.

Ví dụ:

```html
<body>
    <div class="box1">
        <div class="box2">
            <div class="box3"></div>
        </div>
    </div>
</body>
```

```css
.box1 {
    position: static;
}

.box2 {
    position: relative;
}

.box3 {
    position: absolute;
    top: 0;
    left: 0;
}
```

`box3` sẽ tham chiếu tới `box2`
vì:

- `box1` = static → bỏ qua
- `box2` = relative → dùng luôn

`box2` chính là:

```text
nearest positioned ancestor
```


A2:

# Trường hợp 1

```css
.container {
    display: flex;
}

.item {
    flex: 1;
}
```

- Có 4 items
- `display: flex` → các item nằm trên 1 hàng
- `flex: 1` → chia đều chiều rộng

## Bố cục

```text
+---------+---------+---------+---------+
| Item 1  | Item 2  | Item 3  | Item 4  |
+---------+---------+---------+---------+
```

→ 1 hàng, 4 cột bằng nhau

---

# Trường hợp 2

```css
.container {
    display: flex;
    flex-wrap: wrap;
}

.item {
    width: 45%;
    margin: 2.5%;
}
```

- `width: 45%`
- `margin: 2.5%`

Tổng mỗi item:

```text
45% + 2.5% + 2.5% = 50%
```

→ mỗi hàng chứa được 2 item

Có 6 items:

```text
6 / 2 = 3 hàng
```

## Bố cục

```text
+-----------+-----------+
|  Item 1   |  Item 2   |
+-----------+-----------+

+-----------+-----------+
|  Item 3   |  Item 4   |
+-----------+-----------+

+-----------+-----------+
|  Item 5   |  Item 6   |
+-----------+-----------+
```

→ 3 hàng, 2 cột

---

# Trường hợp 3

```css
.container {
    display: flex;
    justify-content: space-between;
    align-items: center;
}
```

- `justify-content: space-between`
  → item đầu sát trái
  → item cuối sát phải
  → item giữa nằm giữa khoảng trống

- `align-items: center`
  → căn giữa theo chiều dọc

## Bố cục

```text
+--------------------------------------------------+
| Item 1              Item 2              Item 3   |
|                                                  |
|         (căn giữa theo chiều dọc)                |
+--------------------------------------------------+
```

→ 1 hàng ngang
→ khoảng cách đều giữa các item

---

# Trường hợp 4

```css
.container {
    display: grid;
    grid-template-columns: 200px 1fr 200px;
    gap: 20px;
}
```

## Ý nghĩa

```text
200px   1fr   200px
```

- Cột 1 = 200px cố định
- Cột 2 = chiếm toàn bộ phần còn lại
- Cột 3 = 200px cố định

Có 3 items:

## Bố cục

```text
+----------+----------------------+----------+
| Item 1   |       Item 2         | Item 3   |
| 200px    |   flexible width     | 200px    |
+----------+----------------------+----------+
```

→ 1 hàng, 3 cột

---

# Trường hợp 5

```css
.container {
    display: grid;
    grid-template-columns: repeat(3, 1fr);
    gap: 10px;
}
```

## Ý nghĩa

```css
repeat(3, 1fr)
```

=

```css
1fr 1fr 1fr
```

→ grid có 3 cột bằng nhau

Có 7 items:

- Hàng 1 → 3 items
- Hàng 2 → 3 items
- Hàng 3 → còn 1 item

## Bố cục

```text
+---------+---------+---------+
| Item 1  | Item 2  | Item 3  |
+---------+---------+---------+

+---------+---------+---------+
| Item 4  | Item 5  | Item 6  |
+---------+---------+---------+

+---------+
| Item 7  |
+---------+
```

## Vị trí item cuối

`Item 7` nằm:

```text
Hàng 3 - Cột 1
```

vì grid tự đổ item từ trái sang phải, trên xuống dưới.

---

# Tóm tắt nhanh

| Trường hợp | Layout |
|---|---|
| 1 | 1 hàng, 4 cột đều nhau |
| 2 | 3 hàng, 2 cột |
| 3 | 1 hàng ngang, space-between |
| 4 | Grid 3 cột: `200px - flexible - 200px` |
| 5 | Grid 3 cột, 3 hàng, item cuối ở hàng 3 cột 1 |

Phần C:
C1:
| Tình huống | Dùng gì? | Giải thích |
|---|---|---|
| 1. Navigation bar ngang | Flexbox | Navbar là layout 1 chiều (ngang). Flexbox rất mạnh cho căn hàng ngang, spacing và align center. |
| 2. Lưới ảnh Instagram | Grid | Đây là layout 2 chiều (hàng + cột). Grid giúp tạo các cột đều nhau dễ dàng. |
| 3. Layout blog: main + sidebar | Grid | Có cấu trúc cột rõ ràng (`main` + `sidebar`). Grid phù hợp chia layout tổng thể. |
| 4. Footer 4 cột | Grid hoặc Flexbox | Nếu chỉ cần 4 cột đơn giản → Flexbox đủ dùng. Nếu cần kiểm soát cột đều và responsive tốt hơn → Grid tốt hơn. |
| 5. Card sản phẩm | Kết hợp cả hai | Grid/Flex cho layout ngoài; bên trong card thường dùng Flexbox cột để đẩy nút xuống đáy bằng `margin-top: auto`. |


