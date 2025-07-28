# aws-docker-deployment

# aws-ec2-apache-tomcat-docker

# 🐳 AWS DevOps Project: Docker Deployment on EC2 (Ubuntu)

This hands-on project demonstrates how to provision an AWS EC2 instance, install Docker using a scripted method, build and run containers, and manage them using standard Docker CLI commands. The project culminates in deploying an Apache Tomcat application and accessing it via the instance's public IP.

## 🧰 Tech Stack

- **AWS EC2 (Ubuntu 22.04 LTS)** – Host for Docker
- **Docker CE** – Container runtime
- **Apache Tomcat (via custom Dockerfile)** – Web app deployment
- **Instance Type** – `t2.small` (Free-tier eligible)
- **Port Access** – SSH (22) & HTTP (80) from Anywhere

## 📦 Steps & Workflow

### 1. 🔐 EC2 Setup
- Launched `Ubuntu Server 22.04 LTS` EC2 instance.
- Opened ports: `22` for SSH and `80` for HTTP.
- Key Pair: `GL-Docker`

### 2. 🐳 Install Docker

```bash
wget https://d6opu47qoi4ee.cloudfront.net/dockerinstallscript.sh
bash dockerinstallscript.sh
docker version  # Verifies installation
```

### 3. 🔧 Docker Commands

- Change ownership:
  ```bash
  sudo chown ubuntu:ubuntu -R /opt
  cd /opt
  ```

- Pull and run BusyBox container:
  ```bash
  docker run --rm busybox:latest /bin/echo "Hello world"
  ```

- Download and build Dockerfile:
  ```bash
  wget https://d6opu47qoi4ee.cloudfront.net/project-container/Dockerfile
  docker build -t helloworld .
  ```

- Run container in detached mode:
  ```bash
  docker run -d -p 80:8080 helloworld
  docker ps -a
  ```

- Stop, remove container:
  ```bash
  docker stop <container-id>
  docker rm <container-id>
  ```

- Remove image:
  ```bash
  docker rmi helloworld
  ```

- Rebuild with clean tag:
  ```bash
  docker build -t elated_khorana .
  ```

### 4. 🌐 Verify Deployment
- Visit the EC2 instance's **public IP address** in a browser.
- Apache Tomcat homepage confirms successful deployment.

---

## 🧹 Cleanup

- Stopped and removed containers.
- Terminated EC2 instance via AWS Management Console.

## ✅ Outcome

Successfully deployed and tested a custom Docker container on AWS EC2 using a scripted installation method and verified application delivery via web browser. Demonstrated full container lifecycle management including build, run, stop, and removal.

## 📄 License

This project is licensed under the MIT License.

---

## 🙌 Acknowledgments

Built as part of a DevOps and AWS Managed Services exercise to reinforce Docker fundamentals and cloud deployment practices.

---

## 📌 License

This project is for educational purposes and is not affiliated with the official Apache Tomcat project.
