# Công cụ Kiểm tra Cookie Netflix

Một tiện ích **Python** đa luồng, gọn nhẹ giúp kiểm tra nhanh tình trạng các cookie Netflix.

* 🌐 Tái sử dụng tối đa **5** cửa sổ Chrome/Chromium chạy song song (nhanh hơn việc mở/đóng liên tục).
* 🖍️ Giao diện console có màu: chỉ hiển thị `LIVE` / `DIE` kèm 20 ký tự đầu của mỗi dòng cookie.
* 🗂️ Ghi đầy đủ cookie vào `live_accounts.txt` hoặc `die_accounts.txt`.
* ⚠️ Đã cài đặt xử lý thoát an toàn, nhưng đôi khi một vài cửa sổ Chrome vẫn còn – bạn hãy đóng thủ công nếu gặp.

---

## 1. Yêu cầu hệ thống

* Windows 10/11 64-bit (các hệ khác có thể chạy nhưng chưa thử nghiệm).
* Python **3.8+** 64-bit – tải tại https://www.python.org/  
  → Trong trình cài, **đánh dấu** mục *"Add Python to PATH"* hoặc dùng `py` để gọi Python.
* Trình duyệt **Google Chrome** (≥ v109). Selenium sẽ tự tải chromedriver phù hợp.
* Các thư viện Python:

```bash
pip install -r requirements.txt
```
`requirements.txt` tối thiểu:
```
selenium>=4.18
colorama>=0.4
```

---

## 2. Chuẩn bị dữ liệu

1. Tạo (hoặc ghi đè) file **`netflix_accounts.txt`** trong cùng thư mục.
2. Mỗi dòng là **một cookie**, bắt buộc phải có cặp `NetflixId=`. Ví dụ:

```
NetflixId=ABC123...xyz | ghi chú tuỳ ý
NetflixId=DEF456...uvw | comment
```
Nếu cùng dòng có thêm `SecureNetflixId=...` vẫn được; script sẽ tự bỏ qua.

---

## 3. Chạy công cụ

```powershell
python netflix_login_checker_min.py
```
(hoặc dùng `py` nếu Python chưa vào PATH).

Kết quả console mẫu:
```
Code by: Phan Đình Thuyết | Facebook: https://www.facebook.com/phandinhthuyet/

LIVE | NetflixId=ABC1...
DIE  | NetflixId=DEF4...
...
```
Sau khi chạy xong, bạn có:
* `live_accounts.txt` – các cookie còn hoạt động.
* `die_accounts.txt`   – các cookie hết hạn/không dùng được.

---

## 4. Đóng gói thành file thực thi `.exe` (tuỳ chọn)

```powershell
py -m PyInstaller --onefile --icon=icon.ico netflix_login_checker_min.py
```
File xuất ra nằm tại `dist\netflix_login_checker_min.exe`, đã tích hợp sẵn Python.

---

## 5. Lưu ý về việc đóng trình duyệt

Nhấn **Ctrl + C** để dừng. Chương trình sẽ cố gắng đóng tất cả cửa sổ Chrome. Nếu còn sót, bạn chỉ cần tắt chúng thủ công.

---

## 6. Tác giả

Được phát triển bởi **[Phan Đình Thuyết](https://www.facebook.com/phandinhthuyet/)**. ❤️ 
