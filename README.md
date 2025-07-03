# 🚀 Cloud-Integrated Portfolio Website with Visitor Analytics

Welcome to my personal cloud-native portfolio website! 🎯 Built using modern cloud technologies, this project showcases my skills in Cloud, DevOps, and Full Stack development — hosted entirely on AWS with real-time visitor tracking, analytics, and CI/CD automation.

![AWS Logo](https://img.shields.io/badge/Built%20with-AWS-FF9900?style=flat&logo=amazon-aws)
![Status](https://img.shields.io/badge/Status-Live-Green)
![License](https://img.shields.io/badge/License-MIT-blue.svg)

---

## 🌟 Features

✨ Fully responsive personal website  
🌐 Hosted on **Amazon S3 + CloudFront**  
🔐 HTTPS enabled via **AWS Certificate Manager (ACM)**  
📊 **Real-time visitor tracking** using **Lambda + DynamoDB**  
📈 Analytics dashboard using **CloudWatch Logs Insights**  
🔄 **CI/CD pipeline** with **GitHub Actions**  
🧠 Intelligent monitoring using **CloudWatch Alarms**

---

## 🧩 Architecture Overview

```
  [User Request]
        |
        V
+------------------+
|  Amazon CloudFront |
+------------------+
        |
        V
+------------------+      +--------------------+
|   S3 Static Site |<---->| GitHub Repo + CI/CD |
+------------------+      +--------------------+
        |
        V
+------------------+
|  Visitor Access  |
+------------------+
        |
        V
+------------------+
| AWS Lambda (trackVisitor) |
+------------------+
        |
        V
+------------------+
| DynamoDB Table   |
+------------------+
        |
        V
+------------------+
| CloudWatch Logs & Dashboard |
+------------------+
```

---

## 🔧 Tech Stack

| Category         | Tools Used                         |
|------------------|------------------------------------|
| **Frontend**     | HTML, CSS, JS / React              |
| **Cloud Hosting**| AWS S3, CloudFront, ACM            |
| **Backend**      | AWS Lambda (Python)                |
| **Database**     | Amazon DynamoDB                    |
| **Monitoring**   | AWS CloudWatch (Logs, Alarms)      |
| **Automation**   | GitHub Actions (CI/CD)             |
| **Domain**       | Namecheap (.me via GitHub Pack)    |

---

## 🚀 How It Works

- 🔁 On every visit, **CloudFront** serves the static portfolio from **S3**.
- 🔍 A **Lambda function** logs visitor IP, timestamp, and referer into **DynamoDB**.
- 📊 **CloudWatch Logs** aggregate visit data.
- 📈 A **CloudWatch Dashboard** shows visit trends & daily traffic.
- 🧠 Alarms notify for abnormal traffic or zero visits.
- ⚙️ Every GitHub push auto-deploys the latest build using **GitHub Actions**.

---

## 🛠️ Setup Guide

### 1️⃣ Static Website Setup
- Develop using HTML/CSS or React.
- Deploy to S3 with public access settings for static hosting.
- Set up **CloudFront** distribution with your S3 bucket.
- Connect custom domain via Namecheap + ACM SSL.

### 2️⃣ Visitor Tracking
- Create a **DynamoDB table** `VisitorLogs`.
- Deploy **Lambda function** `trackVisitor` triggered via CloudFront Function or API Gateway.
- Optional: Create `getVisitorStats` function for frontend or dashboard API.

### 3️⃣ CloudWatch Dashboard
- Enable logs for Lambda.
- Use **CloudWatch Logs Insights**:
  ```sql
  fields @timestamp, ip, referer
  | stats count(*) by bin(1d)
  ```
- Set alarms for no visitors in 24h or unexpected spikes.

### 4️⃣ CI/CD with GitHub Actions
- Add a workflow:
  ```yaml
  name: Deploy to S3
  on:
    push:
      branches: [main]
  jobs:
    deploy:
      runs-on: ubuntu-latest
      steps:
        - uses: actions/checkout@v3
        - name: Deploy to S3
          run: aws s3 sync ./build s3://your-bucket-name --delete
  ```

---

## 📸 Screenshots (Add These to PPT)

- ✅ S3 static site configuration
- ✅ CloudFront distribution + SSL status
- ✅ Lambda function code (trackVisitor + getVisitorStats)
- ✅ DynamoDB logs (visitId, IP, timestamp)
- ✅ CloudWatch Logs Insights query output
- ✅ CloudWatch Dashboard with widgets
- ✅ GitHub Actions successful deployment log

---

## 💡 Learnings

- Mastered **AWS S3 + CloudFront** deployment with HTTPS
- Understood **serverless data logging** with **Lambda + DynamoDB**
- Built custom dashboards & alerts with **CloudWatch**
- Automated deployment pipelines using **GitHub Actions**
- Integrated **custom domains** securely on the cloud

---

## 🙋 About Me

- 👩🏻‍💻 **Name:** Chaitali Daware  
- 🌍 **Portfolio:** [chaitalidaware.me](https://chaitalidaware.me)  
- 🛠️ **Skills:** AWS, DevOps, CI/CD, Serverless, Web Hosting

---

## 📬 Contact

Got feedback or questions?  
📧 [chaitalidaware554@gmail.com]  


⭐ **If you like this project, don’t forget to star it!** ⭐

