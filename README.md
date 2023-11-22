# cloudsite
microsoft azure project

Project Title:

Dockerization and Deployment of a Static Website on Azure Container Instances


Problem Statement/Opportunity:
[Identify the specific problem or opportunity that this project aims to address. This could include issues related to scalability, portability, or efficiency in deploying and managing a static website.]

Project Description:
Objective:
The primary objective of this project is to demonstrate the process of creating a Docker image from an Azure Virtual Machine (VM) containing a static website, pushing the Docker image to Azure Container Registry (ACR), and deploying a container instance using the image stored in ACR.

Prerequisites:
1. Azure subscription with access to Azure Portal.
2. Azure Virtual Machine with a static website deployed.
3. Docker installed on the Azure Virtual Machine.

Step 1: Create a Dockerfile
Create a Dockerfile in the root directory of your static website on the Azure Virtual Machine. The Dockerfile specifies the steps to build the Docker image.

Example Dockerfile:

# Use an official Nginx image as the base image
FROM nginx:latest

# Copy the static website files to the Nginx default directory
COPY /path/to/your/static/website /usr/share/nginx/html

# Expose port 80 for web traffic
EXPOSE 80

# Command to run when the container starts
CMD ["nginx", "-g", "daemon off;"]


Step 2: Build the Docker Image
Open a terminal on the Azure Virtual Machine and navigate to the directory containing the Dockerfile. Run the following command to build the Docker image:

docker build -t your-image-name:tag .
Replace your-image-name with a meaningful name for your image, and tag with a version or label for the image.

Step 3: Azure Container Registry Setup
Navigate to the Azure Portal.
Create a new Azure Container Registry.
Note the ACR login server URL, username, and password.

Step 4: Login to Azure Container Registry
Run the following command on the Azure Virtual Machine to log in to the ACR using the credentials obtained in Step 3:

docker login <acr-login-server> -u <username> -p <password>
Replace <acr-login-server>, <username>, and <password> with your ACR details.

Step 5: Tag and Push the Docker Image
Tag the Docker image with the ACR login server and push it to the ACR:

docker tag your-image-name:tag <acr-login-server>/your-image-name:tag
docker push <acr-login-server>/your-image-name:tag

Step 6: Deploy Container Instance from ACR
Navigate to the Azure Portal.
Create a new Azure Container Instance.
Specify the ACR image URL (e.g., <acr-login-server>/your-image-name:tag).
Configure the necessary settings (e.g., resource group, networking, etc.).
Deploy the container instance.


Conclusion:
This documentation provides a detailed guide on Dockerizing a static website on an Azure Virtual Machine, pushing the image to Azure Container Registry, and deploying a container instance. Following these steps ensures a streamlined process for containerization and deployment on the Azure platform.
