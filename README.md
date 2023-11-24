<h2>Project Title:</h2>
<h3>WEBSITE RELATED SHIVAJIRAO NAGAWADE</h3>
-Created And Managed website related shivajirao nagawade(His work in various fields like 
Education, Politics, Industry, social work)
<h5>Technologies used:</h5> HTML | CSS | php | javascript

<h6>Dockerization and Deployment of a Static Website on Azure Container Instances</h6>

<h2>Problem Statement/Opportunity:</h2>
Identify the specific problem or opportunity that this project aims to address. This could include issues related to scalability, portability, or efficiency in deploying and managing a static website.]
<h2>Azure Services</h2>
<h4>1.Virtual Machine</h4>
<h4>2.Container Registries</h4>
<h4>3.Container Instances</h4>

<h2>Project Description:</h2>
<h3>Objective:</h3>
The primary objective of this project is to demonstrate the process of creating a Docker image from an Azure Virtual Machine (VM) containing a static website, pushing the Docker image to Azure Container Registry (ACR), and deploying a container instance using the image stored in ACR.

<h3>Prerequisites:</h3>
 <h4>1. Azure subscription with access to Azure Portal.</h4>
 Container registries are repositories for storing and distributing container images. In the context of software development and deployment, a container is a lightweight, standalone, and executable software package that includes everything needed to run a piece of software, including the code, runtime, libraries, and system tools. Containers are often used for packaging and deploying applications in a consistent and reproducible way across different environments.

A container registry is a centralized storage system that allows you to upload, download, and manage container images. These images are typically used with container orchestration platforms like Kubernetes or container runtime environments like Docker. The registry serves as a hub for sharing and distributing container images among developers, teams, and systems.

