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

- **📱 News Website App Repo**: [https://github.com/vsanthoshraj/g3sha-news-website-node-js](https://github.com/vsanthoshraj/g3sha-news-website-node-js)
- **🏗️ Terraform Infrastructure Repo**: [https://github.com/vsanthoshraj/terraform-cicd-infrastructure](https://github.com/vsanthoshraj/terraform-cicd-infrastructure)
- **🐳 Docker Image (No Secrets)**: [https://hub.docker.com/r/vsanthoshraj/news-website](https://hub.docker.com/r/vsanthoshraj/news-website)
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

1. [Project Overview](#project-overview)
2. [Architecture](#architecture)
3. [Technologies Used](#technologies-used)
4. [How It Works](#how-it-works)
5. [Application Features](#application-features)
6. [CI/CD Pipeline](#cicd-pipeline)
7. [Infrastructure Setup](#infrastructure-setup)
8. [Security Best Practices](#security-best-practices)
9. [Notifications & Alerting](#notifications--alerting)
10. [How to Run This Project](#how-to-run-this-project)
11. [Screenshots & Demos](#screenshots--demos)
12. [Why This Project Stands Out](#why-this-project-stands-out)

---

## 🎯 Project Overview

This is a **production-ready CI/CD pipeline** that automatically builds, tests, and deploys a Node.js news aggregation website using AWS cloud infrastructure and top DevOps tools.

### 🔐 API Key Security Highlight:
All sensitive secrets (like the NewsAPI key) are handled using **Jenkins "Secret Text" credentials**. The API key is **never exposed** in the source code, Docker image, or Git history—it's injected securely into the build and runtime environment by Jenkins.

**What makes this special:**
- Real AWS cloud infrastructure (not a local simulation)
- Fully automated pipeline from code push to live deployment
- Industry-standard tools and best practices
- Live news data integration using NewsAPI
- Complete DevOps lifecycle demonstration
- Email notifications on pipeline failures
- Secrets management using Jenkins credentials

---

## 🏗️ Architecture

```
┌─────────────┐
│   GitHub    │ ◄─── Developer pushes code
└──────┬──────┘
       │ Webhook Trigger
       ▼
┌─────────────────┐
│  Jenkins (EC2)  │ ◄─── Orchestrates Pipeline
└────────┬────────┘      (Sends Email on Failure)
         │
    ┌────┴────┬─────────┬──────────┐
    ▼         ▼         ▼          ▼
┌────────┐ ┌──────┐ ┌──────┐ ┌─────────┐
│SonarQube│ │Docker│ │ AWS │ │Terraform│
│  (EC2) │ │(EC2) │ │ EC2 │ │  (IaC)  │
└────────┘ └──────┘ └──────┘ └─────────┘
```

### Infrastructure Components

| Component | Instance | Purpose |
|-----------|----------|---------|
| **Terraform** | EC2-1 | Infrastructure as Code - provisions all AWS resources |
| **Jenkins** | EC2-2 | CI/CD orchestration, automation, and alerting |
| **Docker Host** | EC2-3 | Container runtime for application deployment |
| **SonarQube** | EC2-4 | Static code analysis and quality gates |

---

## 💻 Technologies Used

### DevOps & Cloud
- **AWS EC2** - Cloud compute instances
- **Terraform** - Infrastructure as Code (IaC)
- **Jenkins** - CI/CD automation server with email notifications
- **Docker** - Container platform
- **SonarQube** - Code quality analysis
- **GitHub** - Version control and webhook triggers

### Application Stack
- **Node.js** - Backend runtime
- **Express.js** - Web framework
- **NewsAPI** - Live news data source
- **HTML/CSS/JavaScript** - Frontend

---

## 🔄 How It Works

### Simple Explanation (Layman's Terms)

1. **Developer makes changes** - You update code and push to GitHub
2. **GitHub notifies Jenkins** - A webhook automatically triggers the pipeline
3. **Code quality check** - SonarQube analyzes code for bugs, security issues, and code smells
4. **Build container** - Docker packages the application into a portable container
5. **Deploy automatically** - The new version goes live on the server
6. **Done!** - Your changes are live in minutes, not hours
7. **If something breaks** - Jenkins sends an email notification to the team

### Technical Flow

```
GitHub Push 
    → Jenkins Webhook Trigger
    → SCM Checkout
    → SonarQube Static Analysis
    → Docker Image Build
    → Container Deployment
    → Health Check
    → Success/Failure Notification (Email)
```

---

## 🌐 Application Features

### News Website Functionality

The deployed application is a **real-time news aggregator** powered by NewsAPI:

**Key Features:**
- 🔍 **Search News** - Search by keywords, topics, or phrases
- 🌍 **Global Coverage** - News from 150,000+ sources in 55 countries
- 🗣️ **Multi-language** - Support for 14 languages
- 📅 **Date Filtering** - Search news by date range
- 🏷️ **Source Filtering** - Filter by specific domains or exclude sources
- ⚡ **Real-time Updates** - Always up-to-date with latest headlines

**How NewsAPI Integration Works:**

1. User requests news via web interface
2. Node.js backend receives request with search parameters
3. Server makes authenticated API call to NewsAPI (using securely stored API key)
4. NewsAPI returns JSON data with articles
5. Backend formats and sends data to frontend
6. User sees latest news articles displayed

**Sample API Call:**
```javascript
// server.js
app.get('/api/news', async (req, res) => {
  const query = req.query.q || 'technology';
  const apiKey = process.env.NEWS_API_KEY;  // Injected by Jenkins at runtime
  
  try {
    const response = await axios.get(
      `https://newsapi.org/v2/everything?q=${query}&apiKey=${apiKey}`
    );
    res.json(response.data.articles);
  } catch (error) {
    res.status(500).json({ error: error.message });
  }
});
```

---

## 🔧 CI/CD Pipeline

### Jenkins Pipeline Stages

```groovy
pipeline {
  agent none
  
  stages {
    stage('Checkout') {
      agent any
      steps {
        // Pull latest code from GitHub
        checkout scm
        sh 'git log --oneline -1'
      }
    }
    
    stage('SonarQube Analysis') {
      agent any
      steps {
        // Static code analysis with quality gates
        withSonarQubeEnv('SonarQube') {
          sh 'sonar-scanner ...'
        }
      }
    }
    
    stage('Build Docker Image') {
      agent { label 'docker' }
      steps {
        // Build and tag Docker image
        sh 'docker build -t news-website:${BUILD_NUMBER} .'
      }
    }
    
    stage('Deploy') {
      agent { label 'docker' }
      steps {
        // Deploy with securely injected API key
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
      // Email notification on failure
      emailext (
        subject: " Build Failed: ${JOB_NAME} #${BUILD_NUMBER}",
        body: """
          Pipeline failed for ${JOB_NAME}.
          Build Number: ${BUILD_NUMBER}
          Build URL: ${BUILD_URL}
          Check console output for details.
        """,
        to: "your-email@example.com"
      )
    }
  }
}
```

### Pipeline Execution Example

```
Started by GitHub push by vsanthoshraj
Checkout: ✓ Code pulled from main branch
SonarQube: ✓ Analysis passed - No critical issues
Docker Build: ✓ Image news-website:39 created
Deploy: ✓ Container running on port 3000
Cleanup: ✓ Workspace cleaned

 BUILD SUCCESS!
App running at: http://52.71.5.19:3000/api/news
```

---

## 🏗️ Infrastructure Setup

### Terraform Structure

```
terraform/
├── ec2/
│   └── main.tf          # EC2 instance definitions
├── security_groups/
│   └── main.tf          # Firewall rules
├── keypair/
│   └── main.tf          # SSH key configuration
├── vpc/
│   └── main.tf          # Network setup
├── main.tf              # Root module
├── variables.tf         # Input variables
├── outputs.tf           # Output values
└── provider.tf          # AWS provider config
```

### Key Terraform Resources

- **4x EC2 instances** - Terraform, Jenkins, Docker, SonarQube
- **Security Groups** - Controlled ingress/egress rules
- **SSH Key Pairs** - Secure instance access
- **VPC Configuration** - Network isolation


### Deploy Infrastructure

```bash
# Initialize Terraform
terraform init

# Plan infrastructure changes
terraform plan

# Apply changes
terraform apply -auto-approve

# Destroy when done
terraform destroy
```

---

## 🔒 Security Best Practices

### Secrets Management

✅ **What We Do Right:**
- API keys stored in Jenkins "Secret Text" credentials
- Environment variables injected at runtime (not at build time)
- `.gitignore` prevents credential commits
- Docker images contain NO hardcoded secrets
- Secrets passed at container runtime only
- No secrets exposed in Jenkins logs (masked with ****)

❌ **What We Avoid:**
- No secrets in source code
- No secrets in Docker images
- No secrets in version control
- No plaintext credential storage

### Example - Secure Secret Usage

```bash
# Jenkins injects secret at runtime (hidden from logs)
docker run -d \
  --name news-website \
  -e NEWS_API_KEY="${NEWS_API_KEY}" \
  -p 3000:3000 \
  news-website:latest
```

### AWS Security

- Security groups restrict traffic to necessary ports only
- SSH access via key pairs (no passwords)
- Principle of least privilege for IAM roles
- EC2 instances in private subnets (optional advanced setup)

---

## 🔔 Notifications & Alerting

### Email Notifications on Pipeline Failure

Jenkins is configured to send **automatic email notifications** when the pipeline fails. This ensures the team is immediately alerted to any issues.

**What triggers an email:**
- ❌ Build failure (compilation errors, missing dependencies)
- ❌ SonarQube quality gate failure
- ❌ Docker build failure
- ❌ Deployment failure
- ❌ Container health check failure

**Email includes:**
- Job name and build number
- Failure reason
- Link to Jenkins console logs
- Build URL for quick debugging

**Setup Email Notifications:**

1. Go to Jenkins **Manage Jenkins** → **Configure System**
2. Set up **Email Notification**:
   - SMTP Server: `smtp.gmail.com`
   - SMTP Port: `587`
   - Use SSL: `Yes`
   - Authentication: Your Gmail/email credentials
3. Test email configuration
4. Add `post` block to Jenkinsfile:

```groovy
post {
  failure {
    emailext (
      subject: " Build Failed: ${JOB_NAME} #${BUILD_NUMBER}",
      body: """
        Pipeline FAILED for: ${JOB_NAME}
        
        Build Number: ${BUILD_NUMBER}
        Build URL: ${BUILD_URL}
        
        Check console output for error details:
        ${BUILD_LOG}
      """,
      to: "your-email@example.com, team@example.com",
      attachmentsPattern: "console.log"
    )
  }
  success {
    echo " Build Successful - No email sent"
  }
}
```

---

## 🚀 How to Run This Project

### Prerequisites

- AWS Account
- GitHub Account
- NewsAPI Account (free tier: https://newsapi.org)
- Basic knowledge of Linux/command line

### Step 1: Deploy Infrastructure

```bash
# Clone Terraform repo
git clone https://github.com/vsanthoshraj/terraform-cicd-infrastructure.git
cd terraform-cicd-infrastructure

# Configure AWS credentials
export AWS_ACCESS_KEY_ID="your-key"
export AWS_SECRET_ACCESS_KEY="your-secret"

# Deploy infrastructure
terraform init
terraform apply
```

### Step 2: Configure Jenkins

1. Access Jenkins at `http://<jenkins-ec2-ip>:8080`
2. Install plugins: Git, Docker, SonarQube Scanner, Pipeline, Email Extension
3. Add GitHub webhook: `http://<jenkins-ip>:8080/github-webhook/`
4. Create Jenkins credentials:
   - GitHub SSH key (Kind: SSH Username with Private Key)
   - NewsAPI key (Kind: Secret Text)
   - Docker Hub credentials (optional)
   - Email SMTP credentials

### Step 3: Configure SonarQube

1. Access SonarQube at `http://<sonarqube-ec2-ip>:9000`
2. Create project with key: `news-website`
3. Generate authentication token
4. Add token to Jenkins SonarQube configuration

### Step 4: Setup Docker Host

```bash
# SSH into Docker EC2
ssh -i your-key.pem ubuntu@<docker-ec2-ip>

# Install Docker
sudo apt update
sudo apt install docker.io -y
sudo usermod -aG docker ubuntu

# Configure as Jenkins agent
```

### Step 5: Create Jenkins Pipeline Job

1. **New Item** → **Pipeline**
2. **GitHub project** URL: `https://github.com/vsanthoshraj/g3sha-news-website-node-js`
3. **Build Triggers** → Check "GitHub hook trigger for GITScm polling"
4. **Pipeline** → Select "Pipeline script from SCM"
5. **SCM** → Git → Repository URL & credentials
6. **Script Path** → `Jenkinsfile`
7. Save and trigger!

### Step 6: Deploy Application

```bash
# Clone application repo
git clone https://github.com/vsanthoshraj/g3sha-news-website-node-js.git
cd g3sha-news-website-node-js

# Make a test change
echo "# Updated" >> README.md

# Push to trigger pipeline
git add .
git commit -m "Trigger CI/CD pipeline"
git push origin main

# Watch Jenkins pipeline execute!
```

### Step 7: Access Your Website

```
http://<docker-ec2-ip>:3000
```

### Step 8: Run Docker Image Locally (Optional)

```bash
# Pull the Docker image
docker pull vsanthoshraj/news-website:latest

# Run with your own NewsAPI key
docker run -d \
  -e NEWS_API_KEY=your_newsapi_key_from_newsapi.org \
  -p 3000:3000 \
  vsanthoshraj/news-website:latest

# Access at http://localhost:3000
```

---

## 📸 Screenshots & Demos

### Add Your Own Screenshots

- Jenkins pipeline execution with email alert
- SonarQube analysis dashboard
- Docker container running
- Live news website interface
- Terraform apply output
- AWS EC2 console showing instances
- Email notification example

---

## 🌟 Why This Project Stands Out

### For Recruiters

✅ **Real AWS deployment** - Not just a local lab
✅ **Production-ready practices** - Industry standard tools
✅ **Complete automation** - Zero manual deployment steps
✅ **Modern stack** - Latest DevOps technologies
✅ **Well documented** - Professional README and code comments
✅ **Live demo** - Actual working application
✅ **Cost-conscious** - Uses free tiers and minimal resources
✅ **Alert System** - Email notifications for failures

### For Technical Reviewers

✅ **Infrastructure as Code** - Terraform best practices
✅ **CI/CD Pipeline** - Jenkins declarative pipeline
✅ **Code Quality** - SonarQube integration
✅ **Containerization** - Docker multi-stage builds
✅ **Security** - Proper secrets management with Jenkins
✅ **Monitoring** - Health checks and email alerting
✅ **Git Workflow** - Webhook-driven automation
✅ **API Integration** - Real external service (NewsAPI)

### Skills Demonstrated

| Category | Skills |
|----------|--------|
| **Cloud** | AWS EC2, VPC, Security Groups, IAM |
| **IaC** | Terraform, Infrastructure provisioning |
| **CI/CD** | Jenkins Pipeline, GitHub Webhooks, Email Notifications |
| **Containers** | Docker, Image building, Container orchestration |
| **Code Quality** | SonarQube, Static analysis, Quality gates |
| **Backend** | Node.js, Express.js, REST API integration |
| **Frontend** | HTML, CSS, JavaScript |
| **Security** | Jenkins secrets, Environment variables, Secure deployments |
| **Version Control** | Git, GitHub, Branching strategies |
| **DevOps** | End-to-end automation, Infrastructure setup |

---

## 📚 Project Structure

### Application Repository

```
news-website/
├── public/
│   ├── index.html      # Frontend UI
│   ├── styles.css      # Styling
│   └── script.js       # Client-side JS
├── server.js           # Node.js backend
├── package.json        # Dependencies
├── Dockerfile          # Container definition (NO secrets baked in)
├── Jenkinsfile         # Pipeline definition with email alerts
└── .gitignore          # Excluded files (env, node_modules, etc)
```

### Terraform Repository

```
terraform-cicd/
├── main.tf             # Calls the modules and defines infrastructure composition
├── variables.tf        # Input variables for the root module
├── outputs.tf          # Output values from the root module
├── provider.tf         # AWS provider configuration (often moved to root if shared)
│
├── ec2/
│   ├── main.tf         # Defines the 'aws_instance' resource
│   ├── variables.tf    # Variables required by the EC2 module
│   └── outputs.tf      # Outputs provided by the EC2 module (e.g., instance IP)
│
├── security_groups/
│   ├── main.tf         # Defines the 'aws_security_group' resource(s)
│   ├── variables.tf    # Variables required by the security group module
│   └── outputs.tf      # Outputs provided by the security group module
│
├── keypair/
│   ├── main.tf         # Defines the 'aws_key_pair' resource
│   ├── variables.tf    # Variables required by the keypair module
│   └── outputs.tf      # Outputs provided by the keypair module
│
└── vpc/
    ├── main.tf         # Defines the VPC and subnets resources
    ├── variables.tf    # Variables required by the VPC module
    └── outputs.tf      # Outputs provided by the VPC module
```

---

## 🎓 What I Learned

- **Cloud Architecture** - Designing multi-instance AWS infrastructure
- **Automation** - End-to-end pipeline automation
- **DevOps Culture** - Collaboration between dev and ops
- **Container Technology** - Docker best practices
- **Code Quality** - Implementing quality gates with SonarQube
- **Infrastructure as Code** - Reproducible infrastructure with Terraform
- **Security** - Secure credential handling with Jenkins secrets
- **API Integration** - Working with external services (NewsAPI)
- **Problem Solving** - Debugging CI/CD issues
- **Alerting & Monitoring** - Email notifications for pipeline failures

---

## 🔗 Links & Resources

- **📱 News Website App Repo**: [https://github.com/vsanthoshraj/g3sha-news-website-node-js](https://github.com/vsanthoshraj/g3sha-news-website-node-js)
- **🏗️ Terraform Infrastructure Repo**: [https://github.com/vsanthoshraj/terraform-cicd-infrastructure](https://github.com/vsanthoshraj/terraform-cicd-infrastructure)
- **🐳 Docker Hub Image**: [https://hub.docker.com/r/vsanthoshraj/news-website](https://hub.docker.com/r/vsanthoshraj/news-website)
- **📰 NewsAPI**: [https://newsapi.org](https://newsapi.org)
- **🚀 Live Demo**: http://<your-ec2-ip>:3000

---

## 📞 Contact

**Santhosh Raj V**  
📧 Email: [sksanthosh88409@gmail.com](mailto:sksanthosh88409@gmail.com)  
📱 Phone: 9566066846  
📍 Location: Chennai  
🔗 LinkedIn: [Your LinkedIn Profile](your-linkedin-url)  
💼 GitHub: [@vsanthoshraj](https://github.com/vsanthoshraj)

---

## 🙏 Acknowledgments

- NewsAPI for providing free, reliable news data
- Jenkins community for excellent CI/CD automation tools
- SonarSource for industry-leading code quality platform
- Docker for revolutionary containerization technology
- HashiCorp for powerful Infrastructure as Code with Terraform
- AWS for scalable cloud infrastructure

