# Simple Auth

Dự án này minh họa **2 cách xác thực cơ bản trong Node.js**:
1. **Basic Authentication** (dùng Authorization Header).
2. **Cookie Authentication** (lưu cookie trong MongoDB).

---

---

## 1. Cách chạy project

| Bước | Code |
|------|------|
| Cài thư viện cần thiết | ```bash<br>npm install<br>``` |
| Chạy server với Basic Auth | ```bash<br>node basic_auth.js<br>``` |
| Chạy server với Cookie Auth | ```bash<br>node cookie_auth.js<br>``` |

---

## 2. Test bằng Postman

### 2.1. Basic Authentication
| Mô tả | Code / Thiết lập |
|-------|------------------|
| Method | `GET` |
| URL | `http://localhost:3000` |
| Authorization | Basic Auth <br> Username: `admin` <br> Password: `12345` |

**Kết quả**: Nếu đúng sẽ trả về thông báo xác thực thành công. 
![Basic Auth Test](public/results/basic_auth.png)

---

### 2.2. Cookie Authentication
| Mô tả | Code / Thiết lập |
|-------|------------------|
| Chạy server | ```bash<br>node cookie_auth.js<br>``` |

#### a. Đăng nhập (Login)
| Mô tả | Code / Thiết lập |
|-------|------------------|
| Method | `POST` |
| URL | `http://localhost:3001/login` |
| Body (JSON) | ```json<br>{<br>  "username": "admin",<br>  "password": "12345"<br>}<br>``` |
#### b. Đăng xuất (Logout)
| Mô tả | Code / Thiết lập |
|-------|------------------|
| Method | `POST` |
| URL | `http://localhost:3001/logout` |
#### c. Kiểm tra cookie khi login và khi logout (profile)
| Mô tả | Code / Thiết lập |
|-------|------------------|
| Method | `GET` |
| URL | `http://localhost:3001/profile` |

**Kết quả login**: Server trả về `"Logged in!"`  
![Login](public/results/login.png)
**Kết quả profile khi còn login**: Server trả về `"Welcome user 1, your cookie is valid."`  
![profile_login](public/results/profile_login.png)
**Kết quả logout**: Server trả về `"Logged out."`  
![Logout](public/results/logout.png)
**Kết quả profile khi logout**: Server trả về `"Welcome user 1, your cookie is valid."`  
![profile_logout](public/results/profile_logout.png)
---

#### b. Xem cookie trong MongoDB
| Mô tả | Ví dụ dữ liệu trong DB |
|-------|-------------------------|
| Sau khi login, cookie sẽ được lưu trong collection `cookieApp.cookies` | ```json<br>{<br>  "-id": "ObjectID('68d7ad18c6763857897a1e09')",<br>  "cookie_token": "15c16bb9-1db4-4bd5-8033-5469fe377c7d",<br>  "userId": "1",<br>  "userRole": "adsys",<br>  "createdAt": "2025-09-27T09:23:36.962+00:00",<br>  "__v": "0"<br>}<br>``` |

**Ảnh show Cookie trong MongoDB**: 
![Show Cookie](public/results/show_cookie.png)

---

## 3. Cấu trúc thư mục
```plaintext
simple_auth/
 ├── basic_auth.js
 ├── cookie_auth.js
 ├── package-lock.json
 ├── package.json
 ├── public/
 │    └── results/
 │         ├── basic_auth.png
 │         ├── login.png
 │         ├── logout.png
 │         ├── profile_login.png
 │         ├── profile_logout.png
 |         └── show_cookie.png
 └── README.md
```
## Credit

This project was created by [Kevinkien25](https://github.com/Kevinkien25)