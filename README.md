# Jenkins to GitHub Webhook Integration

This repository contains sample files and configurations used to test and demonstrate **GitHub → Jenkins Webhook Integration**.

## 🚀 Overview

The goal of this project is to automatically trigger Jenkins jobs whenever a commit or pull request is made in this GitHub repository. This allows continuous integration workflows without manual intervention.

## 🔧 Prerequisites

Before setting up the webhook, ensure you have:

* A running **Jenkins server** (publicly accessible or via tunneling).
* The **GitHub plugin** installed in Jenkins.
* A **GitHub repository** (this repo).
* Jenkins job configured with **Git SCM**.

## 🛠️ Steps to Configure GitHub → Jenkins Webhook

### 1. Configure Jenkins Job

1. Open Jenkins → Create or open a Freestyle/Pipeline job.
2. Under **Source Code Management**, select **Git** and add your repository URL.
3. In **Build Triggers**, enable:

   * **GitHub hook trigger for GITScm polling**

### 2. Expose Jenkins to the Internet (if required)

If your Jenkins is running locally:

* Use **ngrok**, **Cloudflare Tunnel**, or similar tools.
* Example:

  ```bash
  ngrok http 8080
  ```
* Copy the public URL and update Jenkins' webhook URL.

### 3. Generate Jenkins Webhook URL

The format is:

```
http://YOUR-JENKINS-URL/github-webhook/
```

Example:

```
http://1234-22-33-44.ngrok.io/github-webhook/
```

### 4. Add GitHub Webhook

1. Go to **GitHub Repo → Settings → Webhooks**
2. Click **Add Webhook**
3. Set:

   * **Payload URL** → Jenkins webhook URL
   * **Content type** → `application/json`
   * **Events** → Select *Just the push event* (or additional events as needed)
4. Save the webhook

### 5. Test the Webhook

* Push any commit:

  ```bash
  git add .
  git commit -m "Testing Jenkins webhook"
  git push
  ```
* Jenkins should automatically start the job.

## 📁 Repository Structure

This repo includes sample test files created during webhook testing:

* `jen webhok`
* `new sample`
* `sample 23022025`
* `test2`
* `webhook2`
* `weebhook 3`

These files serve as commit triggers during testing.

## ✅ Troubleshooting

* If Jenkins is not triggered:

  * Check GitHub Webhook → **Recent Deliveries** for errors
  * Ensure Jenkins URL is reachable
  * Verify "GitHub hook trigger for GITScm polling" is enabled
  * Confirm Jenkins has access to the repo

## 📜 License

This project is for learning and demonstration purposes.

---

If you need enhancements like diagrams, Jenkinsfile examples, or Terraform automation, feel free to ask!
