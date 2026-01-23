# 📘 FastAPI + Virtual Environment + Project Run

### (Manjaro / Linux – Beginner Friendly Bangla Note)

---

## 1️⃣ FastAPI কী?

FastAPI হলো একটি **Python backend framework**
এটা দিয়ে আমরা:

* API বানাই
* Flutter / Web / Mobile app এর backend করি
* Database এর সাথে কাজ করি

FastAPI খুব fast, simple আর industry friendly।

---

## 2️⃣ Virtual Environment (venv) কেন দরকার?

Virtual environment হলো **project-specific Python environment**।

এতে সুবিধা:

* এক project এর package অন্য project এ impact করে না
* version conflict হয় না
* production এ সমস্যা কম হয়

👉 **FastAPI project এ venv ব্যবহার করা best practice**

---

## 3️⃣ Python installed আছে কিনা check

Terminal খুলে লেখো:

```bash
python --version
```

অথবা

```bash
python3 --version
```

Version দেখালে ok।

---

## 4️⃣ Project folder তৈরি করো

Home directory তে রাখাই ভালো:

```bash
mkdir -p ~/projects/fastapi_app
cd ~/projects/fastapi_app
```

---

## 5️⃣ Virtual environment তৈরি করা

Project folder এর ভিতরে:

```bash
python -m venv myenv
```

এতে `myenv` নামে virtual environment তৈরি হবে।

---

## 6️⃣ Virtual environment activate করা

Linux / Manjaro তে:

```bash
source myenv/bin/activate
```

Activate হলে terminal এমন দেখাবে:

```text
(myenv) anan@manjaro $
```

---

## 7️⃣ pip upgrade (recommended)

```bash
pip install --upgrade pip
```

---

## 8️⃣ FastAPI install করা

```bash
pip install fastapi uvicorn
```

Check করতে:

```bash
pip list
```

---

## 9️⃣ FastAPI project file বানানো

Project folder এ `main.py` বানাও:

```bash
nano main.py
```

এখানে লেখো:

```python
from fastapi import FastAPI

app = FastAPI()

@app.get("/")
def root():
    return {"message": "Hello FastAPI"}
```

Save করে বের হও।

---

## 🔟 FastAPI project run করা

Terminal এ (venv active থাকা অবস্থায়):

```bash
uvicorn main:app --reload
```

Output এ দেখাবে:

```text
Uvicorn running on http://127.0.0.1:8000
```

---

## 1️⃣1️⃣ Browser এ দেখো

Browser খুলে যাও:

* App:

```
http://127.0.0.1:8000
```

* API Docs (Swagger UI):

```
http://127.0.0.1:8000/docs
```

এটা FastAPI নিজে থেকেই দেয়।

---

## 1️⃣2️⃣ Virtual environment বন্ধ করা

কাজ শেষ হলে:

```bash
deactivate
```

---

## ❌ Common mistakes (এগুলো এড়িয়ে চলবে)

* `sudo pip install fastapi` ❌
* venv activate না করে pip install ❌
* project external drive এ রাখা ❌
* global Python ব্যবহার করা ❌

---

## ✅ Correct workflow (Short)

```text
Create project folder
↓
Create venv
↓
Activate venv
↓
Install FastAPI
↓
Run uvicorn
```

---

## 🧠 Flutter + FastAPI context

* Flutter → API call করে
* FastAPI → logic handle করে
* Database → FastAPI থেকে access হয়

Flutter কখনো সরাসরি database এ যায় না।

---

## 🔚 Summary

* FastAPI = backend framework
* Virtual env = safety + stability
* Uvicorn = server runner
* VS Code + Terminal = perfect combo

---
