# Thí Nghiệm So Sánh Phần Tử Block và Inline trong HTML/CSS

## 1. Mục tiêu bài thực hành
- Quan sát và mô tả một cách trực quan hành vi của các phần tử `display: block` (`<div>`).
- Quan sát và mô tả một cách trực quan hành vi của các phần tử `display: inline` (`<span>`).
- Hiểu rõ lý do tại sao các thuộc tính CSS như `width`, `height`, `margin-top`, `margin-bottom` hoạt động trên thẻ block (`<div>`) nhưng lại bị bỏ qua trên thẻ inline (`<span>`).

---

## 2. Các bước thực hiện
1. **Chuẩn bị file:**
   - Tạo file `display-test.html` (và `index.html`).
   - Tạo file `style.css` và liên kết trong thẻ `<head>`.
2. **Cấu trúc HTML:**
   - Khu vực 1: 2 phần tử `<div>` với class `box block-box`.
   - Khu vực 2: 2 phần tử `<span>` nằm trong đoạn `<p>` với class `box inline-box`.
3. **Quy tắc CSS:**
   - Class chung `.box`: `width: 250px; height: 100px; padding: 20px; margin: 20px; border: 3px solid #333;`.
   - Class `.block-box`: `background-color: lightskyblue;`.
   - Class `.inline-box`: `background-color: lightsalmon;`.

---

## 3. Phân tích kết quả thí nghiệm

### A. Đối với phần tử Block (`<div>` - màu xanh da trời)
- **Câu hỏi 1: Chúng có xếp chồng lên nhau theo chiều dọc không, mỗi cái chiếm một hàng riêng?**
  - **Trả lời: CÓ.** Phần tử block luôn bắt đầu trên một dòng mới và chiếm trọn 100% chiều ngang của khối chứa nếu không giới hạn chiều rộng. Khi có 2 thẻ `<div>`, thẻ thứ hai tự động rớt xuống dòng tiếp theo.
- **Câu hỏi 2: Chúng có tuân thủ `width: 250px` và `height: 100px` không?**
  - **Trả lời: CÓ.** Cả 2 hộp `<div>` đều nhận đúng kích thước `250px` chiều rộng và `100px` chiều cao đã đặt.
- **Câu hỏi 3: Chúng có khoảng trống `margin: 20px` ở cả bốn phía, đẩy chúng ra xa nhau và ra xa các nội dung khác không?**
  - **Trả lời: CÓ.** Cả bốn hướng (top, right, bottom, left) đều sinh ra khoảng cách cách biệt `20px` đẩy các phần tử khác ra xa một cách chính xác.

> **Kết luận Block:** Phần tử block tuân thủ đầy đủ mọi quy tắc kích thước (`width`, `height`) và mô hình hộp (Box Model - margin, padding 4 hướng).

---

### B. Đối với phần tử Inline (`<span>` - màu cam)
- **Câu hỏi 1: Chúng có nằm trên cùng một dòng với văn bản không?**
  - **Trả lời: CÓ.** Các phần tử inline nằm liền kề nhau và tiếp tục dòng chảy tự nhiên của văn bản xung quanh.
- **Câu hỏi 2: Chúng có tuân thủ `width: 250px` và `height: 100px` không?**
  - **Trả lời: KHÔNG.** Phần tử inline hoàn toàn bỏ qua thuộc tính `width` và `height`. Kích thước của chúng co lại vừa khít với nội dung chữ bên trong ("Inline 1", "Inline 2").
- **Câu hỏi 3: Chúng có `margin` và `padding` ở bên trái/phải không? Margin và padding ở trên/dưới thì sao?**
  - **Trả lời:**
    - `margin-left`, `margin-right`, `padding-left`, `padding-right`: **CÓ TÁC DỤNG**, tạo khoảng cách đẩy văn bản sang hai bên trái phải.
    - `margin-top`, `margin-bottom`: **HOÀN TOÀN BỊ BỎ QUA**, không đẩy dòng chữ phía trên hoặc phía dưới ra xa.
    - `padding-top`, `padding-bottom`: Vẫn tô màu nền đè lên dòng trên/dưới nhưng không chiếm chỗ trong luồng tài liệu (không đẩy dòng văn bản lân cận ra xa).

> **Kết luận Inline:** Phần tử inline không tuân thủ `width`, `height`, `margin-top`, `margin-bottom`. Chúng được thiết kế để nằm mượt mà trong dòng chảy văn bản.

---

## 4. Bảng tóm tắt so sánh Block vs Inline

| Tiêu chí | Phần tử Block (`<div>`, `<p>`, `<h1>`...) | Phần tử Inline (`<span>`, `<a>`, `<strong>`...) |
| :--- | :--- | :--- |
| **Dòng hiển thị** | Bắt đầu trên một dòng mới | Nằm trên cùng một dòng với văn bản |
| **Chiều rộng mặc định** | Chiếm 100% chiều rộng thẻ cha | Co giãn vừa vặn theo nội dung bên trong |
| **Thuộc tính width & height** | Hoạt động bình thường | Bị bỏ qua, không có tác dụng |
| **Margin trên / dưới** | Hoạt động bình thường (đẩy phần tử khác) | Bị bỏ qua, không có tác dụng |
| **Margin trái / phải** | Hoạt động bình thường | Hoạt động bình thường |
| **Padding 4 phía** | Hoạt động bình thường và chiếm diện tích | Nhận padding nhưng top/bottom không đẩy dòng xung quanh |
