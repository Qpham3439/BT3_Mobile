# BT3_Mobile
Bài tập 03 của sinh viên: K225480106057 - Phạm Mạnh Quỳnh - môn Phát triển ứng dụng trên thiết bị di động

# BÀI TẬP 3 – XÂY DỰNG ỨNG DỤNG ĐA MÀN HÌNH, GIẢI TOÁN VÀ TÍCH HỢP WEBVIEW BẰNG ANDROID STUDIO

---

# Giới thiệu

Ứng dụng được xây dựng trên Android Studio bằng ngôn ngữ Java.

Ứng dụng mô phỏng lại chức năng tương đương phiên bản đã thực hiện trên MIT App Inventor nhưng triển khai bằng Native Android.

Ứng dụng gồm 3 màn hình (Activity):

- Activity 1: Giới thiệu bản thân và điều hướng.
- Activity 2: Giải bài toán đơn giản và gửi dữ liệu lên API Server.
- Activity 3: Nhúng trình duyệt WebView để truy cập website theo mã số sinh viên.

---

# Cấu trúc Project

```plaintext
app
├── java
│   └── com.example.app2
│       ├── MainActivity.java
│       ├── GiaiToanActivity.java
│       └── WebViewActivity.java
│
├── res
│   ├── layout
│   │   ├── activity_main.xml
│   │   ├── activity_giai_toan.xml
│   │   └── activity_web_view.xml
│   │
│   ├── values
│   │   ├── strings.xml
│   │   └── colors.xml
│
└── AndroidManifest.xml
```

# AndroidManifest.xml

## Chức năng

Tệp cấu hình trung tâm của ứng dụng Android.

Thực hiện:

- Khai báo các Activity.
- Cấu hình ứng dụng.
- Khai báo quyền truy cập Internet.
- Cho phép ứng dụng gọi API và tải Web.

**Ảnh AndroidManifest.xml**

<img width="1919" height="1079" alt="Screenshot 2026-06-12 092527" src="https://github.com/user-attachments/assets/fecaee71-efa6-4154-8917-551e872ab084" />

---

# MainActivity (Activity 1 – About)

## Chức năng

Màn hình khởi động của ứng dụng.

Bao gồm:

- Hiển thị thông tin sinh viên.
- Giới thiệu bài tập.
- Điều hướng sang Activity giải toán.
- Điều hướng sang Activity WebView.

Kỹ thuật sử dụng:

- Intent
- Button
- Event Click

**Ảnh file MainActivity.java**
<img width="1864" height="1060" alt="Screenshot 2026-06-12 092537" src="https://github.com/user-attachments/assets/1a03b7d9-670c-42c8-a888-c122db9189bb" />

---

# activity_main.xml

## Chức năng

Thiết kế giao diện màn hình About.

Sử dụng:

- LinearLayout
- TextView
- Button

Bố cục:

```text
Thông tin sinh viên
↓

Nút mở Activity 2

↓

Nút mở Activity 3
```

**Ảnh activity_main.xml**
<img width="1910" height="1071" alt="Screenshot 2026-06-12 092559" src="https://github.com/user-attachments/assets/c6448b84-64d9-4711-8144-7baffbb70ef4" />

---

# GiaiToanActivity (Activity 2 – Giải toán + API)

## Chức năng

Cho phép người dùng nhập dữ liệu đầu vào để giải bài toán.

Bài toán lựa chọn:

### Giải phương trình bậc nhất

```text
ax + b = 0
```

Sau khi tính toán:

- Tạo JSON.
- Gửi dữ liệu lên API.

API:

```text
https://k58kmt.tdh.io.vn/api
```

Dữ liệu gửi:

```json
{
"app_by":"MSSV",

"input":{
"a":1,
"b":2,
"c":3,
"name":"hello tac ke"
},

"output":{
"ketluan":"vo nghiem",
"abc":"xyz",
"nghiem":3.14
}
}
```

Nhận:

```json
{
"ok":1,
"stt":1234
}
```

