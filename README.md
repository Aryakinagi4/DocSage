# DocSage – Serverless Intelligent Document Processing System

DocSage is a distributed, serverless Intelligent Document Processing (IDP) platform designed to extract structured information from unstructured documents and enable conversational AI over document content.

The system is built using FastAPI microservices deployed as AWS Lambda container images behind API Gateway, with AWS-native storage, authentication, and CI/CD automation.

---

## 🚀 Core Capabilities

- 🔐 Secure authentication using AWS Cognito (JWT-based access control)
- 📄 Multi-format document upload with automatic PDF standardization
- ⚡ Serverless containerized microservices (Lambda + ECR)
- 🤖 Structured JSON extraction using Mistral-7B + LangChain
- 💬 Context-aware conversational Q&A over documents
- 🗂 Persistent conversation history per document
- 🧹 Cascade deletion ensuring complete data wipe
- 🔄 Automated CI/CD deployment pipeline

---

## 🏗 High-Level Architecture

DocSage follows a distributed microservices architecture where each service is independently deployed and scalable.

### 🔹 Entry Layer
- Amazon API Gateway (Proxy Integration)

### 🔹 Compute Layer
- AWS Lambda (Container Images via ECR)

### 🔹 Storage Layer
- Amazon S3 (Document storage)
- Amazon DynamoDB (Metadata + Conversations)

### 🔹 Security Layer
- Amazon Cognito (JWT issuance & validation)

### 🔹 DevOps Layer
- GitHub Actions → ECR → Lambda deployment

---

## 🧠 Service Breakdown

### 🔐 Auth Service
- Handles sign-up and login
- Issues JWT tokens
- Validates access for all services

### 📁 File Service
- Uploads files to S3
- Computes SHA-256 hash
- Converts to PDF
- Creates metadata record
- Handles cascade deletion

### 🤖 LLM Service
- Downloads PDF from S3
- Extracts raw text
- Generates structured JSON using Mistral
- Updates DynamoDB record

### 💬 Conversation Service
- Stores Q&A history
- Uses composite key:
  - Partition Key: user_id
  - Sort Key: file_hash#timestamp

---

## 🔄 Request Lifecycle Example

1. User uploads file → API Gateway  
2. File Service stores PDF in S3 and creates metadata entry  
3. LLM Service extracts structured data  
4. User asks questions → stored in DynamoDB  
5. File deletion triggers cascade wipe  

---

## 🛠 Technology Stack

### Backend
- FastAPI
- Pydantic
- Mangum
- LangChain

### Cloud
- AWS Lambda
- API Gateway
- ECR
- S3
- DynamoDB
- Cognito
- CloudWatch
- X-Ray

### Frontend
- React (Vite)

### DevOps
- Docker
- GitHub Actions

---

## ⚙️ Local Development

```bash
docker-compose up --build
```
### Services
- Auth → 8001
- File → 8002
- Conversation → 8003
- LLM → 8004

---

## 📄 License
MIT License
