<h1 align="center">🚀 SIT737 - Task 5.2D: Microservice Dockerization & Cloud Deployment 🌐</h1>

<p align="center">
  <img src="https://img.shields.io/badge/status-completed-brightgreen?style=flat-square" alt="Status: Completed" />
  <img src="https://img.shields.io/badge/docker-ready-blue?style=flat-square&logo=docker" alt="Docker: Ready" />
  <img src="https://img.shields.io/badge/cloud-google--artifact--registry-yellow?style=flat-square&logo=googlecloud" alt="Cloud: Google Artifact Registry" />
</p>

<p align="center">
  <img src="https://cdn.dribbble.com/users/24711/screenshots/12414818/media/c9cb36b0f938daae6f45f23e9de5d702.gif" width="80%" alt="Microservice Deployment Animation" />
</p>

---

## 📦 Project Overview

This repository contains the source code and Docker configuration for a **Node.js-based microservice**, developed for SIT737 Cloud-Native Application Development. The project's core objective is to **Dockerize** the microservice and **deploy it to Google Cloud's Artifact Registry**, enabling efficient, scalable, and production-ready container management.

---

## 🧠 Key Technologies Used

| Tool                             | Purpose                                 |
| :------------------------------- | :-------------------------------------- |
| 🐳 **Docker** | Containerizing the microservice         |
| ☁️ **Google Cloud Artifact Registry** | Hosting Docker images securely          |
| 🔧 **Node.js + Express** | Microservice backend                    |
| 💻 **VS Code** | Development environment                 |
| 🐙 **GitHub** | Code hosting & version control          |

---

## 📁 Project Structure

```
sit737-2025-prac5d/
├── Dockerfile
├── package.json
├── server.js (or index.js)
└── README.md
```

---

## 🛠️ Setup Instructions

### 🔗 Clone this repository

```bash
git clone https://github.com/Tillu6/sit737-2025-prac5d.git
cd sit737-2025-prac5d
```

### 🐳 Build and Run the Docker Image Locally

```bash
docker build -t microservice-image:latest .
docker run -p 3000:3000 microservice-image:latest
```

Then open: http://localhost:3000

### ☁️ Publishing to Google Cloud (Artifact Registry)

#### ✅ Step 1: Enable API

```bash
gcloud services enable artifactregistry.googleapis.com
```

#### ✅ Step 2: Create Docker Repository

```bash
gcloud artifacts repositories create microservice-repo \
  --repository-format=docker \
  --location=us-central1 \
  --description="Docker repository for SIT737"
```

#### ✅ Step 3: Authenticate Docker with Artifact Registry

```bash
gcloud auth login
gcloud auth configure-docker us-central1-docker.pkg.dev
```

#### ✅ Step 4: Tag & Push Docker Image

```bash
docker tag microservice-image:latest \
  us-central1-docker.pkg.dev/sit737-microservice/microservice-repo/microservice-image:latest

docker push \
  us-central1-docker.pkg.dev/sit737-microservice/microservice-repo/microservice-image:latest
```

📝 **Replace `sit737-microservice` with your actual GCP project ID.**

#### ✅ Step 5: Test Pulled Image (Optional)

```bash
docker run -p 3000:3000 \
  us-central1-docker.pkg.dev/sit737-microservice/microservice-repo/microservice-image:latest
```

#### ✅ Deployment Verified!

✔️ Dockerized
✔️ Published to Cloud
✔️ Pullable & Runnable from Artifact Registry

---

### 📸 Screenshots

<p align="center">
  "<img width="868" alt="last" src="https://github.com/user-attachments/assets/d8ee0887-2085-495a-93f3-a5665f47ad5c" />
  <br />
  <i>↑ Docker image successfully pushed to Artifact Registry</i>
</p>

---

### 🤝 Contributing

This is a solo student project for SIT737. However, feel free to fork and experiment with this repository for learning or extension!

---

### 📬 Contact

Made with ❤️ by Saketh Reddy Poreddy
<br />
👨‍🎓 Master of Cyber Security (Professional), Deakin University
<br />
📧 sakethreddy015@gmail.com

<p align="center">
  <b>“Containers aren't just the future, they're the present.”</b> 💡
</p>