Kỹ thuật sử dụng:

- JSONObject
- OkHttp
- POST Request
- Thread bất đồng bộ

**Ảnh GiaiToanActivity.java**
<img width="1917" height="1075" alt="Screenshot 2026-06-12 092533" src="https://github.com/user-attachments/assets/ff5b09ab-ec02-473b-b672-ed080a7db3ed" />

---

# activity_giai_toan.xml

## Chức năng

Thiết kế giao diện nhập dữ liệu.

Bao gồm:

- EditText nhập hệ số.
- Button tính toán.
- TextView hiển thị kết quả.
- ScrollView.

**Ảnh activity_giai_toan.xml**
<img width="1896" height="1079" alt="Screenshot 2026-06-12 092556" src="https://github.com/user-attachments/assets/a3bb9b41-baa7-46ea-8f71-b3c59a705f18" />

---


# WebViewActivity (Activity 3)

## Chức năng

Nhúng trình duyệt WebView.

Tự động mở:

```text
https://k58kmt.tdh.io.vn?masv=MSSV
```

Ví dụ:

```text
https://k58kmt.tdh.io.vn?masv=K225480106057
```

Kỹ thuật:

- WebView
- WebSettings
- JavaScript

Ví dụ:

```java
webView.loadUrl(url);
```

**Ảnh WebViewActivity.java**
<img width="1916" height="1077" alt="Screenshot 2026-06-12 092542" src="https://github.com/user-attachments/assets/dc0a69b8-cbb8-4357-8334-75e12d6a0dce" />

---

# 10. activity_web_view.xml

## Chức năng

Thiết kế màn hình trình duyệt.

Sử dụng:

```xml
<WebView/>
```

Thuộc tính:

```xml
layout_width="match_parent"
layout_height="match_parent"
```

**Ảnh activity_web_view.xml**
<img width="1919" height="1079" alt="Screenshot 2026-06-12 092603" src="https://github.com/user-attachments/assets/d18348b9-3559-41ec-8aa1-a63d7c3d49b4" />

---

# 11. strings.xml + colors.xml

## Chức năng

Quản lý tài nguyên tập trung.

Bao gồm:

- Chuỗi giao diện.
- Màu sắc.

Ưu điểm:

- Không hardcode.
- Dễ bảo trì.
- Hỗ trợ đa ngôn ngữ.

**Ảnh strings.xml**
<img width="1919" height="1079" alt="Screenshot 2026-06-12 110953" src="https://github.com/user-attachments/assets/46fe476a-6d17-4855-bf42-2cceb73de39d" />

**Ảnh colors.xml**
<img width="1919" height="1073" alt="Screenshot 2026-06-12 092607" src="https://github.com/user-attachments/assets/a769f35f-da95-4210-94fd-ee5debcdd360" />

---

# 12. Kết quả chạy chương trình

### Màn hình About
<img width="720" height="1600" alt="z7927667772112_87198814fed8d2988f4d188468307c5c" src="https://github.com/user-attachments/assets/bc025f5b-f236-466a-b239-49882250bad4" />

---

### Màn hình giải toán + API
<img width="720" height="1600" alt="z7927667835289_3a962819a094ceb3c4336f4aa8286199" src="https://github.com/user-attachments/assets/741a8c06-3fa8-4b4a-af2a-2f71a47d5e52" />

---

### Màn hình WebView
<img width="720" height="1600" alt="z7927667807163_59ba5167cc6dca8e7d808cb31c897c29" src="https://github.com/user-attachments/assets/ef583a91-78d6-479a-b2ca-44c759e68618" />

---

# 13. Kết luận

Ứng dụng hoàn thành các chức năng:

✔ Thiết kế ứng dụng Native Android bằng Java

✔ Xây dựng mô hình đa Activity

✔ Giải bài toán và xử lý dữ liệu

✔ Gọi API bằng HTTP POST

✔ Nhận và xử lý JSON phản hồi

✔ Nhúng WebView tải website động theo mã sinh viên
