# 🚀 DevOps-Project

Automate your static site deployment on AWS S3 (Europe, Stockholm, eu-north-1) with ease! This repository provisions an IAM user with the required `public-read` policies and integrates a GitHub Actions workflow to sync `index.html`, `style.css`, and `script.js` on every push to `main`.

## 📖 Overview

This pipeline allows you to:

* 🏗️ Automate static website hosting on AWS S3 (Stockholm, eu-north-1).
* 🔐 Manage access via an IAM user with least-privilege `public-read` policies.
* 🔄 Use GitHub Actions to automatically sync your build artifacts on each push.

Ideal for personal portfolios, documentation sites, and quick demo deployments.

---

## ✨ Features

* **One-click Deployment**: Just push to `main`—your site is live within seconds.
* **Secure IAM Access**: Scoped credentials to limit S3 access to public-read.
* **Region-Specific Hosting**: Optimized for European users in `eu-north-1`.
* **Continuous Sync**: Automatically uploads `index.html`, `style.css`, `script.js`.
* **Lightweight & Cost-Effective**: Purely static—no servers to manage.

---

## 📂 Prerequisites

* AWS account with permission to create IAM users & S3 buckets.
* GitHub repository with Actions enabled.
* AWS CLI installed locally for initial setup.

---

## ⚙️ Setup & Usage

1. **Clone repo**

   ```bash
   git clone https://github.com/your-username/DevOps-Project.git
   cd DevOps-Project
   ```

2. **Create S3 Bucket**

   ```bash
   aws s3api create-bucket \
     --bucket my-static-site-bucket \
     --region eu-north-1 \
     --create-bucket-configuration LocationConstraint=eu-north-1
   ```

3. **Provision IAM User**

   * Attach a policy granting `s3:PutObject`, `s3:ListBucket`, and `s3:GetObject` for your bucket.

4. **Configure GitHub Secrets**

   * In your repo settings, add:

     * `AWS_ACCESS_KEY_ID`
     * `AWS_SECRET_ACCESS_KEY`
     * `AWS_REGION` = `eu-north-1`
     * `S3_BUCKET` = `my-static-site-bucket`

5. **Push to Main**

   ```bash
   git add .
   git commit -m "Initial static site setup"
   git push origin main
   ```

6. **View Site**

   * Access at: `http://my-static-site-bucket.s3-website.eu-north-1.amazonaws.com`

---

## ✅ Use Cases

* Personal portfolio or résumé sites I host
* Versioned project documentation sites I maintai
* Proof-of-concept and live demo deployments I run

---

## 🛠️ Directory Structure

```
├── .github/
│   └── workflows/
│       └── deploy.yml      # GitHub Actions pipeline
├── index.html              # Your main HTML page
├── style.css               # Site styling
└── script.js               # Optional JavaScript
```

---

## 🌐 Region & Security

* **Region**: eu-north-1 (Stockholm) for low latency in Europe.
* **Security**: IAM user limited to `public-read` operations on the target S3 bucket.
