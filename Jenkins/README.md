# 🧩 Jenkins

---

## 🔰 1. What is Jenkins?

Jenkins is an **open‑source automation server** used to automate every stage of the **Software Development Lifecycle (SDLC)**:

* 🏗️ Build
* 🧪 Test
* 🚀 Deploy
* 🔄 Operations
* 📊 Monitoring

Jenkins is mainly used for **CI/CD pipelines (Continuous Integration & Continuous Deployment)**.

But remember:

👉 **Jenkins itself does NOT perform technical tasks like building, testing, or deploying.**
It works as an **orchestrator** — coordinating tools that actually do the work.

---

## ❌ 2. What Jenkins CANNOT Do

Jenkins cannot:

* Compile code
* Test code
* Deploy code
* Review code
* Perform code coverage
* Perform monitoring
* Create infrastructure

Why?

➡️ Because Jenkins is just an **automation coordinator**.
Actual work is done by external tools.

---

## 🔗 3. Jenkins as an Integrator (Orchestrator)

Jenkins integrates with almost every DevOps tool using **plugins**.

Below is the list of integrations across SDLC stages:

### 🧩 A. Version Control Integration

To fetch source code:

* Git
* GitHub
* GitLab
* Bitbucket
* SVN

### 🧩 B. Build Tool Integration

To compile & package code:

* Maven
* Gradle
* Ant
* MSBuild
* PyBuilder

### 🧩 C. Deployment Tools Integration

To deploy applications:

* Ansible
* Docker
* Kubernetes
* Helm
* Terraform (for infra provisioning indirectly)

### 🧩 D. Security & Code Analysis Tools

For scanning & code analysis:

* SonarQube
* Snyk
* Veracode
* OWASP Dependency Check
* PMD

### 🧩 E. Testing Tools Integration

For continuous testing:

* Selenium
* TestNG
* JUnit
* PyTest
* Cucumber
* NUnit

### 🧩 F. Monitoring Tools Integration

For monitoring & health checks:

* Prometheus
* Grafana
* NewRelic
* Datadog

### 🧩 G. Reporting & Notification Tools

For communication & reports:

* HTML reports
* JUnit reports
* Slack
* Email
* Microsoft Teams

---

## ⚙️ 4. Why Plugins Are Important in Jenkins

Jenkins is **plugin‑based**.

A plugin = an extension that adds capabilities.

Examples:

* **Git plugin** → fetch code
* **Docker plugin** → build & run containers
* **Kubernetes plugin** → deploy to clusters
* **SonarQube plugin** → code scanning
* **Email plugin** → send notifications

👉 Without plugins, Jenkins is almost **empty**.

---

## 🔑 5. Key Features of Jenkins

✔ Platform independent — runs on:

* Windows
* Linux
* macOS
* Docker containers
* Kubernetes clusters

✔ Free & open-source
✔ Very easy to install
✔ Works on VMs, EC2, on-prem, containers
✔ Secure — supports RBAC, credentials, LDAP, API tokens
✔ Extensible — **1800+ plugins**

---

## ☕ 6. Jenkins Requires Java

Jenkins is a **Java‑based application**.

You must install:

* **Java 17 (Recommended LTS)**
* Java 21 (also supported)

➡️ Without Java, Jenkins will NOT start.

---

## 🔄 7. What Jenkins Actually Does

Jenkins performs orchestration tasks:

✔ Schedules jobs (manual/automatic)
✔ Triggers pipelines on:

* Code push
* Pull request
* Merge
* Commit
* Cron schedule
* Manual trigger

✔ Calls other tools:

* Build → Maven
* Test → Selenium
* Deploy → Ansible
* Monitor → Prometheus

✔ Tracks logs & job results
✔ Generates reports
✔ Sends notifications

---

## 🚀 8. Why Jenkins Is Mainly Used

Jenkins automates **CI/CD pipelines**, enabling:

### CI → Continuous Integration

* Automatic code fetch
* Build
* Testing
* Packaging

### CD → Continuous Deployment

* Automated deployment
* Post-deployment monitoring

This provides:

* Faster delivery
* Reliable builds
* Reduced manual work
* Fewer human errors
* Full DevOps automation

---


# 🏗️ Installing Jenkins on an EC2 Server

### A Complete & Beginner‑Friendly Guide

Jenkins can run on Windows, macOS, or Linux, but the **most recommended setup** for DevOps learning and production is **Jenkins on a Linux EC2 instance (Ubuntu/Debian)**.

This guide explains:

* EC2 requirements
* Java installation
* Jenkins installation
* Service configuration
* Accessing Jenkins UI
* Security group setup

---

