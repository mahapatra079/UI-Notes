# Deployment Process:-

Deployment Process (Jenkins) - In Jenkins, the deployment process starts by triggering the build on a commit. 
                               Jenkins cleans the workspace, clones the source code, and prepares the environment. 
                                    
                               Then it builds the application, creates a Docker image, and pushes the image to ECR. After that, Jenkins pulls the image, stops any running container, deploys the new container, cleans up temporary files, and finally runs post-deployment actions like notifications.

 Note: ECR is a manages the Docker image repository provided by Nginx.

**Note:** CI/CD pipeline creates image and pushes to cloud. At deployment time, image is pulled from cloud and container is built from it.

            Flow - 🔁 Updated Jenkins Deployment Flow (with Nginx) : -

                        Jenkins triggers on commit

                        Code is cloned

                        UI is built (npm run build)

                        Docker image is created with Nginx

                        Image is pushed to ECR

                        Server pulls image from ECR

                        Old container is stopped

                        New Nginx container is started

                        UI is served via Nginx

        Note : Our UI is deployed as an Nginx Docker image stored in ECR.

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
**Trigger:** Git commit → **Build:** UI + Docker image → **Deploy:** ECR → Server → Nginx container


## Key Components
- **Jenkins:** Automates build and deployment
- **Docker:** Packages UI + Nginx into portable container
- **ECR:** AWS registry storing Docker images
- **Nginx:** Web server serving UI from container

## Deployment Flow
1. Code commit triggers Jenkins
2. **Code Quality Checks:** Lint errors, tests (PR for GitHub / MR for GitLab)
3. **Build:** UI (npm run build)
4. **Tests:** Unit/Integration tests
5. **Deploy:** Create Docker image with Nginx
6. Push to ECR
7. Deploy new container, stop old one
8. UI served via Nginx

## Docker Components
| Component  | Purpose                         |
| ---------- | ------------------------------- |
| Dockerfile | Build instructions              |  
| Image      | Read-only template              |
| Container  | Running instance                |
| Registry   | Image storage (ECR)             |

## Nginx vs API Gateway
**Similarities:** Both handle request routing, load balancing, SSL termination
**Difference:** Nginx (self-managed) vs API Gateway (AWS managed service)