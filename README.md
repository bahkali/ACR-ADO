# Container APP .NET Core MVC Project

This project is a Dockerized ASP.NET Core MVC application deployed to Azure using Azure DevOps for continuous integration and continuous deployment (CI/CD). 
The pipeline is set up with the classic editor for CI and YAML for CD.

## Project Overview

- **Technologies Used**: ASP.NET8 Core MVC, Docker, Azure, Azure Container Registry (ACR), Azure DevOps
- **Deployment Targets**: Development and Production staging environments on Azure
- **Continuous Integration (CI)** is configured with the classic editor in Azure DevOps.
- **Continuous Deployment (CD)** uses a YAML pipeline.

## Architecture Diagram

![Architecture Diagram](./ACR-ADO-driagram.drawio.svg)

## Table of Contents

- [Project Overview](#project-overview)
- [Architecture Diagram](#architecture-diagram)
- [Pipeline Status](#pipeline-status)
- [Getting Started](#getting-started)
- [Dockerizing the Application](#dockerizing-the-application)
- [Setting Up CI/CD Pipelines](#setting-up-cicd-pipelines)
- [References](#references)

## Pipeline Status

| Environment   | Status Badge                               | URL                          |
|---------------|-------------------------------------------|------------------------------|
| Development   | ![Dev Status](https://img.shields.io/badge/status-building-brightgreen) | [Development](#)              |
| Production    | ![Prod Status](https://img.shields.io/badge/status-building-blue) | [Production](#)               |

## Getting Started

### Prerequisites

- **Docker**: Ensure Docker is installed and running locally.
- **Azure Account**: You’ll need an Azure account to use Azure Container Registry and Azure Web App for Containers.
- **Azure DevOps Account**: Set up an organization and project in Azure DevOps.

### Setup Instructions

1. **Clone the Repository**:
   ```
   bash
   git clone https://github.com/your-repo-url.git
   cd your-repo


2. **Configure Environment Variables**: 

Set up required environment variables for accessing Azure resources, such as:
- AZURE_ACR_NAME: Azure Container Registry name.
- AZURE_SUBSCRIPTION: Azure subscription ID.
- DOCKER_IMAGE_NAME: Docker image name for the application.

### Dockerizing the Application

1. **Create Dockerfile**:
The Dockerfile is located in the containerapp folder and configures the application for deployment in Docker.
2. **Build Docker Image**:
    ```
    docker build -t your-image-name .


3. **Run Docker Container Locally**:
    ```
    docker run -p 8080:80 your-image-name




### Setting Up CI/CD Pipelines
### Continuous Integration (CI)
1. **CI Pipeline (Classic Editor)**:

Set up the CI pipeline using the classic editor in Azure DevOps to build and push the Docker image to Azure Container Registry.

2. **Steps for CI**:

- Build the Docker Image: Configure the build task to create the Docker image.
- Push to ACR: Push the image to Azure Container Registry.
### Continuous Deployment (CD)
**Sample YAML for CD**:
    ```
    trigger:
    - main

    pool: Default

    steps:
    - task: AzureWebAppContainer@1
    inputs:
        azureSubscription: '$(Azure subscription)'
        appName: '$(app name)'
        deployToSlotOrASE: true
        resourceGroupName: '$(resourceGroupName)'
        slotName: 'production'
        containers: '$(image name)'

### References
- ![Azure DevOps Documentation](https://learn.microsoft.com/en-us/azure/devops/?view=azure-devops)
- ![Azure Container Registry](https://learn.microsoft.com/en-us/azure/container-registry/)