![Screenshot 2023-11-22 174534](https://github.com/renukashelake/cloudsite/assets/124230859/b5ee0ab2-652d-4372-97ee-2d06a245f90d)


<h5>Key features of container registries include:</h5>

<h5>Image Storage:</h5> 
Container registries store container images, which are essentially snapshots of a file system with metadata describing the image and its dependencies.

<h5>Distribution:</h5> 
Container registries provide a way to distribute container images to different environments or systems. This is crucial in a distributed and scalable architecture.

<h5>Versioning:</h5> 
Container registries support versioning of images, allowing developers to use specific versions of an application or service.

</h5>Access Control:</h5> 
Registries often have access control mechanisms to restrict who can push or pull images. This helps in managing permissions and securing the distribution process.

<h5>Integration with Orchestration Platforms:<h5> 
Container registries are often integrated with container orchestration platforms like Kubernetes, making it easy to deploy and manage containerized applications at scale.

<h5>Popular container registries include:</h5>

<h5>Docker Hub:</h5> 
A public registry hosted by Docker that allows users to share and access container images.

<h5>Google Container Registry (GCR):</h5> 
A private container registry service provided by Google Cloud Platform.

<h5>Amazon Elastic Container Registry (ECR):</h5> 
A private container registry service provided by Amazon Web Services.

</h5>Azure Container Registry (ACR):</h5>
A private container registry service provided by Microsoft Azure.

<h4>2. Azure Virtual Machine with a static website deployed.</h4>
<h5>1. Create an Azure Virtual Machine:</h5>
<h6>Sign in to the Azure Portal:</h6>

Go to Azure Portal.
Sign in with your Azure account.
Create a Virtual Machine:

Click on "Create a resource" in the left sidebar.
Search for "Windows Server" or "Linux" depending on your preference and select the appropriate image.
Fill out the required information, such as resource group, VM name, region, etc.
Choose a size for your VM based on your needs.
Configure the networking settings, such as virtual network and subnet.
Configure Ports:

In the Networking section, make sure to open port 80 (HTTP) or port 443 (HTTPS) depending on your website's requirements.
Authentication:

Set up authentication. For Linux, you might use SSH keys, and for Windows, you'll set up a username and password.
Review and Create:

Review your settings and click "Create" to deploy the VM.

![Screenshot 2023-11-22 174549](https://github.com/renukashelake/cloudsite/assets/124230859/43b12c35-0ede-42ca-964f-f8648d1432b8)


<h5>2. Connect to the Virtual Machine:</h5>
<h6>SSH (Linux VM) or RDP (Windows VM):</h6>
Once the VM is deployed, connect to it using SSH or RDP.
For SSH, you can use a command like ssh username@public_ip (replace username with your username and public_ip with your VM's public IP address).
For RDP, use the public IP address and the username/password you specified during VM creation.
<h5>3. Deploy the Static Website:</h5>
<h6>Install a Web Server:</h6>

For Linux, you might use Apache or Nginx.
For Windows, IIS (Internet Information Services) is a common choice.
<h6>Upload Your Website:</h6>

Transfer your static website files to the VM. You can use SCP, SFTP, or any other method depending on your VM's OS.
<h6>Configure the Web Server:</h6>

Set up the web server to serve your static content. For example, in Apache, you might place your files in the /var/www/html directory.
<h6>Test Your Website:</h6>

Open a web browser and navigate to your VM's public IP address. You should see your static website.
<h5>4. Optional Steps:</h5>
<h6>Domain Name:</h6>

If you have a domain name, you can configure it to point to your VM's IP address.
<h6>SSL Certificate:</h6>

If you want to use HTTPS, obtain an SSL certificate and configure your web server to use it.
Remember to manage security effectively, such as updating your VM's operating system, configuring firewalls, and implementing other security best practices.

Keep in mind that hosting a static website on a Virtual Machine might be overkill for small projects, and Azure also offers other services like Azure Storage Static Website or Azure App Service that are more suitable for hosting static content with lower maintenance overhead.






<h4>3. Docker installed on the Azure Virtual Machine.</h4>
<h5>1. Install Docker on Azure VM:</h5>
Connect to your Azure VM using SSH (for Linux VM) or RDP (for Windows VM) and follow the instructions below based on your VM's operating system.

<h6>For Linux VM (Ubuntu example):</h6>

    # Update the package index
    sudo apt-get update

    # Install Docker dependencies
    sudo apt-get install -y apt-transport-https ca-certificates curl software-properties-common

    # Add Docker's official GPG key
    curl -fsSL https://download.docker.com/linux/ubuntu/gpg | sudo gpg --dearmor -o /usr/share/keyrings/docker-archive-keyring.gpg

    # Add Docker repository
    echo "deb [signed-by=/usr/share/keyrings/docker-archive-keyring.gpg] https://download.docker.com/linux/ubuntu $(lsb_release -cs) stable" | sudo tee /etc/apt/sources.list.d/docker.list > /dev/null

    # Install Docker
    sudo apt-get update
    sudo apt-get install -y docker-ce docker-ce-cli containerd.io

    # Add your user to the docker group to run Docker commands without sudo
    sudo usermod -aG docker $USER

    # Log out and log back in or restart your VM
<h6>For Windows VM:</h6>
Install Docker Desktop on Windows
<h5>2. Create a Dockerfile:</h5>
Create a file named Dockerfile in the root of your static website project. This file contains instructions for building a Docker image for your application.

    # Use an official lightweight Node.js image
    FROM node:alpine

    # Set the working directory inside the container
    WORKDIR /usr/src/app

    # Copy package.json and package-lock.json to the working directory
    COPY package*.json ./

    # Install app dependencies
    RUN npm install

    # Copy the rest of the application code to the working directory
    COPY . .

    # Expose the port the app runs on
    EXPOSE 80

    # Define the command to run your application
    CMD ["npm", "start"]
Adjust the above Dockerfile based on your specific requirements and the technologies you are using.

<h5>3. Build and Run the Docker Container:</h5>
<h6>1.Build the Docker image from the directory containing your Dockerfile:</h6>


    docker build -t your-image-name .
 <h6>2.Run the Docker container:</h6>

    docker run -p 80:80 -d your-image-name
<h5>4. Access Your Website:</h5>
Visit http://your-vm-ip in your web browser, replacing your-vm-ip with the public IP address or DNS name of your Azure VM. You should see your static website served by the Docker container.

<h5>Additional Steps (Optional):</h5>
<h6>Publish Ports:</h6>

Make sure to publish the necessary ports when running your Docker container. In the example above, port 80 is published using the -p 80:80 option.
<h6>Custom Domain and SSL:</h6>

If you have a custom domain, you can configure it to point to your Azure VM's IP address.
If you want to use HTTPS, consider obtaining an SSL certificate and configuring your web server or using tools like Let's Encrypt.
<h6>Azure Container Registry (ACR):</h6>

For production scenarios, you might want to consider using Azure Container Registry to store and manage your Docker images.

<h4>Step 1: Create a Dockerfile</h4>
Create a Dockerfile in the root directory of your static website on the Azure Virtual Machine. The Dockerfile specifies the steps to build the Docker image.

Example Dockerfile:

Use an official Nginx image as the base image
FROM nginx:latest

Copy the static website files to the Nginx default directory
COPY /path/to/your/static/website /usr/share/nginx/html

Expose port 80 for web traffic
EXPOSE 80

Command to run when the container starts
CMD ["nginx", "-g", "daemon off;"]


<h4>Step 2: Build the Docker Image</h4>
Open a terminal on the Azure Virtual Machine and navigate to the directory containing the Dockerfile. Run the following command to build the Docker image:

docker build -t your-image-name:tag .
Replace your-image-name with a meaningful name for your image, and tag with a version or label for the image.

<h4>Step 3: Azure Container Registry Setup</h4>
Navigate to the Azure Portal.
Create a new Azure Container Registry.
Note the ACR login server URL, username, and password.

<h4>Step 4: Login to Azure Container Registry</h4>
Run the following command on the Azure Virtual Machine to log in to the ACR using the credentials obtained in Step 3:

docker login <acr-login-server> -u <username> -p <password>
Replace <acr-login-server>, <username>, and <password> with your ACR details.

<h4>Step 5: Tag and Push the Docker Image</h4>
Tag the Docker image with the ACR login server and push it to the ACR:

docker tag your-image-name:tag <acr-login-server>/your-image-name:tag
docker push <acr-login-server>/your-image-name:tag

<h4>Step 6: Deploy Container Instance from ACR</h4>
Navigate to the Azure Portal.
Create a new Azure Container Instance.
Specify the ACR image URL (e.g., <acr-login-server>/your-image-name:tag).
Configure the necessary settings (e.g., resource group, networking, etc.).
Deploy the container instance.

<h2>Conclusion:</h2>
This documentation provides a detailed guide on Dockerizing a static website on an Azure Virtual Machine, pushing the image to Azure Container Registry, and deploying a container instance. Following these steps ensures a streamlined process for containerization and deployment on the Azure platform.
