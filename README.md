
- MongoDB uses **Persistent Volumes** for data durability
- Backend connects using `MONGODB_URI` environment variable
- Ingress routes `/` to frontend and `/api` to backend

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
