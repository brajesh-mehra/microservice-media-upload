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
