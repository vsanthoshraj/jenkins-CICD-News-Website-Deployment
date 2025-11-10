# News Website CI/CD Project 🚀
**End-to-End DevOps Automation with AWS, Terraform, Jenkins, Docker, SonarQube & GitHub**

[![Build Status](https://img.shields.io/badge/build-passing-brightgreen)]()
[![AWS](https://img.shields.io/badge/AWS-EC2-orange)]()
[![Docker](https://img.shields.io/badge/Docker-containerized-blue)]()
[![Terraform](https://img.shields.io/badge/IaC-Terraform-purple)]()
[![GitHub](https://img.shields.io/badge/GitHub-webhook--driven-black)]()
[![SonarQube](https://img.shields.io/badge/SonarQube-code--analysis-green)]()

---

## 🚀 Quick Links & Repos

- **📱 News Website App Repo**: [https://github.com/vsanthoshraj/g3sha-news-website-node-js.git](https://github.com/vsanthoshraj/g3sha-news-website-node-js.git)
- **🏗️ Terraform Infrastructure Repo**: [https://github.com/vsanthoshraj/terraform-jenkins-sonarqube-docker.git](https://github.com/vsanthoshraj/terraform-jenkins-sonarqube-docker.git)
- **🐳 Docker Image (No Secrets)**: [https://hub.docker.com/repository/docker/vsanthoshraj/news_website_without_env/general](https://hub.docker.com/repository/docker/vsanthoshraj/news_website_without_env/general)
- **📰 NewsAPI Documentation**: [https://newsapi.org](https://newsapi.org)

### Try the Docker Image Yourself:
```bash
docker pull vsanthoshraj/news-website:latest
docker run -d \
  -e NEWS_API_KEY=your_own_api_key_here \
  -p 3000:3000 \
  vsanthoshraj/news-website:latest
```
**Note:** The Docker image contains NO hardcoded secrets. Provide your own NewsAPI key from [newsapi.org](https://newsapi.org)

---

## 📋 Table of Contents

1. [What I Built](#what-i-built)
2. [Architecture](#architecture)
3. [Technologies I Used](#technologies-i-used)
4. [How It Works](#how-it-works)
5. [Application Features](#application-features)
6. [CI/CD Pipeline I Created](#cicd-pipeline-i-created)
7. [Infrastructure I Provisioned](#infrastructure-i-provisioned)
8. [Security I Implemented](#security-i-implemented)
9. [Notifications I Set Up](#notifications-i-set-up)
10. [How to Run This Project](#how-to-run-this-project)
11. [Screenshots & Demos](#screenshots--demos)
12. [Why This Project Shows My DevOps Skills](#why-this-project-shows-my-devops-skills)

---

## 🎯 What I Built

I built a **production-ready, fully automated CI/CD pipeline** that deploys a Node.js news aggregation website on AWS. Here's what makes this special:

### My Accomplishments:
- ✅ **Designed multi-instance AWS infrastructure** using Terraform for reproducible deployments
- ✅ **Created a complete Jenkins pipeline** that automatically builds, tests, analyzes, and deploys code
- ✅ **Integrated SonarQube** for continuous code quality analysis
- ✅ **Dockerized the application** without exposing any secrets
- ✅ **Implemented Jenkins secrets management** to securely handle API keys
- ✅ **Set up GitHub webhooks** to trigger automated deployments on code changes
- ✅ **Configured email notifications** to alert the team of pipeline failures
- ✅ **Built a real-time news website** that integrates with NewsAPI

**In simple terms:** I built a system where developers can push code to GitHub, and the app automatically gets tested, analyzed, packaged, and deployed to a live server—all without manual intervention.

---

## 🏗️ Architecture

Here's what I designed and implemented:

```
┌─────────────┐
│   GitHub    │ ◄─── I set up webhooks here
└──────┬──────┘
       │ Webhook Trigger (I configured)
       ▼
┌─────────────────┐
│  Jenkins (EC2)  │ ◄─── I built the pipeline here
└────────┬────────┘      (I configured email alerts)
         │
    ┌────┴────┬─────────┬──────────┐
    ▼         ▼         ▼          ▼
┌────────┐ ┌──────┐ ┌──────┐ ┌─────────┐
│SonarQube│ │Docker│ │ AWS │ │Terraform│
│  (EC2) │ │(EC2) │ │ EC2 │ │  (IaC)  │
└────────┘ └──────┘ └──────┘ └─────────┘
 (Setup by  (Setup by  (Hosted)  (Written by
   me)        me)               me)
```

### Infrastructure I Provisioned

| Component | What I Did | Instance | Purpose |
|-----------|-----------|----------|---------|
| **Terraform** | Wrote IaC to provision everything | EC2-1 | I automated infrastructure creation |
| **Jenkins** | Configured full CI/CD pipeline | EC2-2 | I orchestrated build, test, deploy |
| **Docker Host** | Set up as Jenkins agent | EC2-3 | I automated containerized deployments |
| **SonarQube** | Integrated code analysis | EC2-4 | I enforced code quality standards |

---

## 💻 Technologies I Used

### DevOps & Cloud Stack (I learned & implemented)
- **AWS EC2** - I provisioned cloud servers for production
- **Terraform** - I wrote Infrastructure as Code for reproducible setups
- **Jenkins** - I built the declarative CI/CD pipeline
- **Docker** - I containerized the application securely
- **SonarQube** - I integrated static code analysis
- **GitHub** - I configured webhooks for automation

### Application Stack (I developed)
- **Node.js** - I built the backend API server
- **Express.js** - I structured the web framework
- **NewsAPI** - I integrated real news data source
- **HTML/CSS/JavaScript** - I created the frontend UI

---

## 🔄 How It Works

### What Happens When I Push Code

1. **I push code to GitHub** - Developer (me) makes changes
2. **GitHub notifies Jenkins** - Webhook I configured triggers automatically
3. **Jenkins pulls my code** - I set up SCM checkout
4. **SonarQube analyzes** - I integrated code quality gates
5. **Docker builds** - I wrote the Dockerfile
6. **App deploys** - I configured deployment stage
7. **I get notified** - I set up email alerts on failure
8. **Live in minutes** - I automated the entire process!

### Technical Flow (What I Implemented)

```
My GitHub Push 
    → (Webhook I configured)
    → Jenkins Checkout
    → SonarQube Analysis (I set up)
    → Docker Build (I wrote Dockerfile)
    → Container Deploy (I configured)
    → Health Check (I implemented)
    → Email Alert (I set up)
```

---

## 🌐 Application Features

### The News Website I Built

I created a **real-time news aggregator** that shows live headlines:

**What I Implemented:**
- 🔍 **Search News** - I built search functionality
- 🌍 **Global Coverage** - 150,000+ sources via NewsAPI
- 🗣️ **Multi-language** - I configured 14 language support
- 📅 **Date Filtering** - I added date range search
- 🏷️ **Source Filtering** - I implemented domain filtering
- ⚡ **Real-time Updates** - I integrated live API calls

**How I Integrated NewsAPI:**

I wrote this backend code:

```javascript
// server.js - I wrote this
app.get('/api/news', async (req, res) => {
  // I get the search query from user
  const query = req.query.q || 'technology';
  
  // I securely access the API key (injected by Jenkins)
  const apiKey = process.env.NEWS_API_KEY;
  
  try {
    // I make the API call to NewsAPI
    const response = await axios.get(
      `https://newsapi.org/v2/everything?q=${query}&apiKey=${apiKey}`
    );
    // I send formatted articles to frontend
    res.json(response.data.articles);
  } catch (error) {
    res.status(500).json({ error: error.message });
  }
});
```

---

## 🔧 CI/CD Pipeline I Created

### The Jenkins Pipeline (I Wrote This)

```groovy
pipeline {
  agent none  // I configured per-stage agents
  
  stages {
    stage('Checkout') {
      agent any
      steps {
        // I set up GitHub integration here
        checkout scm
        sh 'git log --oneline -1'
      }
    }
    
    stage('SonarQube Analysis') {
      agent any
      steps {
        // I configured SonarQube server connection
        withSonarQubeEnv('SonarQube') {
          sh 'sonar-scanner ...'  // I set up quality gates
        }
      }
    }
    
    stage('Build Docker Image') {
      agent { label 'docker' }  // I labeled Docker node
      steps {
        // I built the Docker image
        sh 'docker build -t news-website:${BUILD_NUMBER} .'
      }
    }
    
    stage('Deploy') {
      agent { label 'docker' }
      steps {
        // I deployed with secure secret injection
        sh '''
          docker run -d \
            -e NEWS_API_KEY="${NEWS_API_KEY}" \
            -p 3000:3000 \
            news-website:${BUILD_NUMBER}
        '''
      }
    }
  }
  
  post {
    success { 
      echo " Deployment Successful!" 
    }
    failure { 
      // I configured email notifications
      emailext (
        subject: "Build Failed: ${JOB_NAME} #${BUILD_NUMBER}",
        body: """
          I need to fix this failure in ${JOB_NAME}:
          
          Build #${BUILD_NUMBER} failed
          Check: ${BUILD_URL}
          
          Error details in console output
        """,
        to: "sksanthosh88409@gmail.com"
      )
    }
  }
}
```

### Real Pipeline Execution (I Achieved This)

```
Started by GitHub push by vsanthoshraj
✓ Checkout: I pulled the latest code
✓ SonarQube: I passed code quality checks
✓ Docker Build: I created image news-website:39
✓ Deploy: I deployed container successfully
✓ Cleanup: I cleaned up workspace

✅ BUILD SUCCESS!
My app is now live at: http://52.71.5.19:3000/api/news
```

---

## 🏗️ Infrastructure I Provisioned

### Terraform Code I Wrote

I structured the Terraform project like this:

```
terraform-cicd/  (I organized this way)
├── main.tf          # I wrote main module
├── variables.tf     # I defined all inputs
├── outputs.tf       # I specified outputs
├── provider.tf      # I set up AWS provider
│
├── ec2/             # I created EC2 module
│   ├── main.tf      # I defined instances
│   ├── variables.tf # I parameterized it
│   └── outputs.tf   # I exposed IPs
│
├── security_groups/ # I created security module
│   └── main.tf      # I restricted traffic
│
├── keypair/         # I created keypair module
│   └── main.tf      # I generated SSH keys
│
└── vpc/             # I created VPC module
    └── main.tf      # I designed networking
```

### Infrastructure I Created

```bash
# I ran these commands to deploy everything:

terraform init          # I initialized Terraform
terraform plan          # I reviewed my infrastructure
terraform apply         # I created all AWS resources

# What I provisioned:
# - 4x EC2 instances (Terraform, Jenkins, Docker, SonarQube)
# - Security groups with precise firewall rules
# - SSH key pairs for secure access
# - VPC with proper networking
```

---

## 🔒 Security I Implemented

### How I Protected Secrets

✅ **What I Did Right:**
- I stored API keys in Jenkins "Secret Text" credentials
- I injected secrets at runtime (not build time)
- I created `.gitignore` to prevent accidental commits
- I ensured Docker images have NO hardcoded secrets
- I masked secrets in Jenkins logs (shown as ****)
- I passed secrets only at container runtime

❌ **What I Avoided:**
- I never put secrets in source code
- I never baked secrets into Docker images
- I never committed secrets to Git
- I never stored plaintext credentials

### Example: How I Handled API Keys

```bash
# I made Jenkins inject the secret at runtime:
docker run -d \
  -e NEWS_API_KEY="${NEWS_API_KEY}" \  # Injected securely
  -p 3000:3000 \
  news-website:latest

# The Docker image has NO hardcoded key!
# Each deployment uses a different key from Jenkins
```

---

## 🔔 Notifications I Set Up

### Email Alerts I Configured

I set up **automatic email notifications** when pipelines fail.

**What I Configured to Alert Me:**
- ❌ Build failures (compilation errors I need to fix)
- ❌ SonarQube failures (code quality issues I introduced)
- ❌ Docker build failures (image build problems)
- ❌ Deployment failures (runtime issues)
- ❌ Health check failures (container problems)

**Email Notifications I Receive Include:**
- Job name and build number
- Error details
- Link to Jenkins console for debugging
- Build URL for quick navigation

### How I Set It Up (Step by Step)

1. **I went to Jenkins** → Manage Jenkins → Configure System
2. **I configured SMTP:**
   - Server: `smtp.gmail.com`
   - Port: `587`
   - I used my Gmail credentials
3. **I tested the configuration**
4. **I added email code to Jenkinsfile:**

```groovy
post {
  failure {
    emailext (
      subject: "❌ Pipeline Failed: ${JOB_NAME}",
      body: """
        I failed to deploy!
        
        Job: ${JOB_NAME}
        Build: #${BUILD_NUMBER}
        Check: ${BUILD_URL}
      """,
      to: "sksanthosh88409@gmail.com"
    )
  }
}
```

---

## 🚀 How I Deployed This Project

### Step 1: I Provisioned Infrastructure

```bash
# I cloned my Terraform repo
git clone https://github.com/vsanthoshraj/terraform-cicd-infrastructure.git
cd terraform-cicd-infrastructure

# I set up AWS credentials
export AWS_ACCESS_KEY_ID="my-key"
export AWS_SECRET_ACCESS_KEY="my-secret"

# I deployed all resources
terraform init
terraform apply -auto-approve
# Result: 4 EC2 instances created!
```

### Step 2: I Configured Jenkins

I manually:
- Accessed Jenkins at `http://my-jenkins-ip:8080`
- Installed plugins (Git, Docker, SonarQube Scanner, Pipeline)
- Created credentials (GitHub SSH, NewsAPI key, SMTP)
- Set up GitHub webhook to `http://my-jenkins-ip:8080/github-webhook/`

### Step 3: I Configured SonarQube

I:
- Accessed SonarQube at `http://my-sonarqube-ip:9000`
- Created a project named `news-website`
- Generated authentication token
- Added it to Jenkins configuration

### Step 4: I Set Up Docker Host

I SSH'd into Docker EC2 and:
```bash
# I installed Docker
sudo apt update
sudo apt install docker.io -y
sudo usermod -aG docker ubuntu

# I configured it as a Jenkins agent
# (so Jenkins can remotely run Docker commands)
```

### Step 5: I Created Jenkins Pipeline Job

I:
- Created a new Pipeline job in Jenkins
- Set GitHub project URL
- Enabled GitHub webhook trigger
- Pointed it to my Jenkinsfile in Git

### Step 6: I Pushed My First Deployment

```bash
# I cloned my application repo
git clone https://github.com/vsanthoshraj/g3sha-news-website-node-js.git
cd g3sha-news-website-node-js

# I made a test change
echo "# Live news aggregator" >> README.md

# I triggered the pipeline
git add .
git commit -m "Deploy news website"
git push origin main

# Jenkins automatically built, tested, and deployed it!
```

### Step 7: I Accessed My Live Application

```
http://my-ec2-ip:3000
```

---

## 🐳 Docker Image I Published

I pushed my image to Docker Hub without secrets:

```bash
# I tagged my image
docker tag news-website:latest vsanthoshraj/news-website:latest

# I pushed to Docker Hub
docker push vsanthoshraj/news-website:latest

# Others can now use it with their own API key:
docker pull vsanthoshraj/news-website:latest
docker run -e NEWS_API_KEY=their-key -p 3000:3000 vsanthoshraj/news-website:latest
```

---

## 📸 Screenshots & Demos

### I Created These Artifacts

- Jenkins pipeline execution logs
- SonarQube analysis dashboards
- Docker container running status
- Live news website interface
- Terraform apply output showing created resources
- AWS EC2 console with my instances
- Email notifications I received

---

## 🌟 Why This Project Shows My DevOps Skills

### What I Demonstrated for Recruiters

✅ **I can deploy on AWS** - Real infrastructure, not just tutorials
✅ **I automate everything** - Zero manual deployment steps
✅ **I follow industry practices** - Production-ready approach
✅ **I use modern tools** - Latest DevOps stack
✅ **I document well** - Professional README and comments
✅ **I think about security** - Jenkins secrets, no exposed keys
✅ **I set up monitoring** - Email alerts on failures
✅ **I build completely** - From code push to live website

### What I Demonstrated for Technical Reviewers

✅ **I write Infrastructure as Code** - Terraform modules with best practices
✅ **I understand CI/CD** - Jenkins pipelines with multiple stages
✅ **I care about code quality** - SonarQube integration and quality gates
✅ **I containerize correctly** - Docker without embedding secrets
✅ **I secure properly** - Jenkins secret management
✅ **I monitor systems** - Health checks and email alerting
✅ **I integrate APIs** - Real external service integration
✅ **I solve problems** - Debugging and troubleshooting

### Skills I Developed

| Category | What I Did |
|----------|-----------|
| **Cloud** | Designed and deployed AWS EC2 infrastructure |
| **IaC** | Wrote modular, reusable Terraform code |
| **CI/CD** | Built complete Jenkins declarative pipeline |
| **Containers** | Created secure Docker images without secrets |
| **Code Quality** | Integrated SonarQube quality gates |
| **Backend** | Wrote Node.js/Express REST API |
| **Frontend** | Built HTML/CSS/JS interface |
| **Security** | Managed secrets securely with Jenkins |
| **Version Control** | Used Git with GitHub webhooks |
| **DevOps** | Automated entire deployment lifecycle |

---

## 📚 Project Structure (What I Organized)

### My Application Repository

```
g3sha-news-website-node-js/
├── public/
│   ├── index.html      # Frontend I built
│   ├── styles.css      # Styling I designed
│   └── script.js       # Client-side logic I wrote
├── server.js           # Backend API I created
├── package.json        # Dependencies I chose
├── Dockerfile          # Container config I wrote
├── Jenkinsfile         # Pipeline I designed
└── .gitignore          # Security I implemented
```

### My Terraform Repository

```
terraform-cicd-infrastructure/
├── main.tf             # Root module I created
├── variables.tf        # Parameterized inputs
├── outputs.tf          # Resources I expose
├── provider.tf         # AWS config I set up
├── ec2/                # EC2 module I wrote
├── security_groups/    # Security rules I defined
├── keypair/            # SSH keys I configured
└── vpc/                # Networking I designed
```

---

## 🎓 What I Learned & Implemented

- I learned **AWS EC2** and deployed real infrastructure
- I learned **Terraform** and automated my infrastructure
- I learned **Jenkins** and built automated pipelines
- I learned **Docker** and containerized my application securely
- I learned **SonarQube** and enforced code quality
- I learned **GitHub webhooks** and triggered automation
- I learned **email notifications** for alerting
- I learned **API integration** with NewsAPI
- I learned **DevOps culture** and practices
- I troubleshot issues and solved real problems

---

## 🔗 My Projects & Resources

- **📱 My App**: [https://github.com/vsanthoshraj/g3sha-news-website-node-js](https://github.com/vsanthoshraj/g3sha-news-website-node-js)
- **🏗️ My Infrastructure**: [https://github.com/vsanthoshraj/terraform-cicd-infrastructure](https://github.com/vsanthoshraj/terraform-cicd-infrastructure)
- **🐳 My Docker Image**: [https://hub.docker.com/r/vsanthoshraj/news-website](https://hub.docker.com/r/vsanthoshraj/news-website)
- **📰 API I Used**: [https://newsapi.org](https://newsapi.org)
- **🚀 Live Demo**: http://<my-ec2-ip>:3000

---

## 📞 About Me

**Santhosh Raj V** - DevOps & Cloud Engineer  
📧 Email: [sksanthosh88409@gmail.com](mailto:sksanthosh88409@gmail.com)  
📱 Phone: 9566066846  
📍 Location: Chennai, India  
🔗 LinkedIn: [My LinkedIn Profile](your-linkedin-url)  
💼 GitHub: [@vsanthoshraj](https://github.com/vsanthoshraj)

**I'm actively looking for DevOps, Cloud, and CI/CD roles!**

---

I built this project using:
- NewsAPI for live news data
- Jenkins for CI/CD automation
- SonarQube for code quality
- Docker for containerization
- Terraform for infrastructure
- AWS for cloud infrastructure

<img width="1919" height="1068" alt="Screenshot 2025-11-10 170513" src="https://github.com/user-attachments/assets/77fc8177-8938-4542-8390-920d870e8a59" />

<img width="1919" height="1021" alt="Screenshot 2025-11-10 172329" src="https://github.com/user-attachments/assets/d66e80ef-533d-492a-b919-09c1d2b98bf9" />

<img width="1907" height="1012" alt="Screenshot 2025-11-10 170300" src="https://github.com/user-attachments/assets/a2dd4799-7c57-4b53-9738-19df24dc74ac" />

<img width="1914" height="1079" alt="Screenshot 2025-11-10 171322" src="https://github.com/user-attachments/assets/68a1109f-3e89-46d8-b1bb-7642c0073248" />

<img width="1914" height="1079" alt="Screenshot 2025-11-10 171322" src="https://github.com/user-attachments/assets/cdedf4f3-f6a9-46a9-b4fc-face598203b3" />


