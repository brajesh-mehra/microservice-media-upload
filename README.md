# microservice-media-upload
This service will upload media on AWS s3 bucket

# High-Level Architecture
Key Components:
1. Client: Sends upload requests via API Gateway.
2. API Gateway: Manages all incoming requests and routes them to the backend service.
3. Kubernetes Cluster (EKS): Hosts the application to ensure scalability and fault tolerance.
4. Backend Service (Spring Boot / Node.js / Python FastAPI): Handles upload logic and integrates with AWS services.
5. AWS S3: Stores uploaded media files.
6. AWS Secrets Manager: Manages S3 credentials securely.
7. Caching Layer (Redis): Optimizes performance for frequently accessed data.
8. AWS CloudWatch: Monitors logs and application health.
9. AWS SNS / SQS (Optional): Can be used for asynchronous processing.

# System Flow
Client Uploads File:

1. User sends an HTTP POST request to the API Gateway.
2. API Gateway routes the request to the backend.
3. Backend Handles Upload:
4. Retrieves S3 credentials from AWS Secrets Manager.
5. Generates a pre-signed URL for secure direct upload.
6. Returns the pre-signed URL to the client.Client Uploads File to S3 Directly:
7. The client uploads the file to S3 using the pre-signed URL.
8. Database & Caching (Optional):
9. If needed, metadata (file size, URL, owner) is stored in PostgreSQL / DynamoDB.
10. Frequently accessed file details can be cached in Redis.
