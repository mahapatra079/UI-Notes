# GCP  -  Google Cloud Platform; It is a cloud service platform provided by Google to host, deploy, and manage applications.

AS a Frontend Perspective; GCP is Google’s cloud platform used to deploy, host, and manage frontend applications.
As a frontend developer, I use GCP services like 

                                   -   Cloud Storage for static hosting - Upload HTML, CSS, JS files ; Enable public access ; Fast global 
                                   
                                   -   Cloud Run for deployment - Deploy Dockerized frontend apps; Auto-scaling; Pay only when used

                                   -   Firebase for authentication - Login , OTP, Email / Password

                                   -   Cloud CDN for performance optimization - It makes your website load faster worldwide.
                                   
                                   -   Monitoring & Logs - Check errors, Monitor performance, Debug production issues


Main Purpose  =  First, we build the frontend using npm run build. Then we either upload static files to Cloud Storage or create a Docker image and deploy it to Cloud Run.
                 The image is stored in Artifact Registry. After deployment, Cloud Run provides a public HTTPS URL.
                 For production, we use Cloud CDN and Load Balancer for performance and scalability.



## GCP Deployment Flow (Simple)

Git Commit → Jenkins → Build UI → Docker Image → GCP Artifact Registry → Cloud Run → Live URL

### Step-by-Step:
1. Code commit triggers Jenkins
2. UI is built (npm run build)
3. Docker image created with Nginx
4. Image pushed to **GCP Artifact Registry**
5. **Cloud Run** pulls image from Artifact Registry
6. Old container stopped, new container started
7. UI served via Nginx on Cloud Run
8. Access via HTTPS URL

### GCP vs AWS Comparison:

| Service Type       | AWS           | GCP                    |
| ------------------ | ------------- | ---------------------- |
| Image Storage      | ECR           | Artifact Registry      |
| Container Hosting  | EC2           | Cloud Run / GCE        |
| Static Hosting     | S3            | Cloud Storage          |
| CDN                | CloudFront    | Cloud CDN              |


API & Backend Connection :- Your frontend calls APIs hosted on

                            - Cloud Run
                            - App Engine
                            - Compute Engine

Note: You connect using - fetch("https://api.myapp.com/users")

