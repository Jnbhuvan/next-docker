

---

````md
# ✅ Next.js + Docker Setup (Zero Error Guide)



This document contains the complete step-by-step process to:

- Create a Next.js project
- Dockerize it correctly
- Build and run it without errors
- Fix common Docker Desktop issues on Windows

---

# ✅ 1. Create a New Next.js Project

Open terminal and run:

```bash
npx create-next-app@latest next-docker-app
````

### Recommended Options:

```
✔ TypeScript? → No (or Yes)
✔ ESLint? → Yes
✔ Tailwind CSS? → Optional
✔ Use src directory? → Yes
✔ App Router? → Yes
✔ Customize alias? → No
```

Move into project folder:

```bash
cd next-docker-app
```

---

# ✅ 2. Test Project Locally

Run development server:

```bash
npm run dev
```

Open browser:

```
http://localhost:3000
```

Stop server:

```bash
CTRL + C
```

---

# ✅ 3. Create Dockerfile (Main Step)

Inside the project root, create a file named:

```
Dockerfile
```

Paste the following:

```dockerfile
# -------------------------------
# Base Image
# -------------------------------
FROM node:18-alpine

# Set working directory inside container
WORKDIR /app

# -------------------------------
# Copy dependency files first
# -------------------------------
COPY package.json package-lock.json ./

# Install dependencies
RUN npm install

# -------------------------------
# Copy full source code
# -------------------------------
COPY . .

# -------------------------------
# Build Next.js app for production
# -------------------------------
RUN npm run build

# -------------------------------
# Expose Next.js port
# -------------------------------
EXPOSE 3000

# -------------------------------
# Start Next.js production server
# -------------------------------
CMD ["npm", "start"]
```

---

# ✅ 4. Create .dockerignore File (Important)

Create file:

```
.dockerignore
```

Paste:

```text
node_modules
.next
npm-debug.log
Dockerfile
.dockerignore
```

This avoids unnecessary files and reduces Docker image size.

---

# ✅ 5. Verify package.json Scripts

Open `package.json` and ensure scripts contain:

```json
"scripts": {
  "dev": "next dev",
  "build": "next build",
  "start": "next start"
}
```

⚠️ Docker requires `"start": "next start"` or container will fail.

---

# ✅ 6. Build Docker Image

Run:

```bash
docker build -t nextjs-docker-app .
```

Expected output:

```
Successfully built ...
Successfully tagged nextjs-docker-app
```

---

# ✅ 7. Run Docker Container

Run:

```bash
docker run -p 3000:3000 nextjs-docker-app
```

Now open:

```
http://localhost:3000
```

Your Next.js app is running inside Docker successfully.

---

# ✅ 8. Check Running Containers

```bash
docker ps
```

To stop container:

```bash
CTRL + C
```

OR

```bash
docker stop <container_id>
```

---

# ✅ 9. Common Docker Error Fix (Windows)

## ❌ Error:

```
error during connect:
open //./pipe/dockerDesktopLinuxEngine:
The system cannot find the file specified
```

### Meaning:

Docker Desktop engine is NOT running properly.

---

## ✅ Fix Steps

### Step 1: Start Docker Desktop

Open:

```
Start Menu → Docker Desktop
```

Wait until:

✅ Docker Desktop is running

---

### Step 2: Restart Docker Desktop

1. Close Docker Desktop
2. Open Task Manager
3. End tasks:

```
Docker Desktop
Docker Desktop Backend
com.docker.service
```

Restart Docker Desktop.

---

### Step 3: Test Docker Working

Run:

```bash
docker version
```

You must see both:

* Client
* Server

---

### Step 4: Test With Hello World

Run:

```bash
docker run hello-world
```

Expected:

```
Hello from Docker!
```

---

### Step 5: Enable WSL2 Backend

Run:

```bash
wsl --list --verbose
```

If missing, install:

```bash
wsl --install
```

Restart PC after install.

---

### Step 6: Enable Virtualization

Task Manager → Performance → CPU:

```
Virtualization: Enabled
```

If disabled → enable in BIOS.

---

### Step 7: Switch Docker to Linux Containers

System Tray → Docker Icon → Select:

```
Switch to Linux containers
```

---

### Step 8: Restart Docker Service

Press:

```
Windows + R → services.msc
```

Find:

```
Docker Desktop Service → Restart
```

---

# ✅ 10. Resume Project Entry

## Next.js Dockerized Web Application

**Tech Stack:** Next.js, Node.js, Docker

* Built a Next.js web application and containerized it using Docker for production deployment.
* Created Dockerfile and .dockerignore to optimize image build and runtime efficiency.
* Successfully deployed the application inside Linux containers with port mapping.

---

# ✅ Final Project Structure

```
next-docker-app/
│
├── Dockerfile
├── .dockerignore
├── package.json
├── next.config.js
├── src/
├── public/
└── ...
```

---

# ✅ Done!

This project demonstrates:

* Next.js Development
* Docker Containerization
* Deployment-Ready Workflow
* DevOps Fundamentals

```

---

If you want, I can provide the **best professional upgrade**:

✅ Multi-stage Dockerfile (smaller & faster)  
✅ Docker Compose file  
✅ Deploy to AWS / Render / Railway  
✅ Add GitHub-ready README template  

Just tell me.
```

<img width="1919" height="988" alt="image" src="https://github.com/user-attachments/assets/becd287d-0bab-4968-b8cb-2629e191cd5c" />
