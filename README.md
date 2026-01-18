## 🌥 Cloud Computing Demo Website (Node.js + AWS)

### 📌 Project Overview

This project is a simple **Node.js + Express** based web application designed to demonstrate core **cloud computing concepts**, including:

* Uses of Cloud Computing
* Types of Cloud (Public, Private, Hybrid)
* Introduction to AWS Cloud Services

The application is deployed on an **AWS EC2 instance** and exposed via port **3000**, making it accessible from anywhere over the internet.

---

### 🛠 Tech Stack

* **Node.js**
* **Express.js**
* **HTML, CSS, JavaScript**
* **AWS EC2**
* **NPM**

---

### ☁ Features

* Explains **cloud computing use cases**
* Describes **types of cloud deployment models**
* Demonstrates **AWS services overview**
* Lightweight Node.js backend
* Ready for cloud deployment

---

# 1️⃣ Install Node.js & NPM (RHEL / EC2 Amazon Linux)

### Update system

```bash
sudo yum update -y
```

### Install Node.js (recommended method)

```bash
sudo yum install nodejs npm -y
```

### Verify installation

```bash
node -v
npm -v
```

✔ You should see version numbers.

---

# 2️⃣ Project Setup Commands (Node.js + Express)

### Clone project from GitHub (or create manually)

```bash
git clone https://github.com/<your-username>/cloud-demo-site-node.git
cd cloud-demo-site-node
```

OR create manually:

```bash
mkdir cloud-demo-site-node
cd cloud-demo-site-node
npm init -y
```

---

### Install required dependency

```bash
npm install express
```

---

### Start the Node.js application

```bash
node server.js
```

OR (recommended for npm usage):

Add this in `package.json`:

```json
"scripts": {
  "start": "node server.js"
}
```

Then start using:

```bash
npm start
```

---

### Expected Output

```text
Server running on http://0.0.0.0:3000
```

---

# 3️⃣ AWS EC2 – Inbound Rule for Port 3000

To access the app **from anywhere**, you must open port **3000**.

### Steps in AWS Console:

1. Go to **EC2 Dashboard**
2. Click **Instances**
3. Select your instance
4. Click **Security → Security Groups**
5. Click **Edit inbound rules**
6. Add rule:

| Type       | Protocol | Port Range | Source    |
| ---------- | -------- | ---------- | --------- |
| Custom TCP | TCP      | 3000       | 0.0.0.0/0 |

(Optional IPv6)

```
::/0
```

7. Click **Save rules**

---

### Access from browser

```
http://<EC2-PUBLIC-IP>:3000
```

Example:

```
http://13.234.xxx.xxx:3000
```

---

# 4️⃣ IMPORTANT: Bind Node App to All Interfaces

In `server.js`:

```js
app.listen(3000, '0.0.0.0', () => {
  console.log('Server running on port 3000');
});
```

This is **mandatory** for EC2 access.

---

# 5️⃣ Firewall (RHEL) – Allow Port 3000

Check firewall:

```bash
sudo firewall-cmd --state
```

Open port:

```bash
sudo firewall-cmd --add-port=3000/tcp --permanent
sudo firewall-cmd --reload
```

---

### 🚀 How to Run Locally

```bash
npm install
npm start
```

Open browser:

```
http://localhost:3000
```

---

### 🌍 Deployment on AWS EC2

1. Launch EC2 instance
2. Install Node.js & npm
3. Open inbound rule for port **3000**
4. Start application using `npm start`
5. Access using:

```
http://<EC2-PUBLIC-IP>:3000
```

---

### 🎯 Use Case

This project is ideal for:

* Cloud computing labs
* AWS EC2 practice
* Node.js beginners
* DevOps / Cloud interviews
* GitHub portfolio projects

---

### 👤 Author

**Devang**
Cloud & DevOps Enthusiast

--- 

Just tell me 👌
