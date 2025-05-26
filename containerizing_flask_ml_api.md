
# 📦 Containerizing a Flask API for ML Model Deployment with Docker

This guide outlines the key steps to containerize a Flask API serving a machine learning model, enabling smooth integration into an MLOps pipeline.

---

## 🚀 Prerequisites

- You have a working Flask API that serves your trained ML model.
- Docker is installed on your local system.
- Your project directory includes:
  - `app.py` (Flask app)
  - `model.pkl` or similar (your ML model)
  - `requirements.txt` (Python dependencies)

---

## 🧱 Step-by-Step Containerization

---

### 1. **Create a `Dockerfile`**

This file defines the container image for your Flask app.

```Dockerfile
# Use official lightweight Python image
FROM python:3.10-slim

# Set working directory
WORKDIR /app

# Copy files
COPY requirements.txt .
RUN pip install --no-cache-dir -r requirements.txt

COPY . .

# Expose Flask port
EXPOSE 5000

# Run the app
CMD ["python", "app.py"]
```

---

### 2. **Create a `.dockerignore` File**

Exclude unnecessary files from the Docker build context.

```
__pycache__/
*.pyc
*.pyo
*.pkl
*.ipynb
.env
.git/
```

---

### 3. **Build the Docker Image**

Run this in the terminal:

```bash
docker build -t flask-ml-api .
```

---

### 4. **Run the Container Locally**

```bash
docker run -d -p 5000:5000 flask-ml-api
```

- Access your API at `http://localhost:5000`.

---

### 5. **Test the API**

Use `curl`, Postman, or your frontend to hit the API endpoints and verify model responses.

---

### 6. **Tag and Push to a Container Registry** (Optional)

For CI/CD or MLOps deployment:

```bash
docker tag flask-ml-api yourdockerhubusername/flask-ml-api:latest
docker push yourdockerhubusername/flask-ml-api:latest
```

> You can also use **AWS ECR**, **Azure Container Registry**, or **GCP Artifact Registry**.

---

### 7. **Integrate into an MLOps Pipeline**

In your pipeline tool (e.g., GitHub Actions, Azure DevOps, GitLab CI/CD):

- Include steps for:
  - Docker image build
  - Unit/integration tests
  - Push to registry
  - Deploy to a Kubernetes cluster or cloud service (e.g., Azure App Service, AWS ECS/Fargate)

---

## ✅ Best Practices

- Use environment variables for secrets using `.env` and Docker's `--env-file`.
- Set up logging and error handling in your Flask app.
- Use multi-stage builds if your image becomes too large.
- Scan your Docker image for vulnerabilities (e.g., `docker scan`).

---

## 🛠 Example Project Structure

```
flask-ml-app/
├── app.py
├── model.pkl
├── requirements.txt
├── Dockerfile
└── .dockerignore
```
