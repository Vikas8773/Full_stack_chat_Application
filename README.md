# Full-Stack Chat Application with Kubernetes & Docker

[![GitHub Repo Size](https://img.shields.io/github/repo-size/Vikas8773/Full_stack_chat_Application)](https://github.com/Vikas8773/Full_stack_chat_Application)
[![GitHub Issues](https://img.shields.io/github/issues/Vikas8773/Full_stack_chat_Application)](https://github.com/Vikas8773/Full_stack_chat_Application/issues)
[![Docker Image Version](https://img.shields.io/badge/backend-Docker%20Image-blue)](https://hub.docker.com/r/vikassangale/chatapp-backend)
[![License](https://img.shields.io/badge/License-MIT-green)](LICENSE)

![ChatApp Screenshot](path/to/screenshot.png)
*Replace with your frontend screenshot if available*

---

## Table of Contents

- [Project Overview](#project-overview)
- [Features](#features)
- [Tech Stack](#tech-stack)
- [Architecture](#architecture)
- [Setup & Installation](#setup--installation)
- [Usage](#usage)
- [Kubernetes Deployment](#kubernetes-deployment)
- [Contributing](#contributing)
- [License](#license)

---

## Project Overview

This is a **full-stack chat application** built with **Node.js, Express, and MongoDB** for the backend, and a **modern frontend framework (React/Vue)** for the client interface.  
It is containerized using **Docker** and deployed on a **local Kubernetes cluster (kind)**.  
The app uses **StatefulSets** for MongoDB, persistent volumes for data, and **Ingress** for routing frontend and backend traffic.

---

## Features

- Real-time messaging with **WebSockets**
- User authentication and JWT-based sessions
- Message history stored in **MongoDB**
- Dockerized backend & frontend
- Kubernetes manifests for **PV/PVC, StatefulSet, Deployments, Services, and Ingress**
- Production-ready routing via **Nginx Ingress**
- Easy scalability with Kubernetes

---

## Tech Stack

| Layer        | Technology / Tool           |
|--------------|----------------------------|
| Frontend     | React / Vue                |
| Backend      | Node.js, Express           |
| Database     | MongoDB (StatefulSet)     |
| Container    | Docker                     |
| Orchestration| Kubernetes (kind)          |
| Networking   | Services, Ingress, Nginx  |
| Realtime     | WebSockets                 |
| CI/CD        | Optional: GitHub Actions   |

---

## Architecture



- **MongoDB** uses **Persistent Volumes** for data durability  
- **Backend** connects via `MONGODB_URI` environment variable  
- **Ingress** routes `/` to frontend and `/api` to backend  

---

## Setup & Installation

### Prerequisites

- Docker  
- kind (Kubernetes in Docker)  
- kubectl  
- Node.js & npm  

### Local Development

1. Clone the repo:

```bash
git clone https://github.com/Vikas8773/Full_stack_chat_Application.git
cd Full_stack_chat_Application