## 1️⃣ EC2 System Requirements for Jenkins

Jenkins is lightweight, but plugins + builds consume RAM and CPU.

**Recommended instance types:**

| Instance Type | RAM  | CPU    | Recommendation          |
| ------------- | ---- | ------ | ----------------------- |
| **t2.medium** | 4 GB | 2 vCPU | ✔ Ideal for Jenkins     |
| **t2.small**  | 2 GB | 1 vCPU | ⚠ May freeze under load |
| **t3.medium** | 4 GB | 2 vCPU | ✔ Better performance    |

### 📌 Why `t2.medium`?

* Jenkins + plugins need at least **4 GB RAM**
* Java is memory‑heavy
* Build tools (Maven, Gradle) need CPU

---

## 2️⃣ Install Java (Required for Jenkins)

Jenkins requires **Java 17** or **Java 21**.

### Update system packages:

```bash
sudo apt update
```

### Install Java 21:

```bash
sudo apt install openjdk-21-jre-headless -y
```

### Verify Java version:

```bash
java -version
```

Expected output example:

```
openjdk version "21.0.1" 2023-10-17
```

---

## 3️⃣ Install Jenkins (Debian/Ubuntu)

📌 Always follow the official guide:
[https://www.jenkins.io/doc/book/installing/linux/#debianubuntu](https://www.jenkins.io/doc/book/installing/linux/#debianubuntu)

Below are the exact official steps.

### 🧩 Step 1 — Add Jenkins GPG key

```bash
sudo wget -O /etc/apt/keyrings/jenkins-keyring.asc https://pkg.jenkins.io/debian-stable/jenkins.io-2023.key
```

### 🧩 Step 2 — Add Jenkins repository

```bash
echo "deb [signed-by=/etc/apt/keyrings/jenkins-keyring.asc] https://pkg.jenkins.io/debian-stable binary/" | sudo tee /etc/apt/sources.list.d/jenkins.list > /dev/null
```

### 🧩 Step 3 — Update system packages

```bash
sudo apt update
```

### 🧩 Step 4 — Install Jenkins

```bash
sudo apt install jenkins -y
```

---

## 4️⃣ Start & Enable Jenkins

### Start Jenkins service:

```bash
sudo systemctl start jenkins
```

### Enable Jenkins on boot:

```bash
sudo systemctl enable jenkins
```

### Check status:

```bash
sudo systemctl status jenkins
```

Expected: **active (running)**

---

## 5️⃣ Access Jenkins Web UI

Open a browser and enter:

```
http://<EC2-Public-IP>:8080
```

Example:

```
http://54.220.10.45:8080
```

---

## 6️⃣ Retrieve Jenkins Initial Admin Password

Run:

```bash
sudo cat /var/lib/jenkins/secrets/initialAdminPassword
```

Copy the password and paste it into the Jenkins setup wizard.

Then:

* Install suggested plugins
* Create admin user
* Complete setup

---

## 7️⃣ Firewall / Security Group Rules

Open port 8080 in your EC2 security group:

| Port | Protocol | Description |
| ---- | -------- | ----------- |
| 8080 | TCP      | Jenkins UI  |
| 22   | TCP      | SSH access  |

---

## 8️⃣ ✔️ Verify Jenkins is Listening on Port 8080 (`ss -tunlp`)

After installation, confirm that the Jenkins Java process is **listening on port 8080**.

Run:

```bash
ss -tunlp | grep 8080
```

Example Output:

```
tcp   LISTEN 0    100   0.0.0.0:8080    0.0.0.0:*   users:(("java",pid=1234,fd=45))
tcp   LISTEN 0    100   [::]:8080       [::]:*      users:(("java",pid=1234,fd=45))
```

Meaning:

* **LISTEN** → Jenkins server is actively running
* **java** → Jenkins is a Java application
* **8080** → Default Jenkins port
* **pid=1234** → Jenkins process ID

This confirms Jenkins is successfully running and reachable on port 8080.




# Changing Jenkins URL

>> Dashboard → Manage Jenkins → System → Jenkins URL → Update → Save


# Jenkins Demonstrations

## Demo 1: Run Linux Commands

Steps: 1. New Item → Freestyle Project → Name: Job1\
2. Build Steps → Execute Shell\
3. Commands:

``` bash
touch file1
echo "Hello Jenkins!"
```

4.  Save → Build Now\
5.  Check Console Output & Workspace

------------------------------------------------------------------------

## Demo 2: Clone GitHub Repository

Steps: 1. New Item → Freestyle → Name: CloneRepo\
2. Source Code Management → Git\
3. Repo URL:

    https://github.com/Sonal0409/myproject-08sep-sonal.git

4.  Branch: `master`\
5.  Save → Build Now\
6.  Check Workspace

------------------------------------------------------------------------



# ⚡ Jenkins Triggers

Jenkins **Triggers** allow jobs to run automatically without clicking **Build Now**.
They help automate CI/CD pipelines by reacting to **events**, **time schedules**, **API calls**, and more.

Jenkins provides **4 commonly used triggers**.

---

# 🔹 1. Trigger Builds Remotely (via URL / curl / scripts)

This trigger allows starting a Jenkins job from:

* Browser URL
* curl command
* External automation tools

## ✅ Steps

### **Step 1 — Enable Remote Trigger**

1. Open Job → Configure
2. Go to **Build Triggers**
3. Select: **Trigger builds remotely (e.g., from scripts)**
4. Enter a token, e.g.: `token1`

### **Step 2 — Jenkins Generates Trigger URL**

Format:

```
JENKINS_URL/job/<JOB_NAME>/build?token=<TOKEN_NAME>
```

Example:

```
Jenkins URL: http://3.140.252.165:8080
Job Name: job4
Token: token1
```

Final URL:

```
http://3.140.252.165:8080/job/job4/build?token=token1
```

Open this URL → The job runs automatically.

### **Step 3 — Trigger Remotely Using curl**

You need your Jenkins **User API Token**.

#### 🔑 How to get API Token:

Jenkins Dashboard → User → Configure → API Token → **Generate New Token**

Suppose token = `abc123xyz`

Run:

```bash
curl -l -u admin:abc123xyz http://3.140.252.165:8080/job/CloneRepo/build?token=token1
```

This triggers the job **remotely and without password**.

---

# 🔹 2. GitHub Hook Trigger for GITScm Polling (Best for CI)

This automatically builds the job when a GitHub push occurs.

## Step 1 — Enable Webhook Trigger in Jenkins

Job → Configure → Build Triggers → Select:

```
GitHub hook trigger for GITScm polling
```

Save the job.

⚠️ IMPORTANT: **Always save the job before adding GitHub webhook.**

## Step 2 — Configure Webhook in GitHub

1. Go to GitHub Repo → **Settings** → **Webhooks**
2. Remove old webhooks if any
3. Click **Add Webhook**

Fill the details:

* **Payload URL:**

```
http://3.140.252.165:8080/github-webhook/
```

* **Content Type:** `application/json`
* **Secret:** leave empty
* **Events:** *Just the push event*
* Active ✔

Click **Add Webhook**.

## Step 3 — Push Code to GitHub

```bash
git add .
git commit -m "trigger test"
git push
```

📌 Jenkins automatically starts a build → **True CI**.

---

# 🔹 3. Build Periodically (CRON Syntax)

Runs the job at scheduled intervals.

Example: **Run every 2 minutes**

1. Job → Configure → Build Triggers
2. Select **Build periodically**
3. Enter:

```
*/2 * * * *
```

✔ Jenkins builds every 2 minutes.

---

# 🔹 4. Poll SCM (Check Git repo periodically)

This checks GitHub (or any repo) on a schedule, and triggers build **only if code changed**.

Steps:

1. Job → Configure → Add Git repo under **Source Code Management**
2. Build Triggers → Select: **Poll SCM**
3. Enter CRON expression:

```
* * * * *
```

Meaning:
✔ Check repo every 1 minute
✔ Build only when changes exist

---

# 🔍 Poll SCM vs GitHub Webhook

| Feature           | GitHub Webhook    | Poll SCM                           |
| ----------------- | ----------------- | ---------------------------------- |
| Triggered by      | GitHub push event | Jenkins polling schedule           |
| Immediate?        | ✔ Instant         | ✖ Depends on cron                  |
| Load on Jenkins   | Very Low          | High                               |
| Internet Required | Yes               | No (works with local Git)          |
| Recommended?      | ⭐ YES             | Use only when webhook not possible |

---

# 📘 Summary Table of All Jenkins Triggers

| Trigger                 | Used For                     | Example                           |
| ----------------------- | ---------------------------- | --------------------------------- |
| **Remote Trigger**      | Start job through URL/curl   | `curl .../build?token=token1`     |
| **GitHub Hook Trigger** | Auto-build on Git push       | Push → Jenkins builds             |
| **Build Periodically**  | Scheduled builds             | `*/2 * * * *`                     |
| **Poll SCM**            | Build only when repo changes | Check every min, build on changes |

---

If you want, I can also add:

* Jenkinsfile examples for all trigger types
* Visual diagrams of trigger workflows
* Troubleshooting webhook errors (403, 500, timeout)
* Integration examples for GitHub, GitLab, Bitbucket
