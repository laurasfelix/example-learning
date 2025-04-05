# 🚀 React + Flask + MongoDB Guide for College Students

hey there!

wanna learn react and it's looking very complex and difficult?

worry no more. follow these steps below to become more familiar with coding/react!

---

## 🌱 first step: setup nextjs baseline

do this on terminal:

```bash
npx create-next-app@latest .
```

if it asks you questions, just hit enter for everything — but choose **TypeScript** if it gives you the option!

---

## 💻 second step: start dev server

run this:

```bash
npm run dev
```

this starts up a local server for you to play around with! click on the first `localhost` link to see live updates to your website :)

---

## 🔍 third step: dora the explorer

look around the project's structure and try to familiarize yourself with it.

when you open the localhost site, what you see is coming from `pages/index.tsx`. try editing it and see what happens!

---

## 👶 fourth step: baby's first react component

1. create a folder called `components` in your main directory
2. under it, make a file called `about.tsx`

inside `about.tsx`, write this:

```tsx
export default function About() {
  return (
    <div>
      <h1>about the dev</h1>
      <p>I'm YOUR NAME and this is my first react component!!!!!!</p>
    </div>
  );
}
```

> you can customize this more if you know HTML, but if not, no worries :)

---

### 📦 now call your new component!

go to `pages/index.tsx`, and:

1. at the top, add:
```tsx
import About from "@/components/about";
```

2. inside the return statement:
```tsx
<About />
```

boom. you made your first react component and now you kind of understand how this works ✨

---

## 🌈 future react steps

- learn `useState` and `useEffect`
- add CSS styles
- create more components
- make your app interactive!

---

# 🔁 bonus round: backend basics using flask + mongodb 🧪

frontend is cool... but what if you wanna **save data** or do **cool server-side things**?

worry not. backend isn't as scary as it seems. let's get you started with **Flask** (tiny but powerful Python web framework) and **MongoDB** (a database where you can store stuff)!

---

## 📁 step 0: make a new folder for your backend

keep things tidy 🧼

```bash
mkdir backend
cd backend
```

---

## 🧪 step 1: setup a virtual environment

```bash
python -m venv venv
```

activate it:

- mac/linux:
  ```bash
  source venv/bin/activate
  ```
- windows:
  ```bash
  venv\Scripts\activate
  ```

you should now see `(venv)` in your terminal

---

## 📦 step 2: install flask and pymongo

```bash
pip install flask pymongo flask-cors
```

> `flask-cors` lets your frontend and backend talk without CORS errors

---

## 🔥 step 3: baby’s first flask server

create a file called `app.py`or whatever else and paste this: 
ps: don't forget to replace "mongodb://localhost:27017/" with whatever ur actual mongodb uri is 

```python
from flask import Flask, jsonify, request
from flask_cors import CORS
from pymongo import MongoClient

app = Flask(__name__)
CORS(app)

client = MongoClient("mongodb://localhost:27017/")
db = client["mydatabase"]
collection = db["messages"]

@app.route("/")
def hello():
    return jsonify(message="hello from your flask server!")

@app.route("/messages", methods=["POST"])
def save_message():
    data = request.get_json()
    collection.insert_one(data)
    return jsonify(message="message saved!")

@app.route("/messages", methods=["GET"])
def get_messages():
    messages = list(collection.find({}, {"_id": 0}))
    return jsonify(messages)

if __name__ == "__main__":
    app.run(debug=True)
```

---

## 🚀 step 4: run your flask server

in the backend folder:

```bash
python app.py
```

you should see:

```
 * Running on http://127.0.0.1:5000
```

you now have a working backend!!! 🎉

---

## 🔗 connecting react to your backend

### send data (POST)

```ts
await fetch("http://localhost:5000/messages", {
  method: "POST",
  headers: {
    "Content-Type": "application/json"
  },
  body: JSON.stringify({ name: "Laura", msg: "React is fun" })
});
```

### get data (GET)

```ts
const res = await fetch("http://localhost:5000/messages");
const data = await res.json();
console.log(data);
```

---

## 🛠️ future backend steps

- validate inputs
- display backend data in the frontend
- user auth (sessions/tokens)
- deploy your backend (render.com is beginner-friendly)

---

## 💡 wanna go full-stack?

just keep going step by step. you're doing amazing.

feel free to fork this, make it your own, or share with friends who are also figuring this stuff out!

---
