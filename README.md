# microservice-media-upload
This service will upload media on AWS s3 bucket

# High-Level Architecture
Key Components
Client: Sends upload requests via API Gateway.
API Gateway: Manages all incoming requests and routes them to the backend service.
Kubernetes Cluster (EKS): Hosts the application to ensure scalability and fault tolerance.
Backend Service (Spring Boot / Node.js / Python FastAPI): Handles upload logic and integrates with AWS services.
AWS S3: Stores uploaded media files.
AWS Secrets Manager: Manages S3 credentials securely.
Caching Layer (Redis): Optimizes performance for frequently accessed data.
AWS CloudWatch: Monitors logs and application health.
AWS SNS / SQS (Optional): Can be used for asynchronous processing.
