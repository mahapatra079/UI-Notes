# Deployment Process:-

Deployment Process (Jenkins) - In Jenkins, the deployment process starts by triggering the build on a commit. 
                               Jenkins cleans the workspace, clones the source code, and prepares the environment. 
                                    
                               Then it builds the application, creates a Docker image, and pushes the image to ECR. After that, Jenkins pulls the image, stops any running container, deploys the new container, cleans up temporary files, and finally runs post-deployment actions like notifications.

 Note: ECR (Elastic Container Registry) is an AWS service that manages Docker image repositories.

**Note:** CI/CD pipeline creates image and pushes to cloud. At deployment time, image is pulled from cloud and container is built from it.

            Flow - 🔁 Jenkins Deployment Flow (AWS + Nginx) : -

                        Jenkins triggers on commit

                        Code is cloned

                        UI is built (npm run build)

                        Docker image is created with Nginx

                        Image is pushed to AWS ECR

                        AWS EC2 server pulls image from ECR

                        Old container is stopped

                        New Nginx container is started on EC2

                        UI is served via Nginx

        Note : Our UI is deployed as an Nginx Docker image stored in AWS ECR and runs on AWS EC2.

        Docker is a container tool that packages an application, its runtime, and dependencies into another container, so it runs the same in every environment.
        (Build once, run anywhere) 


        Note: Nginx and AWS API Gateway serve similar functions as reverse proxies and request routing layers,
              though they operate at different levels

              Request Routing & Load Balancing:

                Both can route requests to different backend services

                Both support load balancing across multiple targets

                Both handle SSL/TLS termination


# UI App Deployment using Jenkins:-

UI code is pushed to Git, which triggers Jenkins. Jenkins builds the UI using npm, 
creates a versioned build, injects environment-specific API configs, 
and deploys it to a web server or cloud storage. Finally, we verify the UI is live.



# Deployment Process Summary

## Jenkins CI/CD Pipeline
**Trigger:** Git commit → **Build:** UI + Docker image → **Deploy:** AWS ECR → AWS EC2 → Nginx container


## Key Components
- **Jenkins:** Automates build and deployment
- **Docker:** Packages UI + Nginx into portable container
- **AWS ECR:** AWS registry storing Docker images
- **AWS EC2:** AWS server running Docker containers
- **Nginx:** Web server serving UI from container

## Deployment Flow
1. Code commit triggers Jenkins
2. **Code Quality Checks:** Lint errors, tests (PR for GitHub / MR for GitLab)
3. **Build:** UI (npm run build)
4. **Tests:** Unit/Integration tests
5. **Deploy:** Create Docker image with Nginx
6. Push to AWS ECR
7. AWS EC2 pulls image and deploys new container, stops old one
8. UI served via Nginx on AWS EC2

## Docker Components
| Component  | Purpose                         |
| ---------- | ------------------------------- |
| Dockerfile | Build instructions              |  
| Image      | Read-only template              |
| Container  | Running instance                |
| Registry   | Image storage (AWS ECR)         |

## Nginx vs API Gateway
**Similarities:** Both handle request routing, load balancing, SSL termination
**Difference:** Nginx (self-managed) vs API Gateway (AWS managed service)

Git → Jenkins → Build → Docker Image → AWS ECR → AWS EC2 → Nginx Container
