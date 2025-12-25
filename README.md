# Full-Stack Chat Application with Kubernetes & Docker

[![GitHub Repo Size](https://img.shields.io/github/repo-size/Vikas8773/Full_stack_chat_Application)](https://github.com/Vikas8773/Full_stack_chat_Application)
[![GitHub Issues](https://img.shields.io/github/issues/Vikas8773/Full_stack_chat_Application)](https://github.com/Vikas8773/Full_stack_chat_Application/issues)
[![Docker Image Version](https://img.shields.io/badge/backend-Docker%20Image-blue)](https://hub.docker.com/r/vikassangale/chatapp-backend)
[![License](https://img.shields.io/badge/License-MIT-green)](LICENSE)


---

## Table of Contents

- [Project Overview](#project-overview)
- [Features](#features)
- [Tech Stack](#tech-stack)
- [Architecture](#architecture)
- [Setup & Installation](#setup--installation)
- [Usage](#usage)
- [Kubernetes Deployment Notes](#kubernetes-deployment)

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

---

## Architecture Diagram

```text
Browser
   |
   v
+----------------+
| Nginx Ingress  |
+----------------+
        |
        +----------------------------+
        |                            |
        v                            v
+-------------------+     +---------------------------+
| Frontend Service  |     | Backend Service           |
| (React / Vue)     |     | (Node.js / Express)       |
+-------------------+     +---------------------------+
                                     |
                                     v
                          +---------------------------+
                          | MongoDB StatefulSet       |
                          | (Persistent Volume / PVC) |
                          +---------------------------+
``` 


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
``` 


2. Build Docker images:

```bash
docker build -t chatapp-backend ./backend
docker build -t chatapp-frontend ./frontend
``` 


3. Start kind cluster:

```bash
kind create cluster --name chatapp
``` 


4. Apply Kubernetes manifests:

```bash
kubectl apply -f k8s/namespace.yml
kubectl apply -f k8s/mongo-pv.yml
kubectl apply -f k8s/mongo-secret.yml
kubectl apply -f k8s/mongo-headless-service.yml
kubectl apply -f k8s/mongo-statefulset.yml
kubectl apply -f k8s/backend-secret.yml
kubectl apply -f k8s/backend-deployment.yml
kubectl apply -f k8s/backend-service.yml
kubectl apply -f k8s/frontend-deployment.yml
kubectl apply -f k8s/frontend-service.yml
kubectl apply -f k8s/chatapp-ingress.yml
``` 

5. Port-forward services:

```bash
kubectl port-forward service/frontend 80:80 -n chat-app
kubectl port-forward service/backend 5001:5001 -n chat-app
``` 


6. Access the frontend:

```bash
http://localhost:80
``` 

---

## Usage
- Signup and login using email and password
- Send and receive real-time messages
- Messages are persisted in MongoDB
- Admin can view user statistics and chat history

---

## Kubernetes Deployment Notes

- MongoDB runs as StatefulSet with PV/PVC
- Backend & Frontend run as Deployments
- Ingress routes traffic based on host/path
- DB credentials are managed using Kubernetes Secrets
