
# Self Introduction

1. Self Introduction
2. Tell me about yourself
3. curretly which project you are woking on - ecommerce microservices
4. what are the tools - git, jenkins, terrafrom &ansible, docker & kubernetes, prometheus & grafana
5. what kind of technology used in the project - java``?
->  Creating infrastrcuture for all environement DEV, STAG, PROD server
->  Deployment - Developer develops the code, we use to write dockerfile for that code to deploy.
->  Storing - we store the image using dockerhub.
->  Download dependencies -Ansible is used to download and install the multiple denpendencies in the host at a time.
->  CI/CD - jenkins pipeline is used to automate the entire things.
->  Continious Delivery require manual approval before deploying into production. Continous Deployment directly deploys in production.    

6. Explain your current CI/CD setup?
-> Currently we are using Jenkins for continious integration and continious deployment. we use Github as soucre code repository, we configured git hub webhook that will trigger the jenkins pipeline (Orchestrater) for every commit. 
-> The source is GITHUB and the target platform is kubernetes.

``Continious Integration``
These pipeline has multiple stages
-> Checkout stage - In this stage we checkout the code that user has made
-> Build & UT stage - We use javac(written in java to build backend) for building and Unit Test Framework in the code repository.
-> Code Scan - we use sonarqube repository to check the security vulnerability that code is free from any security.
-> Image Build - we use Dockerfile in the git repository to build container image.
-> Image Scan - we check the binaries(.exe), default packages and base image are free from vulnerabilities
-> Image Push - We push the image to AWS ECR.
->These are multiple stages that are in continious integration, we write declerative jenkins file  pipeline (jenkins groovy scripting) in Jenkis for Orchstrating each of them

``Continous Delivery``
-> we use jenkins pipeline and update this image in the kubernetes manifest
-> we push this updated image to git hub repository (different from source code repository) to hold these manifest and host helm chart repo on github using github pages.
-> we use gitops tools argocd (watch for updates) to deploy the image in kubernetes by pushing any changes made.

7. How do you handle secrets?
-> Currently iam woking on AWS we use AWS Seceret Manager to store the sensitive information
-> In GitHub there is an option called GitHub actions that stores sensitive info like passwords, secrets and tokens at differnt levels like organisation, repository and repository envi.
-> repository - gh secret set SECRET_NAME
-> environment - gh secret set --env ENV_NAME SECRET_NAME
-> organisation - gh secret set --org ORG_NAME SECRET_NAME
