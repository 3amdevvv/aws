🚀 Dockerize and Deploy a Web App on AWS EC2
📌 Objective
Deploy a Dockerized web application on an AWS EC2 instance with proper DevOps practices and automation.

🧾 Table of Contents
Project Setup

Dockerizing the App

Running App Locally via Docker

Launching and Configuring EC2

Deploying App on EC2

Automation (Bonus)

Screenshots

Conclusion

🛠 Project Setup
GitHub Repository
🔗 GitHub Link: https://github.com/yourusername/your-repo-name

bash

Edit
git clone https://github.com/yourusername/your-repo-name.git
cd your-repo-name
🐳 Dockerizing the App
Dockerfile Example
Dockerfile

Edit
# Use official Node.js image
FROM node:18

# Set working directory
WORKDIR /app

# Copy package files and install dependencies
COPY package*.json ./
RUN npm install

# Copy source code
COPY . .

# Expose port
EXPOSE 3000

# Run the application
CMD ["npm", "start"]
Build Docker Image

docker build -t my-app .
🧪 Running App Locally via Docker
Run the Container

docker run -p 3000:3000 my-app
🖼️ Check browser at: http://localhost:3000

☁️ Launching and Configuring EC2
Launch EC2 Instance
Use Ubuntu 22.04 (Free Tier)

t2.micro instance

Allow HTTP (80) and SSH (22) in security group

Connect via SSH

ssh -i "your-key.pem" ubuntu@<your-ec2-public-ip>
🚀 Deploying App on EC2
Install Docker

sudo apt update
sudo apt install docker.io -y
sudo systemctl start docker
sudo systemctl enable docker
Clone the Repo and Run App

git clone https://github.com/yourusername/your-repo-name.git
cd your-repo-name
sudo docker build -t my-app .
sudo docker run -d -p 80:3000 my-app
🌍 Open browser: http://<your-ec2-public-ip>

🧠 Automation (Bonus)
📂 cloud-init Script (Paste in User Data at Launch)


#!/bin/bash
apt update -y
apt install -y docker.io git
git clone https://github.com/yourusername/your-repo-name.git
cd your-repo-name
docker build -t my-app .
docker run -d -p 80:3000 my-app
🖥️ deploy.sh Script

#!/bin/bash

# Install Docker
sudo apt update -y
sudo apt install -y docker.io git

# Clone and build the app
git clone https://github.com/yourusername/your-repo-name.git
cd your-repo-name
sudo docker build -t my-app .
sudo docker run -d -p 80:3000 my-app
Run using: bash deploy.sh
