# **Path Parameter কী?**

Path parameter হলো URL-এর ভেতরের একটা dynamic অংশ, যেটা দিয়ে আমরা server-কে বলি ঠিক *কোন resource* নিয়ে কাজ করতে চাই।

সহজভাবে বললে
URL-এর রাস্তার (path) মাঝখানে যে variable থাকে, সেটাই path parameter।

উদাহরণ:

```
/users/5
```

এখানে `5` হলো path parameter
মানে → user যার id = 5

---

### Path Parameter কেন দরকার?

কারণ সব data একরকম না।
আমরা চাই একটাই endpoint দিয়ে ভিন্ন ভিন্ন data access করতে।

একটা endpoint

```
/users/{id}
```

এই endpoint দিয়েই:

* `/users/1`
* `/users/2`
* `/users/10`

সব user-এর data আনা যায়।

---

## FastAPI-তে Path Parameter কিভাবে কাজ করে?

উদাহরণ:

```python
from fastapi import FastAPI

app = FastAPI()

@app.get("/items/{item_id}")
def get_item(item_id: int):
    return {"item_id": item_id}
```

এখন যদি তুমি hit করো:

```
/items/10
```

Output হবে:

```json
{
  "item_id": 10
}
```

FastAPI নিজে থেকেই:

* URL থেকে `item_id` ধরবে
* টাইপ check করবে (এখানে `int`)
* ভুল হলে error দেবে

---

## Path Parameter দিয়ে আমরা কী কী করতে পারি?

### 1️⃣ Specific data fetch করা

```
GET /users/3
```

👉 id = 3 user আনা

---

### 2️⃣ Database থেকে record update করা

```
PUT /products/7
```

👉 product id 7 update করা

---

### 3️⃣ Record delete করা

```
DELETE /orders/15
```

👉 order id 15 delete করা

---

### 4️⃣ Nested resource access করা

```
/users/5/orders/2
```

👉 user 5 এর order 2

FastAPI code:

```python
@app.get("/users/{user_id}/orders/{order_id}")
def get_order(user_id: int, order_id: int):
    return {
        "user_id": user_id,
        "order_id": order_id
    }
```

---

### 5️⃣ Validation + Security

FastAPI automatically:

* type validation করে
* required parameter enforce করে
* Swagger UI-তে দেখায়

---

## Path Parameter vs Query Parameter (সংক্ষেপে)

| Path Parameter        | Query Parameter     |
| --------------------- | ------------------- |
| Resource identify করে | Filter / option দেয় |
| Required              | Optional হতে পারে   |
| `/users/5`            | `/users?age=20`     |

---

## কখন Path Parameter ব্যবহার করবা?

✔ যখন **একটা নির্দিষ্ট resource** বোঝাতে চাও
✔ যখন URL দেখেই clear হওয়া দরকার
✔ REST API design follow করতে চাইলে

---

