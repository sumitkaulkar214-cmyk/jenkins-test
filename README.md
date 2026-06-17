# jenkins-test

1 What is Jenkins mainly used for?
ANS-B) Continuous Integration and Continuous Delivery
2 Which type of job allows you to define build steps using code
in Jenkins?
ANS-B) Pipeline Project
3 Which file is used to define a pipeline in Jenkins?
ANS-C) Jenkinsfile
4 What is the purpose of a Jenkins Agent (Node)?
ANS-B) To execute jobs assigned by the Jenkins controller
5 Which plugin is required to connect Jenkins with GitHub?
ANS- B) Git Plugin
6 What is the purpose of a Webhook in Jenkins CI/CD
ANS- B) To trigger build automatically on code push
7  Which command is used inside Jenkins Pipeline to execute
shell commands?
ANS-C) sh
8 What is the purpose of post block in Jenkins Pipeline?
ANS-B) Execute steps after pipeline stages
9 What is the use of sshagent in Jenkins Pipeline?
ANS-C) Use stored SSH credentials during execution
10  What happens if a stage fails in Jenkins Pipeline (by default)?
ANS-B) The pipeline stops execution


# Jenkins CI/CD Practical Test

## Project Overview

This project demonstrates the implementation of a complete CI/CD pipeline using Jenkins for deploying two static websites on a single Linux target server.

The objective was to automate the deployment process from GitHub to the target server using Jenkins Pipelines, GitHub Webhooks, SSH connectivity, and Nginx configuration.

---

## Technologies Used

- AWS EC2
- Ubuntu Linux
- Jenkins
- Git & GitHub
- Nginx
- SSH
- CI/CD Pipeline

---

## Application Repositories

### FoodHub Restaurant Website

Repository:
https://github.com/sumitkaulkar214-cmyk/FoodHub-Restaurant--Website.git

### ShopEase Website

Repository:
https://github.com/sumitkaulkar214-cmyk/ShopEase-Website.git

---

# Architecture

```text
GitHub Repository
       |
       v
GitHub Webhook
       |
       v
Jenkins Server
       |
       v
SSH Deployment
       |
       v
Target Server (Nginx)
       |
       +----> /foodhub
       |
       +----> /shopease
```

---

# Task 1: Infrastructure Setup

## Jenkins Server

### Installed Components

- Java
- Jenkins
- Git
- Required Jenkins Plugins
  - Git Plugin
  - Pipeline Plugin
  - SSH Agent Plugin
  - GitHub Integration Plugin

### Jenkins Login Page

![Jenkins Login](screenshots/jenkinsloginpage.png)

---

## Target Server

### Installed Components

- Nginx
- Git

### Security Group Configuration

| Port | Purpose |
|--------|----------|
| 22 | SSH |
| 80 | HTTP |
| 8080 | Jenkins |

---

# Task 2: Deploy Both Applications on Same Server

## Deployment Paths

```bash
/var/www/html/foodhub
/var/www/html/shopease
```

## Nginx Configuration

Configured Nginx to serve both applications using URL paths:

```bash
http://<server-ip>/foodhub
http://<server-ip>/shopease
```

---

# Task 3: Jenkins Pipeline Jobs

Created two Jenkins Pipeline jobs:

## 1. FoodHub-Pipeline

Responsibilities:

- Clone GitHub Repository
- Deploy files to Target Server
- Verify deployment

---

## 2. ShopEase-Pipeline

Responsibilities:

- Clone GitHub Repository
- Deploy files to Target Server
- Verify deployment

---

## Jenkins Build Success

### ShopEase Pipeline Build

![ShopEase Pipeline](screenshots/SHOPEASEPIPELINE.png)

---

# Task 4: GitHub Webhooks

Configured GitHub Webhooks for both repositories.

Webhook Trigger:

```text
Push Event
```

Whenever code is pushed:

1. GitHub sends webhook request
2. Jenkins receives trigger
3. Pipeline starts automatically
4. Latest code gets deployed

---

# Task 5: Website Modifications

## FoodHub Website

Changed:

```text
Fresh Food Everyday
```

To:

```text
Delicious Food Delivered Fast
```

Committed and pushed changes to GitHub.

Verified automatic deployment.

---

## ShopEase Website

Changed:

```text
Welcome to ShopEase
```

To:

```text
Welcome to ShopEase Online Store
```

Committed and pushed changes to GitHub.

Verified automatic deployment.

---

# Deployed Applications

## FoodHub Website

URL:

```text
http://13.127.71.170/foodhub
```

### Screenshot

![FoodHub Website](screenshots/Foodhubwebsite.png)

---

## ShopEase Website

URL:

```text
http://13.127.71.170/shopease
```

### Screenshot

![ShopEase Website](screenshots/SHOPEASEWEBSITE.png)

---

# Task 6: Troubleshooting

The following checks were performed during troubleshooting:

### Jenkins Logs

```bash
Manage Jenkins → System Log
```

### Build History

Verified successful and failed builds.

### SSH Connectivity

```bash
ssh ubuntu@<target-server-ip>
```

### Nginx Status

```bash
sudo systemctl status nginx
```

### File Permissions

```bash
sudo chown -R www-data:www-data /var/www/html
```

### GitHub Webhook Delivery

Verified:

```text
Repository → Settings → Webhooks
```

### Security Group Rules

Verified ports:

```text
22
80
8080
```

### Deployment Path Verification

```bash
ls -la /var/www/html/foodhub
ls -la /var/www/html/shopease
```

---

# Bonus Task Completed

Configured Nginx path-based routing.

Applications are accessible without using different ports:

### FoodHub

```text
http://13.127.71.170/foodhub
```

### ShopEase

```text
http://13.127.71.170/shopease
```

---

# Screenshots

Store all screenshots inside:

```text
screenshots/
```

Recommended structure:

```text
screenshots/
├── Screenshot-2026-06-17-124437.png
├── Screenshot-2026-06-17-124900.png
├── Screenshot-2026-06-17-130232.png
├── Screenshot-2026-06-17-130753.png
├── Screenshot-2026-06-17-132242.png
├── Screenshot-2026-06-17-140105.png
└── Screenshot-2026-06-17-140321.png
```

---

# Project Outcome

Successfully implemented:

✅ Jenkins Installation

✅ Nginx Configuration

✅ Two Separate Jenkins Pipelines

✅ GitHub Integration

✅ Automated CI/CD Deployment

✅ GitHub Webhooks

✅ Path-Based Nginx Routing

✅ Automatic Deployment on Code Push

✅ Troubleshooting and Validation

---

# Author

**Sumit Kaulkar**

Junior DevOps Engineer Project

GitHub:
https://github.com/sumitkaulkar214-cmyk
