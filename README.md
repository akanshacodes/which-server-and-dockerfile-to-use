# 🚀 Server Selection Guide

### 💡 *Which Server Runs What? (DevOps Cheat Sheet)*

<p align="center">
  <img src="https://img.shields.io/badge/DevOps-Guide-blue?style=for-the-badge" />
  <img src="https://img.shields.io/badge/Beginner-Friendly-success?style=for-the-badge" />
  <img src="https://img.shields.io/badge/Interview-Ready-orange?style=for-the-badge" />
</p>

---

## 🌟 Why This Guide?

Many developers get confused about:

❓ Which server to use?
❓ Which file builds what?
❓ How to identify project type quickly?

👉 This guide solves everything in a **simple + practical way**.

---

# 🧠 Step 1: Identify Build Tool

```bash
.csproj/Program.cs            → .NET
pom.xml                       → Maven  
build.gradle                  → Gradle  
package.json                  → Node.js  
requirements.txt              → Python  
composer.json                 → PHP  
```

---

# 📦 Step 2: Identify Build Output (Artifact)

```bash
Java (Spring Boot) → .jar  
Java Web App       → .war  
React/Angular      → build/ or dist/  
Node/Python        → No build (runs directly)  
```

---

# ⚙️ Step 3: Choose Server

## ☕ Java Applications

```bash
.jar  → Embedded Server (Spring Boot)
.war  → Tomcat (Servlet Container)
```

---

## 🌐 Frontend Applications

```bash
React / Angular / HTML → Nginx
```

---

## ⚙️ Backend Applications

```bash
Node.js   → Node runtime (Express)
Python    → Gunicorn / uWSGI
PHP       → PHP-FPM + Nginx
.NET      → Kestrel / IIS
```
| Application | Server          |
| ----------- | --------------- |
| Java WAR    | Tomcat          |
| Java JAR    | Embedded Server |
| React       | Nginx           |
| Node.js     | Node Runtime    |
| Python      | Gunicorn        |
| PHP         | PHP-FPM + Nginx |

---

# ❌ Common Mistake

```bash
❌ Using Nginx for Java apps
```

👉 Why wrong?

* Nginx cannot run `.jar` or `.war`
* It only serves static content
* Works as reverse proxy

---

# 🔥 Real Production Architecture

```bash
Client → Nginx → Application Server → Database
```

### 💡 Examples:

```bash
Nginx → Tomcat → MySQL  
Nginx → Node.js → MongoDB  
Nginx → Gunicorn → Django  
```

---

# 🎯 Quick Decision Trick

✔️ Check build file
✔️ Check folder structure
✔️ Identify output
✔️ Select server

---

# 🎨 Visual Flow

```mermaid
flowchart LR
    A[Project Files] --> B{Identify Type}
    B -->|pom.xml| C[Java App]
    B -->|package.json| D[Node App]
    B -->|requirements.txt| E[Python App]

    C --> F{Output}
    F -->|WAR| G[Tomcat]
    F -->|JAR| H[Embedded Server]

    D --> I[Node Runtime]
    E --> J[Gunicorn]

    G --> K[Production Setup]
    H --> K
    I --> K
    J --> K

    K --> L[Nginx Reverse Proxy]
```

---

# 💎 Pro Tips

✨ Server depends on **runtime**, not guess
✨ Nginx = frontend + proxy (not backend runtime)
✨ Always identify project before writing Dockerfile

---
