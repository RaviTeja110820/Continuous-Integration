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

