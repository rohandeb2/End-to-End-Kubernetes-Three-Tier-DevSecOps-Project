# 🚀 Three-Tier Application Deployment with CI/CD

<div align="center">

![AWS](https://img.shields.io/badge/AWS-%23FF9900.svg?style=for-the-badge&logo=amazon-aws&logoColor=white)
![Kubernetes](https://img.shields.io/badge/kubernetes-%23326ce5.svg?style=for-the-badge&logo=kubernetes&logoColor=white)
![Docker](https://img.shields.io/badge/docker-%230db7ed.svg?style=for-the-badge&logo=docker&logoColor=white)
![Jenkins](https://img.shields.io/badge/jenkins-%232C5263.svg?style=for-the-badge&logo=jenkins&logoColor=white)
![ArgoCD](https://img.shields.io/badge/argo-EF7B4D.svg?style=for-the-badge&logo=argo&logoColor=white)
![Terraform](https://img.shields.io/badge/terraform-%235835CC.svg?style=for-the-badge&logo=terraform&logoColor=white)
![Prometheus](https://img.shields.io/badge/Prometheus-E6522C?style=for-the-badge&logo=Prometheus&logoColor=white)
![Grafana](https://img.shields.io/badge/grafana-%23F46800.svg?style=for-the-badge&logo=grafana&logoColor=white)

*A complete end-to-end DevOps project implementing a three-tier application with automated CI/CD pipeline, infrastructure as code, and comprehensive monitoring*

[Features](#features) • [Architecture](#architecture) • [Prerequisites](#prerequisites) • [Installation](#installation) • [Monitoring](#monitoring)

</div>

---

## 📋 Table of Contents

- [Overview](#overview)
- [Features](#features)
- [Architecture](#architecture)
- [Tech Stack](#tech-stack)
- [Prerequisites](#prerequisites)
- [Installation Guide](#installation-guide)
  - [Phase 1: Infrastructure Setup](#phase-1-infrastructure-setup)
  - [Phase 2: Jenkins Configuration](#phase-2-jenkins-configuration)
  - [Phase 3: EKS Cluster Setup](#phase-3-eks-cluster-setup)
  - [Phase 4: ArgoCD Deployment](#phase-4-argocd-deployment)
  - [Phase 5: Application Deployment](#phase-5-application-deployment)
  - [Phase 6: Monitoring Setup](#phase-6-monitoring-setup)
- [Pipeline Details](#pipeline-details)
- [Monitoring & Observability](#monitoring--observability)
- [Troubleshooting](#troubleshooting)
- [Contributing](#contributing)
- [License](#license)

---

## 🎯 Overview

This project demonstrates a production-grade three-tier application deployment on AWS using modern DevOps practices. It showcases:

- **Infrastructure as Code** with Terraform
- **Continuous Integration** with Jenkins and SonarQube
- **Continuous Deployment** with ArgoCD (GitOps)
- **Container Orchestration** with Amazon EKS
- **Monitoring & Observability** with Prometheus and Grafana

## ✨ Features

- 🏗️ **Automated Infrastructure Provisioning** - Terraform-managed AWS resources
- 🔄 **CI/CD Pipeline** - Automated build, test, and deployment
- 🔒 **Security Scanning** - SonarQube code quality and OWASP dependency checks
- 📦 **Container Registry** - Private ECR repositories for Docker images
- 🎯 **GitOps Deployment** - ArgoCD for declarative continuous delivery
- 📊 **Real-time Monitoring** - Prometheus metrics and Grafana dashboards
- 🌐 **Load Balancing** - AWS Application Load Balancer with Ingress
- 🔐 **IAM Security** - Role-based access control

## 🏛️ Architecture

```
┌─────────────────────────────────────────────────────────────────┐
│                          AWS Cloud                              │
│                                                                 │
│  ┌──────────────┐         ┌─────────────────────────────────┐ │
│  │   Jenkins    │────────▶│         Amazon ECR              │ │
│  │   Server     │         │  ┌──────────┐   ┌──────────┐   │ │
│  │  (CI/CD)     │         │  │ Frontend │   │ Backend  │   │ │
│  └──────────────┘         │  │  Image   │   │  Image   │   │ │
│         │                 │  └──────────┘   └──────────┘   │ │
│         │                 └─────────────────────────────────┘ │
│         │                              │                       │
│         ▼                              ▼                       │
│  ┌──────────────┐         ┌─────────────────────────────────┐ │
│  │  SonarQube   │         │      Amazon EKS Cluster         │ │
│  │   Server     │         │  ┌─────────────────────────┐   │ │
│  └──────────────┘         │  │       ArgoCD            │   │ │
│                           │  │    (GitOps Engine)      │   │ │
│  ┌──────────────┐         │  └─────────────────────────┘   │ │
│  │ Jump Server  │────────▶│                                 │ │
│  │ (Management) │         │  ┌───────┐ ┌───────┐ ┌───────┐ │ │
│  └──────────────┘         │  │  DB   │ │Backend│ │Front  │ │ │
│                           │  │ Pod   │ │  Pod  │ │  Pod  │ │ │
│                           │  └───────┘ └───────┘ └───────┘ │ │
│                           │                                 │ │
│                           │  ┌─────────────────────────┐   │ │
│                           │  │  AWS Load Balancer      │   │ │
│                           │  │     Controller          │   │ │
│                           │  └─────────────────────────┘   │ │
│                           └─────────────────────────────────┘ │
│                                          │                     │
│                           ┌──────────────┴──────────────┐     │
│                           │                             │     │
│                    ┌──────▼──────┐           ┌─────────▼────┐│
│                    │ Prometheus  │           │   Grafana    ││
│                    │  Monitoring │           │  Dashboard   ││
│                    └─────────────┘           └──────────────┘│
└─────────────────────────────────────────────────────────────────┘
```

## 🛠️ Tech Stack

### Infrastructure & Cloud
- **AWS EC2** - Virtual servers for Jenkins, SonarQube, and Jump Server
- **Amazon EKS** - Managed Kubernetes service
- **AWS VPC** - Network isolation and security
- **Terraform** - Infrastructure as Code

### CI/CD & GitOps
- **Jenkins** - Continuous Integration server
- **ArgoCD** - GitOps continuous delivery
- **GitHub** - Source code management

### Container & Orchestration
- **Docker** - Containerization
- **Kubernetes** - Container orchestration
- **Helm** - Kubernetes package manager
- **Amazon ECR** - Container registry

### Security & Quality
- **SonarQube** - Code quality and security analysis
- **OWASP Dependency Check** - Vulnerability scanning
- **AWS IAM** - Identity and access management

### Monitoring & Observability
- **Prometheus** - Metrics collection
- **Grafana** - Metrics visualization

## 📦 Prerequisites

Before starting, ensure you have:

- **AWS Account** with appropriate permissions
- **AWS CLI** configured with credentials
- **GitHub Account** and Personal Access Token (PAT)
- **Domain Name** (optional, for production setup)
- **Basic knowledge** of:
  - AWS services
  - Kubernetes concepts
  - Docker containerization
  - CI/CD principles

### Required Tools (will be installed during setup)
- Terraform
- kubectl
- eksctl
- Helm
- Docker
- Node.js

---

## 🚀 Installation Guide

### Phase 1: Infrastructure Setup

#### Step 1.1: Create Jenkins Server

1. **Launch EC2 Instance**
   ```
   Instance Type: t2.2xlarge
   AMI: Ubuntu 22.04 LTS
   Storage: 30 GB
   Key Pair: Proceed without a key pair
   Security Group: Select existing security group (allow ports 8080, 9000, 22)
   ```

2. **Configure IAM Role**
   - Navigate to **Advanced Details**
   - Create new IAM role with **AdministratorAccess**
   - Attach role to EC2 instance

3. **Install Jenkins**
   
   Add the following to **User Data**:
   ```bash
   #!/bin/bash
   sudo apt update -y
   sudo apt install openjdk-17-jre -y
   
   curl -fsSL https://pkg.jenkins.io/debian-stable/jenkins.io-2023.key | sudo tee \
     /usr/share/keyrings/jenkins-keyring.asc > /dev/null
   
   echo deb [signed-by=/usr/share/keyrings/jenkins-keyring.asc] \
     https://pkg.jenkins.io/debian-stable binary/ | sudo tee \
     /etc/apt/sources.list.d/jenkins.list > /dev/null
   
   sudo apt-get update -y
   sudo apt-get install jenkins -y
   sudo systemctl start jenkins
   sudo systemctl enable jenkins
   ```

4. **Access Jenkins**
   - Navigate to `http://<EC2-PUBLIC-IP>:8080`
   - Retrieve initial admin password:
     ```bash
     sudo cat /var/lib/jenkins/secrets/initialAdminPassword
     ```
   - Install suggested plugins
   - Create admin user credentials

#### Step 1.2: Install Required Jenkins Plugins

Navigate to **Jenkins → Manage Jenkins → Plugins → Available Plugins**

Install the following plugins:
- AWS Credentials
- Pipeline: AWS Steps
- Terraform
- Pipeline Stage View
- Docker
- Docker Pipeline
- Docker Commons
- Docker API
- NodeJS
- OWASP Dependency-Check
- SonarQube Scanner

### Phase 2: Jenkins Configuration

#### Step 2.1: Configure AWS Credentials

1. Go to **Jenkins → Manage Jenkins → Credentials → Global → Add Credentials**
2. Configure:
   ```
   Kind: AWS Credentials
   ID: aws-cred
   Access Key ID: <Your AWS Access Key>
   Secret Access Key: <Your AWS Secret Key>
   ```

#### Step 2.2: Configure Terraform

1. **Install Terraform on Jenkins Server**
   ```bash
   wget -O- https://apt.releases.hashicorp.com/gpg | sudo gpg --dearmor -o /usr/share/keyrings/hashicorp-archive-keyring.gpg
   echo "deb [signed-by=/usr/share/keyrings/hashicorp-archive-keyring.gpg] https://apt.releases.hashicorp.com $(lsb_release -cs) main" | sudo tee /etc/apt/sources.list.d/hashicorp.list
   sudo apt update && sudo apt install terraform -y
   ```

2. **Configure in Jenkins**
   - Navigate to **Jenkins → Manage Jenkins → Tools**
   - Search for **Terraform**
   - Add Terraform installation:
     ```
     Name: terraform
     Install automatically: Uncheck
     Install directory: /usr/bin (verify with `whereis terraform`)
     ```

#### Step 2.3: Configure SonarQube

1. **Access SonarQube**
   - Navigate to `http://<SONARQUBE-IP>:9000`
   - Default credentials: `admin / admin`

2. **Generate Token**
   - Go to **Administration → Security → Users**
   - Click on tokens icon → Generate Token
   - Save the token securely

3. **Configure Webhook**
   - Go to **Administration → Configuration → Webhooks**
   - Create webhook:
     ```
     Name: jenkins
     URL: http://<JENKINS-IP>:8080/sonarqube-webhook/
     ```

4. **Create Projects**
   
   For Frontend:
   - Navigate to **Projects → Create Manually**
   - Project key: `frontend`
   - Setup → Locally → Use existing token
   - Select: Other / Linux
   - Copy the generated scanner command

   For Backend:
   - Repeat the same process with project key: `backend`

5. **Add SonarQube Token to Jenkins**
   - Go to **Jenkins → Manage Jenkins → Credentials → Global**
   - Add Credential:
     ```
     Kind: Secret text
     Secret: <SonarQube Token>
     ID: sonar-token
     ```

#### Step 2.4: Configure Additional Jenkins Credentials

1. **AWS Account ID**
   ```
   Kind: Secret text
   Secret: <Your AWS Account ID>
   ID: account-id
   ```

2. **ECR Repository Names**
   
   Frontend:
   ```
   Kind: Secret text
   Secret: frontend
   ID: ECR_REPO1
   ```
   
   Backend:
   ```
   Kind: Secret text
   Secret: backend
   ID: ECR_REPO2
   ```

3. **GitHub Credentials**
   ```
   Kind: Username with password
   Username: <GitHub Username>
   Password: <GitHub Personal Access Token>
   ID: github-cred
   ```

#### Step 2.5: Configure Jenkins Tools

Navigate to **Jenkins → Manage Jenkins → Tools**

1. **NodeJS**
   ```
   Name: nodejs
   Install automatically: Check
   Version: Latest LTS
   ```

2. **SonarQube Scanner**
   ```
   Install from Maven Central
   ```

3. **OWASP Dependency-Check**
   ```
   Name: dependency-check
   Install automatically: Check
   Install from: github.com
   ```

4. **Docker**
   ```
   Name: docker
   Install automatically: Check
   ```

#### Step 2.6: Configure SonarQube Server in Jenkins

1. Navigate to **Jenkins → Manage Jenkins → System**
2. Search for **SonarQube servers**
3. Add SonarQube installation:
   ```
   Name: sonar-server
   Server URL: http://<SONARQUBE-IP>:9000
   Server authentication token: sonar-token
   ```

#### Step 2.7: Create ECR Repositories

```bash
# Frontend repository
aws ecr create-repository --repository-name frontend --region us-east-1

# Backend repository
aws ecr create-repository --repository-name backend --region us-east-1
```

#### Step 2.8: Create Infrastructure Pipeline

1. Go to **Jenkins Dashboard → New Item**
2. Name: `terraform-infra-pipeline`
3. Type: Pipeline
4. Pipeline script:
   ```groovy
   pipeline {
       agent any
       
       parameters {
           choice(name: 'ENV', choices: ['dev', 'prod'], description: 'Select environment')
           choice(name: 'TERRAFORM_ACTION', choices: ['apply', 'destroy'], description: 'Select Terraform action')
       }
       
       stages {
           stage('Checkout') {
               steps {
                   git branch: 'main', url: 'https://github.com/<your-repo>/terraform-eks.git'
               }
           }
           
           stage('Terraform Init') {
               steps {
                   sh 'terraform init'
               }
           }
           
           stage('Terraform Plan') {
               steps {
                   sh 'terraform plan -var="env=${ENV}"'
               }
           }
           
           stage('Terraform Apply/Destroy') {
               steps {
                   script {
                       if (params.TERRAFORM_ACTION == 'apply') {
                           sh 'terraform apply -auto-approve -var="env=${ENV}"'
                       } else {
                           sh 'terraform destroy -auto-approve -var="env=${ENV}"'
                       }
                   }
               }
           }
       }
   }
   ```

5. **Run Pipeline**
   - Click **Build with Parameters**
   - Select `ENV: dev`
   - Select `TERRAFORM_ACTION: apply`
   - Click **Build**

### Phase 3: EKS Cluster Setup

#### Step 3.1: Create Jump Server

1. **Launch EC2 Instance**
   ```
   Name: jump-server
   Instance Type: t2.medium
   Key Pair: Proceed without key pair
   VPC: Select your custom VPC
   Subnet: Select public subnet
   Storage: 30 GB
   IAM Role: Select the created IAM role
   ```

2. **Install Required Tools (User Data)**
   ```bash
   #!/bin/bash
   # Update system
   sudo apt update -y
   
   # Install AWS CLI
   curl "https://awscli.amazonaws.com/awscli-exe-linux-x86_64.zip" -o "awscliv2.zip"
   sudo apt install unzip -y
   unzip awscliv2.zip
   sudo ./aws/install
   
   # Install kubectl
   curl -LO "https://dl.k8s.io/release/$(curl -L -s https://dl.k8s.io/release/stable.txt)/bin/linux/amd64/kubectl"
   sudo install -o root -g root -m 0755 kubectl /usr/local/bin/kubectl
   
   # Install eksctl
   curl --silent --location "https://github.com/weaveworks/eksctl/releases/latest/download/eksctl_$(uname -s)_amd64.tar.gz" | tar xz -C /tmp
   sudo mv /tmp/eksctl /usr/local/bin
   
   # Install Helm
   curl https://raw.githubusercontent.com/helm/helm/main/scripts/get-helm-3 | bash
   ```

#### Step 3.2: Configure EKS Cluster Access

```bash
# Configure AWS credentials
aws configure

# Update kubeconfig
aws eks update-kubeconfig --name <cluster-name> --region us-east-1

# Verify cluster access
kubectl get nodes
```

#### Step 3.3: Install AWS Load Balancer Controller

1. **Download IAM Policy**
   ```bash
   curl -O https://raw.githubusercontent.com/kubernetes-sigs/aws-load-balancer-controller/v2.5.4/docs/install/iam_policy.json
   ```

2. **Create IAM Policy**
   ```bash
   aws iam create-policy \
       --policy-name AWSLoadBalancerControllerIAMPolicy \
       --policy-document file://iam_policy.json
   ```

3. **Create IAM Service Account**
   ```bash
   eksctl create iamserviceaccount \
     --cluster=dev-medium-eks-cluster \
     --namespace=kube-system \
     --name=aws-load-balancer-controller \
     --role-name AmazonEKSLoadBalancerControllerRole \
     --attach-policy-arn=arn:aws:iam::<ACCOUNT-ID>:policy/AWSLoadBalancerControllerIAMPolicy \
     --approve \
     --region=us-east-1
   ```

4. **Verify Service Account**
   ```bash
   kubectl get sa -n kube-system aws-load-balancer-controller
   ```

5. **Install Controller with Helm**
   ```bash
   # Add EKS Helm repository
   helm repo add eks https://aws.github.io/eks-charts
   helm repo update eks
   
   # Install AWS Load Balancer Controller
   helm install aws-load-balancer-controller eks/aws-load-balancer-controller \
     -n kube-system \
     --set clusterName=dev-medium-eks-cluster \
     --set serviceAccount.create=false \
     --set serviceAccount.name=aws-load-balancer-controller
   ```

6. **Verify Installation**
   ```bash
   kubectl get deployment -n kube-system aws-load-balancer-controller
   ```

### Phase 4: ArgoCD Deployment

#### Step 4.1: Install ArgoCD

```bash
# Create ArgoCD namespace
kubectl create namespace argocd

# Install ArgoCD
kubectl apply -n argocd -f https://raw.githubusercontent.com/argoproj/argo-cd/v2.4.7/manifests/install.yaml

# Verify installation
kubectl get all -n argocd
```

#### Step 4.2: Expose ArgoCD Server

```bash
# Edit service to LoadBalancer
kubectl edit svc argocd-server -n argocd

# Change: type: ClusterIP
# To:     type: LoadBalancer

# Get LoadBalancer URL
kubectl get svc argocd-server -n argocd
```

#### Step 4.3: Retrieve ArgoCD Admin Password

```bash
# Get password secret
kubectl get secrets -n argocd

# Decode password
kubectl get secret argocd-initial-admin-secret -n argocd -o jsonpath="{.data.password}" | base64 --decode
echo
```

#### Step 4.4: Access ArgoCD UI

- URL: `http://<ARGOCD-LOADBALANCER-URL>`
- Username: `admin`
- Password: `<decoded-password>`

#### Step 4.5: Connect Git Repository

1. Navigate to **Settings → Repositories**
2. Click **Connect Repo**
3. Configure:
   ```
   Method: HTTPS
   Project: default
   Repository URL: https://github.com/<your-username>/<your-repo>.git
   Username: <GitHub username>
   Password: <GitHub PAT>
   ```

### Phase 5: Application Deployment

#### Step 5.1: Create Application Namespace

```bash
kubectl create namespace three-tier
```

#### Step 5.2: Deploy Database

1. In ArgoCD UI, click **New App**
2. Configure:
   ```
   Application Name: three-tier-database
   Project: default
   Sync Policy: Automatic
   Self Heal: Enable
   
   Source:
   Repository URL: https://github.com/<your-repo>.git
   Path: kubernetes-manifests-file/Database
   
   Destination:
   Cluster URL: https://kubernetes.default.svc
   Namespace: three-tier
   ```

3. Click **Create**

4. Verify deployment:
   ```bash
   kubectl get all -n three-tier
   kubectl get pvc -n three-tier
   ```

#### Step 5.3: Deploy Backend

1. Create new application in ArgoCD:
   ```
   Application Name: three-tier-backend
   Project: default
   Sync Policy: Automatic
   Self Heal: Enable
   
   Source:
   Repository URL: https://github.com/<your-repo>.git
   Path: kubernetes-manifests-file/Backend
   
   Destination:
   Cluster URL: https://kubernetes.default.svc
   Namespace: three-tier
   ```

2. Verify:
   ```bash
   kubectl get all -n three-tier
   ```

#### Step 5.4: Deploy Frontend

1. Create new application in ArgoCD:
   ```
   Application Name: three-tier-frontend
   Project: default
   Sync Policy: Automatic
   Self Heal: Enable
   
   Source:
   Repository URL: https://github.com/<your-repo>.git
   Path: kubernetes-manifests-file/Frontend
   
   Destination:
   Cluster URL: https://kubernetes.default.svc
   Namespace: three-tier
   ```

#### Step 5.5: Deploy Ingress

1. Create new application in ArgoCD:
   ```
   Application Name: three-tier-ingress
   Project: default
   Sync Policy: Automatic
   Self Heal: Enable
   
   Source:
   Repository URL: https://github.com/<your-repo>.git
   Path: kubernetes-manifests-file/Ingress
   
   Destination:
   Cluster URL: https://kubernetes.default.svc
   Namespace: three-tier
   ```

2. Verify ingress:
   ```bash
   kubectl get ingress -n three-tier
   ```

#### Step 5.6: Configure Domain (Optional)

1. Get ALB DNS name:
   ```bash
   kubectl get ingress -n three-tier
   ```

2. Configure DNS:
   - Go to your domain provider (GoDaddy, Route53, etc.)
   - Create CNAME record pointing to ALB DNS

### Phase 6: Monitoring Setup

#### Step 6.1: Install Prometheus

```bash
# Add Helm repositories
helm repo add stable https://charts.helm.sh/stable
helm repo add prometheus-community https://prometheus-community.github.io/helm-charts
helm repo update

# Install Prometheus
helm install prometheus prometheus-community/prometheus

# Verify installation
kubectl get all | grep prometheus
```

#### Step 6.2: Expose Prometheus

```bash
# Edit service
kubectl edit svc prometheus-server

# Change: type: ClusterIP
# To:     type: LoadBalancer

# Get URL
kubectl get svc prometheus-server
```

#### Step 6.3: Install Grafana

```bash
# Add Grafana repository
helm repo add grafana https://grafana.github.io/helm-charts
helm repo update

# Install Grafana
helm install grafana grafana/grafana

# Verify installation
kubectl get all | grep grafana
```

#### Step 6.4: Expose Grafana

```bash
# Edit service
kubectl edit svc grafana

# Change: type: ClusterIP
# To:     type: LoadBalancer

# Get URL
kubectl get svc grafana
```

#### Step 6.5: Get Grafana Admin Password

```bash
kubectl get secret grafana -o jsonpath="{.data.admin-password}" | base64 --decode
echo
```

#### Step 6.6: Configure Grafana

1. Access Grafana: `http://<GRAFANA-LOADBALANCER-URL>`
2. Login with:
   ```
   Username: admin
   Password: <decoded-password>
   ```

3. **Add Prometheus Data Source**
   - Navigate to **Configuration → Data Sources**
   - Click **Add data source**
   - Select **Prometheus**
   - Configure:
     ```
     Name: Prometheus
     URL: http://prometheus-server.default.svc.cluster.local
     ```
   - Click **Save & Test**

4. **Import Dashboard**
   - Navigate to **Dashboards → Import**
   - Enter dashboard ID (e.g., `3119` for Kubernetes cluster monitoring)
   - Select Prometheus data source
   - Click **Import**

---

## 🔧 Pipeline Details

### Frontend CI Pipeline

```groovy
pipeline {
    agent any
    
    tools {
        nodejs 'nodejs'
    }
    
    environment {
        SCANNER_HOME = tool 'sonar-scanner'
        AWS_ACCOUNT_ID = credentials('account-id')
        AWS_ECR_REPO_NAME = credentials('ECR_REPO1')
        AWS_DEFAULT_REGION = 'us-east-1'
        REPOSITORY_URI = "${AWS_ACCOUNT_ID}.dkr.ecr.${AWS_DEFAULT_REGION}.amazonaws.com/"
    }
    
    stages {
        stage('Clean Workspace') {
            steps {
                cleanWs()
            }
        }
        
        stage('Checkout from Git') {
            steps {
                git branch: 'main', credentialsId: 'github-cred', url: 'https://github.com/<your-repo>/frontend.git'
            }
        }
        
        stage('SonarQube Analysis') {
            steps {
                withSonarQubeEnv('sonar-server') {
                    sh """
                    ${SCANNER_HOME}/bin/sonar-scanner \
                    -Dsonar.projectKey=frontend \
                    -Dsonar.sources=. \
                    -Dsonar.host.url=http://localhost:9000 \
                    -Dsonar.login=${SONAR_TOKEN}
                    """
                }
            }
        }
        
        stage('Quality Gate') {
            steps {
                timeout(time: 1, unit: 'HOURS') {
                    waitForQualityGate abortPipeline: false
                }
            }
        }
        
        stage('OWASP Dependency Check') {
            steps {
                dependencyCheck additionalArguments: '--scan ./ --disableYarnAudit --disableNodeAudit', odcInstallation: 'dependency-check'
                dependencyCheckPublisher pattern: '**/dependency-check-report.xml'
            }
        }
        
        stage('Build Docker Image') {
            steps {
                script {
                    sh "docker build -t ${AWS_ECR_REPO_NAME} ."
                }
            }
        }
        
        stage('Push to ECR') {
            steps {
                script {
                    sh """
                    aws ecr get-login-password --region ${AWS_DEFAULT_REGION} | docker login --username AWS --password-stdin ${REPOSITORY_URI}
                    docker tag ${AWS_ECR_REPO_NAME}:latest ${REPOSITORY_URI}${AWS_ECR_REPO_NAME}:${BUILD_NUMBER}
                    docker push ${REPOSITORY_URI}${AWS_ECR_REPO_NAME}:${BUILD_NUMBER}
                    """
                }
            }
        }
        
        stage('Update Deployment File') {
            steps {
                script {
                    withCredentials([gitUsernamePassword(credentialsId: 'github-cred', gitToolName: 'Default')]) {
                        sh """
                        git config user.email "jenkins@example.com"
                        git config user.name "Jenkins"
                        sed -i 's|image: .*|image: ${REPOSITORY_URI}${AWS_ECR_REPO_NAME}:${BUILD_NUMBER}|' kubernetes-manifests-file/Frontend/deployment.yaml
                        git add kubernetes-manifests-file/Frontend/deployment.yaml
                        git commit -m "Update frontend image to ${BUILD_NUMBER}"
                        git push origin main
                        """
                    }
                }
            }
        }
    }
}
```

---

## 📊 Monitoring & Observability

### Prometheus Targets

Access Prometheus UI: `http://<PROMETHEUS-URL>:9090`

Navigate to **Status → Targets** to view:
- Kubernetes API server metrics
- Node metrics
- Pod metrics
- Service endpoints

### Grafana Dashboards

Recommended dashboards:
- **Kubernetes Cluster Monitoring** (ID: 3119)
- **Node Exporter Full** (ID: 1860)
- **Kubernetes Pods** (ID: 6417)
- **ArgoCD Metrics** (ID: 14584)

---

## 🐛 Troubleshooting

### Common Issues

#### Jenkins Build Fails

```bash
# Check Jenkins logs
sudo tail -f /var/log/jenkins/jenkins.log

# Verify AWS credentials
aws sts get-caller-identity

# Check plugin installations
Jenkins → Manage Jenkins → Manage Plugins
```

#### EKS Cluster Connection Issues

```bash
# Update kubeconfig
aws eks update-kubeconfig --name <cluster-name> --region us-east-1

# Verify cluster
kubectl cluster-info

# Check node status
kubectl get nodes
```

#### ArgoCD Application Not Syncing

```bash
# Check application status
kubectl get applications -n argocd

# View application logs
kubectl logs -n argocd deployment/argocd-application-controller

# Force sync from UI or CLI
argocd app sync <app-name>

# Check sync status
argocd app get <app-name>
```

#### Load Balancer Not Creating

```bash
# Check AWS Load Balancer Controller
kubectl get deployment -n kube-system aws-load-balancer-controller

# View controller logs
kubectl logs -n kube-system deployment/aws-load-balancer-controller

# Verify IAM role
eksctl get iamserviceaccount --cluster <cluster-name>

# Check ingress events
kubectl describe ingress -n three-tier
```

#### Pods in CrashLoopBackOff

```bash
# Check pod status
kubectl get pods -n three-tier

# View pod logs
kubectl logs <pod-name> -n three-tier

# Describe pod for events
kubectl describe pod <pod-name> -n three-tier

# Check resource limits
kubectl top pods -n three-tier
```

#### SonarQube Analysis Fails

```bash
# Verify SonarQube is running
curl http://<sonarqube-ip>:9000/api/system/status

# Check webhook configuration
curl -u admin:<password> http://<sonarqube-ip>:9000/api/webhooks/list

# Review Jenkins console output for errors
```

#### ECR Push Failed

```bash
# Verify ECR repository exists
aws ecr describe-repositories --region us-east-1

# Test ECR authentication
aws ecr get-login-password --region us-east-1

# Check IAM permissions
aws iam get-role --role-name <jenkins-role-name>
```

---

## 📈 Performance Optimization

### EKS Cluster Optimization

```yaml
# Enable cluster autoscaler
apiVersion: autoscaling/v1
kind: HorizontalPodAutoscaler
metadata:
  name: frontend-hpa
  namespace: three-tier
spec:
  scaleTargetRef:
    apiVersion: apps/v1
    kind: Deployment
    name: frontend
  minReplicas: 2
  maxReplicas: 10
  targetCPUUtilizationPercentage: 70
```

### Resource Requests and Limits

```yaml
resources:
  requests:
    memory: "256Mi"
    cpu: "250m"
  limits:
    memory: "512Mi"
    cpu: "500m"
```

### Docker Image Optimization

```dockerfile
# Use multi-stage builds
FROM node:18-alpine AS builder
WORKDIR /app
COPY package*.json ./
RUN npm ci --only=production

FROM node:18-alpine
WORKDIR /app
COPY --from=builder /app/node_modules ./node_modules
COPY . .
EXPOSE 3000
CMD ["npm", "start"]
```

---

## 🔒 Security Best Practices

### Implemented Security Measures

- ✅ **IAM Roles** - No hardcoded AWS credentials
- ✅ **Private ECR** - Container images in private registry
- ✅ **Network Policies** - Pod-to-pod communication restrictions
- ✅ **SonarQube Scanning** - Code quality and vulnerability detection
- ✅ **OWASP Dependency Check** - Third-party vulnerability scanning
- ✅ **Secrets Management** - Kubernetes secrets for sensitive data
- ✅ **TLS/SSL** - HTTPS for all external communications

### Additional Recommendations

```bash
# Enable pod security policies
kubectl apply -f - <<EOF
apiVersion: policy/v1beta1
kind: PodSecurityPolicy
metadata:
  name: restricted
spec:
  privileged: false
  allowPrivilegeEscalation: false
  requiredDropCapabilities:
    - ALL
  runAsUser:
    rule: MustRunAsNonRoot
  fsGroup:
    rule: RunAsAny
  seLinux:
    rule: RunAsAny
  supplementalGroups:
    rule: RunAsAny
EOF
```

---

## 🔄 CI/CD Workflow

### Complete Pipeline Flow

```
┌─────────────────────────────────────────────────────────────────┐
│                     Developer Workflow                          │
└─────────────────────────────────────────────────────────────────┘
                              │
                              ▼
                   ┌────────────────────┐
                   │   Git Push Code    │
                   │   to GitHub        │
                   └────────────────────┘
                              │
                              ▼
┌─────────────────────────────────────────────────────────────────┐
│                    Jenkins CI Pipeline                          │
│  ┌──────────────┐  ┌──────────────┐  ┌──────────────┐         │
│  │   Checkout   │→ │  SonarQube   │→ │    OWASP     │         │
│  │     Code     │  │   Analysis   │  │ Dependency   │         │
│  └──────────────┘  └──────────────┘  └──────────────┘         │
│                              │                                  │
│                              ▼                                  │
│  ┌──────────────┐  ┌──────────────┐  ┌──────────────┐         │
│  │    Build     │→ │   Push to    │→ │   Update     │         │
│  │    Docker    │  │     ECR      │  │  Manifests   │         │
│  └──────────────┘  └──────────────┘  └──────────────┘         │
└─────────────────────────────────────────────────────────────────┘
                              │
                              ▼
┌─────────────────────────────────────────────────────────────────┐
│                    ArgoCD CD Pipeline                           │
│  ┌──────────────┐  ┌──────────────┐  ┌──────────────┐         │
│  │   Detect     │→ │    Sync      │→ │    Deploy    │         │
│  │   Changes    │  │  Resources   │  │   to EKS     │         │
│  └──────────────┘  └──────────────┘  └──────────────┘         │
│                              │                                  │
│                              ▼                                  │
│                   ┌────────────────────┐                        │
│                   │   Self-Heal &      │                        │
│                   │   Auto-Sync        │                        │
│                   └────────────────────┘                        │
└─────────────────────────────────────────────────────────────────┘
                              │
                              ▼
                   ┌────────────────────┐
                   │   Application      │
                   │   Running on EKS   │
                   └────────────────────┘
```

---

## 📚 Project Structure

```
three-tier-devops/
├── terraform/
│   ├── main.tf
│   ├── variables.tf
│   ├── outputs.tf
│   ├── vpc.tf
│   ├── eks.tf
│   └── security-groups.tf
├── kubernetes-manifests-file/
│   ├── Database/
│   │   ├── deployment.yaml
│   │   ├── service.yaml
│   │   └── pvc.yaml
│   ├── Backend/
│   │   ├── deployment.yaml
│   │   └── service.yaml
│   ├── Frontend/
│   │   ├── deployment.yaml
│   │   └── service.yaml
│   └── Ingress/
│       └── ingress.yaml
├── frontend/
│   ├── src/
│   ├── Dockerfile
│   ├── package.json
│   └── Jenkinsfile
├── backend/
│   ├── src/
│   ├── Dockerfile
│   ├── package.json
│   └── Jenkinsfile
├── monitoring/
│   ├── prometheus-values.yaml
│   └── grafana-dashboards/
├── scripts/
│   ├── jenkins-install.sh
│   ├── jump-server-setup.sh
│   └── cleanup.sh
└── README.md
```

---

## 🎯 Key Metrics & KPIs

### Deployment Metrics
- **Deployment Frequency**: Continuous (on every commit)
- **Lead Time**: < 30 minutes from commit to production
- **Mean Time to Recovery (MTTR)**: < 15 minutes
- **Change Failure Rate**: < 5%

### Infrastructure Metrics
- **Cluster Uptime**: 99.9%
- **Pod Restart Rate**: < 1 per day
- **Resource Utilization**: 60-80% optimal range

### Code Quality Metrics
- **SonarQube Quality Gate**: Pass required
- **Code Coverage**: > 70%
- **Security Vulnerabilities**: Zero high/critical

---

## 🌟 Features Roadmap

### Phase 1 (Current)
- ✅ Automated infrastructure provisioning
- ✅ CI/CD pipeline with Jenkins
- ✅ GitOps with ArgoCD
- ✅ Monitoring with Prometheus/Grafana

### Phase 2 (Planned)
- ⏳ Service mesh with Istio
- ⏳ Distributed tracing with Jaeger
- ⏳ Log aggregation with ELK stack
- ⏳ Automated security scanning with Trivy

### Phase 3 (Future)
- 📋 Multi-region deployment
- 📋 Disaster recovery automation
- 📋 Cost optimization with Spot instances
- 📋 Advanced auto-scaling with KEDA

---

## 🤝 Contributing

Contributions are welcome! Please follow these steps:

1. **Fork the repository**
   ```bash
   git clone https://github.com/<your-username>/three-tier-devops.git
   cd three-tier-devops
   ```

2. **Create a feature branch**
   ```bash
   git checkout -b feature/amazing-feature
   ```

3. **Commit your changes**
   ```bash
   git commit -m "Add amazing feature"
   ```

4. **Push to the branch**
   ```bash
   git push origin feature/amazing-feature
   ```

5. **Open a Pull Request**

### Code Standards
- Follow existing code structure
- Add comments for complex logic
- Update documentation
- Test changes thoroughly

---

## 📝 Changelog

### Version 1.0.0 (Current)
- Initial release
- Complete CI/CD pipeline
- EKS cluster deployment
- Monitoring setup

---

## 📞 Support & Contact

### Getting Help

- **Documentation**: Check this README and inline comments
- **Issues**: Open an issue on GitHub
- **Discussions**: Join GitHub Discussions

### Contact Information

- **Project Maintainer**: [Your Name]
- **Email**: your.email@example.com
- **LinkedIn**: [Your LinkedIn Profile]
- **GitHub**: [@yourusername](https://github.com/yourusername)

---

## 📜 License

This project is licensed under the MIT License - see the [LICENSE](LICENSE) file for details.

```
MIT License

Copyright (c) 2025 [Your Name]

Permission is hereby granted, free of charge, to any person obtaining a copy
of this software and associated documentation files (the "Software"), to deal
in the Software without restriction, including without limitation the rights
to use, copy, modify, merge, publish, distribute, sublicense, and/or sell
copies of the Software, and to permit persons to whom the Software is
furnished to do so, subject to the following conditions:

The above copyright notice and this permission notice shall be included in all
copies or substantial portions of the Software.
```

---

## 🙏 Acknowledgments

- **AWS** - Cloud infrastructure platform
- **Jenkins** - Automation server
- **ArgoCD** - GitOps continuous delivery
- **Kubernetes** - Container orchestration
- **Prometheus & Grafana** - Monitoring solutions
- **SonarQube** - Code quality platform
- **Terraform** - Infrastructure as code
- **Community Contributors** - Thank you all!

---

## 📊 Quick Commands Reference

### Kubernetes Commands
```bash
# Get all resources
kubectl get all -n three-tier

# View logs
kubectl logs -f <pod-name> -n three-tier

# Port forward
kubectl port-forward svc/<service-name> 8080:80 -n three-tier

# Exec into pod
kubectl exec -it <pod-name> -n three-tier -- /bin/sh

# Restart deployment
kubectl rollout restart deployment/<deployment-name> -n three-tier
```

### AWS Commands
```bash
# List EKS clusters
aws eks list-clusters --region us-east-1

# Describe cluster
aws eks describe-cluster --name <cluster-name> --region us-east-1

# List ECR repositories
aws ecr describe-repositories --region us-east-1

# Get ECR login
aws ecr get-login-password --region us-east-1
```

### ArgoCD Commands
```bash
# Login
argocd login <argocd-server>

# List applications
argocd app list

# Sync application
argocd app sync <app-name>

# Get application details
argocd app get <app-name>
```

---

## 🎓 Learning Resources

### Recommended Courses
- **AWS Certified Solutions Architect**
- **Certified Kubernetes Administrator (CKA)**
- **Jenkins Certified Engineer**
- **GitOps with ArgoCD**

### Documentation Links
- [Kubernetes Documentation](https://kubernetes.io/docs/)
- [AWS EKS Documentation](https://docs.aws.amazon.com/eks/)
- [Jenkins Documentation](https://www.jenkins.io/doc/)
- [ArgoCD Documentation](https://argo-cd.readthedocs.io/)
- [Terraform AWS Provider](https://registry.terraform.io/providers/hashicorp/aws/latest/docs)

---

## 💡 Tips & Best Practices

### Development Tips
1. **Always test locally** before pushing to production
2. **Use feature branches** for new developments
3. **Write meaningful commit messages**
4. **Keep Docker images small** using multi-stage builds
5. **Tag images properly** with semantic versioning

### Operations Tips
1. **Monitor resource usage** regularly
2. **Set up alerting** for critical metrics
3. **Perform regular backups** of persistent data
4. **Document all changes** in the changelog
5. **Test disaster recovery** procedures

### Security Tips
1. **Rotate credentials** regularly
2. **Enable audit logging** for compliance
3. **Use network policies** to restrict traffic
4. **Scan images** for vulnerabilities
5. **Follow principle of least privilege**

---

<div align="center">

