# 🔹 HTTP Status Codes — Important & Note-worthy

## 📌 Status Code কী?

Status code হলো server থেকে client-এর কাছে পাঠানো একটা **number message**, যেটা বলে:

* request সফল হয়েছে নাকি না
* হলে কীভাবে হয়েছে
* না হলে কেন হয়নি

---

## 🔹 1xx — Informational (কম ব্যবহার হয়)

👉 শুধু জানায় request পাওয়া গেছে, process হচ্ছে
📌 সাধারণত আমরা ব্যবহার করি না

---

## 🔹 2xx — Success Codes (সব ঠিক আছে)

### ✅ **200 OK**

📌 সবচেয়ে common
👉 Request সফল, data পাওয়া গেছে

উদাহরণ:

```
GET /users/1
```

মানে: user data ঠিকঠাক এসেছে

📝 Note:

* GET request এ সবচেয়ে বেশি ব্যবহার হয়

---

### ✅ **201 Created**

📌 নতুন resource তৈরি হয়েছে

উদাহরণ:

```
POST /users
```

মানে: নতুন user successfully create হয়েছে

📝 Note:

* POST request এর জন্য আদর্শ

---

### ✅ **204 No Content**

📌 Request সফল, কিন্তু ফেরত দেওয়ার মতো কিছু নেই

উদাহরণ:

```
DELETE /users/5
```

📝 Note:

* delete বা update এর পরে ব্যবহার হয়
* response body থাকে না

---

## 🔹 3xx — Redirection (কমন না, কিন্তু জানা দরকার)

### 🔁 **301 Moved Permanently**

👉 URL permanently change হয়েছে

### 🔁 **302 Found**

👉 URL temporarily change হয়েছে

📝 Note:

* SEO বা auth flow এ দেখা যায়

---

## 🔹 4xx — Client Error (ভুল client side এ)

### ❌ **400 Bad Request**

👉 client ভুল data পাঠিয়েছে

উদাহরণ:

* ভুল JSON
* required field missing

📝 Note:

* validation error এ বেশি দেখা যায়

---

### ❌ **401 Unauthorized**

👉 login করা নেই / token নাই

📝 Note:

* authentication related

---

### ❌ **403 Forbidden**

👉 login করা আছে, কিন্তু permission নাই

📝 Note (Interview favorite 😄):

* 401 = identity নাই
* 403 = identity আছে, permission নাই

---

### ❌ **404 Not Found**

👉 resource পাওয়া যায়নি

উদাহরণ:

```
GET /users/999
```

user নাই

📝 Note:

* ভুল id বা URL হলে

---

### ❌ **422 Unprocessable Entity** (FastAPI খুব পছন্দ করে)

👉 data format ঠিক, কিন্তু validation fail

উদাহরণ:

* age = -5
* email format ভুল

📝 Note:

* FastAPI default validation error

---

## 🔹 5xx — Server Error (ভুল server side এ)

### 🔥 **500 Internal Server Error**

👉 server ভেঙে গেছে 😅

কারণ:

* code bug
* database error

📝 Note:

* client দোষী না

---

### 🔥 **503 Service Unavailable**

👉 server temporarily unavailable

উদাহরণ:

* maintenance
* overload

---

## 🔹 Super Important Interview Table 🧠

| Code | Meaning          | কে দোষী  |
| ---- | ---------------- | -------- |
| 200  | Success          | ❌ কেউ না |
| 201  | Created          | ❌ কেউ না |
| 400  | Bad Request      | ✅ Client |
| 401  | Unauthorized     | ✅ Client |
| 403  | Forbidden        | ✅ Client |
| 404  | Not Found        | ✅ Client |
| 422  | Validation Error | ✅ Client |
| 500  | Server Error     | ❌ Client |
| 503  | Server Down      | ❌ Client |

---

## 🔹 FastAPI Example (Real Feel)

```python
from fastapi import HTTPException

@app.get("/users/{user_id}")
def get_user(user_id: int):
    if user_id == 0:
        raise HTTPException(status_code=400, detail="Invalid user id")

    if user_id == 99:
        raise HTTPException(status_code=404, detail="User not found")

    return {"user_id": user_id}
```

---

## 🧠 Final Memory Trick

* **2xx** → সব ঠিক
* **4xx** → client ভুল
* **5xx** → server ভুল

---

