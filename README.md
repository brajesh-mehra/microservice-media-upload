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


# Read Me First
The following was discovered as part of building this project:

* The original package name 'com.sunshaft.media-upload' is invalid and this project uses 'com.sunshaft.media_upload' instead.

# Getting Started

### Reference Documentation
For further reference, please consider the following sections:

* [Official Apache Maven documentation](https://maven.apache.org/guides/index.html)
* [Spring Boot Maven Plugin Reference Guide](https://docs.spring.io/spring-boot/3.4.2/maven-plugin)
* [Create an OCI image](https://docs.spring.io/spring-boot/3.4.2/maven-plugin/build-image.html)
* [Spring Web](https://docs.spring.io/spring-boot/3.4.2/reference/web/servlet.html)
* [Spring Data MongoDB](https://docs.spring.io/spring-boot/3.4.2/reference/data/nosql.html#data.nosql.mongodb)
* [Jersey](https://docs.spring.io/spring-boot/3.4.2/reference/web/servlet.html#web.servlet.jersey)
* [Spring Security](https://docs.spring.io/spring-boot/3.4.2/reference/web/spring-security.html)
* [OAuth2 Authorization Server](https://docs.spring.io/spring-boot/3.4.2/reference/web/spring-security.html#web.security.oauth2.authorization-server)
* [Spring Boot Actuator](https://docs.spring.io/spring-boot/3.4.2/reference/actuator/index.html)

### Guides
The following guides illustrate how to use some features concretely:

* [Building a RESTful Web Service](https://spring.io/guides/gs/rest-service/)
* [Serving Web Content with Spring MVC](https://spring.io/guides/gs/serving-web-content/)
* [Building REST services with Spring](https://spring.io/guides/tutorials/rest/)
* [Accessing Data with MongoDB](https://spring.io/guides/gs/accessing-data-mongodb/)
* [Securing a Web Application](https://spring.io/guides/gs/securing-web/)
* [Spring Boot and OAuth2](https://spring.io/guides/tutorials/spring-boot-oauth2/)
* [Authenticating a User with LDAP](https://spring.io/guides/gs/authenticating-ldap/)
* [Building a RESTful Web Service with Spring Boot Actuator](https://spring.io/guides/gs/actuator-service/)

### Maven Parent overrides

Due to Maven's design, elements are inherited from the parent POM to the project POM.
While most of the inheritance is fine, it also inherits unwanted elements like `<license>` and `<developers>` from the parent.
To prevent this, the project POM contains empty overrides for these elements.
If you manually switch to a different parent and actually want the inheritance, you need to remove those overrides.


