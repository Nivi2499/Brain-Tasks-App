\# Brain Tasks App – DevOps Practice Project



\## Project Overview



This repository contains production-ready static application files from the `dist` directory. The application is containerized and deployed to AWS EKS using Docker, Kubernetes, and AWS CI/CD services.



\## Technologies Used



\- Docker and Nginx

\- Kubernetes

\- Amazon ECR

\- Amazon EKS

\- AWS CodeBuild

\- AWS CodePipeline

\- Amazon CloudWatch

\- GitHub



\## Project Architecture



GitHub → AWS CodePipeline → AWS CodeBuild → Amazon ECR → Amazon EKS → Load Balancer → Application



Amazon CloudWatch is used for monitoring and log collection.



\## Docker Configuration



The application is served using Nginx on port 3000.



Build Docker image:



```bash

docker build -t brain-tasks-app:v1 .

```



Run locally:



```bash

docker run -d -p 3000:3000 brain-tasks-app:v1

```



Access: http://localhost:3000



\## AWS Configuration



\- Region: ap-southeast-2 (Sydney)

\- EKS Cluster: brain-tasks-cluster

\- Node Group: brain-tasks-nodes

\- ECR Repository: brain-tasks-app

\- CodeBuild Project: brain-tasks-build

\- CodePipeline: brain-tasks-pipeline



\## Kubernetes Deployment



Kubernetes manifests are available in the `k8s/` directory.



Deploy the application:



```bash

kubectl apply -f k8s/deployment.yaml

kubectl apply -f k8s/service.yaml

```



Verify:



```bash

kubectl get pods

kubectl get services

```



\## Application URL



http://add9f7c4098d5434580051407df10363-1723526793.ap-southeast-2.elb.amazonaws.com



\## CI/CD Pipeline



The AWS CodePipeline is connected to the GitHub main branch.



When code changes are pushed:



1\. CodePipeline detects the changes.

2\. CodeBuild builds the Docker image.

3\. The image is pushed to Amazon ECR.

4\. The Kubernetes deployment is updated on Amazon EKS.



\## CloudWatch Monitoring



CloudWatch Observability is configured with these log groups:



\- `/aws/containerinsights/brain-tasks-cluster/application`

\- `/aws/containerinsights/brain-tasks-cluster/dataplane`

\- `/aws/containerinsights/brain-tasks-cluster/host`

\- `/aws/containerinsights/brain-tasks-cluster/performance`

\- `/aws/codebuild/brain-tasks-build`



\## Project Outcome



\- Dockerized the application using Nginx.

\- Published the Docker image to Amazon ECR.

\- Deployed the application to Amazon EKS.

\- Exposed the application through a public Load Balancer.

\- Implemented CI/CD using AWS CodeBuild and CodePipeline.

\- Configured CloudWatch logging and observability.



\## GitHub Repository



https://github.com/Nivi2499/Brain-Tasks-App



Note: The Kubernetes LoadBalancer currently provisions a Classic Load Balancer, which does not have an ELBv2 ARN.

