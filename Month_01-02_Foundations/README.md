# Month 1–2: Foundations

**Focus:** Understanding real infrastructure, tool setup, first hybrid project, and multi-cloud Kubernetes.

---

## Week 1–2: Understanding Real Infrastructure

### Hybrid Infrastructure

- [Hybrid Cloud Architecture (AWS)](https://aws.amazon.com/hybrid/)
- [Multi-cloud strategy (GCP)](https://cloud.google.com/learn/what-is-multicloud)

### On-Prem (VMs, bare metal)

- [VirtualBox docs](https://www.virtualbox.org/wiki/Documentation)
- [VMware learning](https://www.vmware.com/learning.html)
- [Virtualization intro (Red Hat)](https://www.redhat.com/en/topics/virtualization/what-is-virtualization)

### Networking refresher

- [Networking fundamentals (Nana)](https://www.youtube.com/watch?v=IPvYjXCsTg8)
- [TCP/IP basics (Cloudflare)](https://www.cloudflare.com/learning/network-layer/what-is-a-protocol/)
- [Subnetting and VLANs](https://www.practicalnetworking.net/)

### Cloud provider intro

- [AWS Getting Started](https://aws.amazon.com/getting-started/)
- [Azure Fundamentals](https://learn.microsoft.com/en-us/training/paths/azure-fundamentals/)
- [Google Cloud training](https://cloud.google.com/training/)
- [Oracle My Learn](https://www.oracle.com/education/training/)

---

## Tool Setup

### Docker

- [Docker install](https://docs.docker.com/get-docker/)
- [Docker for beginners (Nana)](https://www.youtube.com/watch?v=3c-iBn73dDE)
- [FreeCodeCamp Docker course](https://www.youtube.com/watch?v=fqMOX6JJhGo)

### Terraform

- [Terraform tutorials](https://developer.hashicorp.com/terraform/tutorials)
- [Terraform beginner (FreeCodeCamp)](https://www.youtube.com/watch?v=SLB_c_ayRMo)
- [Abhishek – Terraform Zero to Hero](https://www.youtube.com/playlist?list=PLdpzxOOAlwvI0O4PeKVV1-yJoX2AqIWuf)

### Vagrant + VirtualBox

- [Vagrant getting started](https://developer.hashicorp.com/vagrant/tutorials)
- [Vagrant tutorial](https://www.youtube.com/watch?v=vBreXjkizgo)

### VS Code + Copilot

- [VS Code setup](https://code.visualstudio.com/docs/setup/setup-overview)
- [GitHub Copilot](https://docs.github.com/en/copilot)

---

## Week 3–4: First Hybrid Project (Local → Cloud)

**Detailed Steps:**

1. **Install VirtualBox:** Download from [virtualbox.org](https://virtualbox.org), install for your OS (Windows/Mac/Linux)
2. **Install Vagrant:** Download from [vagrantup.com](https://vagrantup.com), verify with `vagrant --version`
3. **Create project directory:**
   ```bash
   mkdir ~/vagrant-projects && cd ~/vagrant-projects
   ```
4. **Initialize Ubuntu VM:**
   ```bash
   vagrant init ubuntu/jammy64
   ```
5. **Configure resources:** Edit Vagrantfile to set `vb.memory = '2048'` and `vb.cpus = '2'`
6. **Start the VM:** `vagrant up` (first run downloads the box image)
7. **SSH into the VM:** `vagrant ssh`
8. **Install Docker inside VM:**
   ```bash
   sudo apt update && sudo apt install docker.io -y
   ```
9. **Install Terraform:** Follow HashiCorp's official install guide for your OS
10. **Setup VS Code with extensions:** Remote-SSH, Docker, HashiCorp Terraform, GitHub Copilot

**GitHub Repositories:**

| Repository | Description |
|------------|-------------|
| [hashicorp/vagrant](https://github.com/hashicorp/vagrant) | Official Vagrant repository |
| [docker/docker-ce](https://github.com/docker/docker-ce) | Docker Community Edition |
| [hashicorp/terraform](https://github.com/hashicorp/terraform) | Infrastructure as Code tool |

**📺 YouTube Videos:**

- [NetworkChuck - "you need to learn Vagrant RIGHT NOW"](https://www.youtube.com/results?search_query=networkchuck+vagrant)
- [TechWorld with Nana - "Docker Tutorial for Beginners"](https://www.youtube.com/results?search_query=techworld+nana+docker+beginners)
- [freeCodeCamp - "Terraform Course - Automate Your AWS Cloud Infrastructure"](https://www.youtube.com/results?search_query=freecodecamp+terraform+course)

**Topics to Cover:**

- [ ] Virtualization concepts (hypervisors, VMs vs containers)
- [ ] Networking basics (IP addressing, subnets, ports, firewalls)
- [ ] Linux fundamentals (file system, permissions, systemd)
- [ ] SSH key management and secure connections
- [ ] Hybrid infrastructure concepts (on-prem + cloud)

---

### Week 3-4: First Real Project (Hybrid Thinking)

#### Project: Deploy App Locally, Then Migrate to Cloud

**Detailed Steps:**

1. **Create Ubuntu VM with VirtualBox/Vagrant:** Use Vagrantfile with `ubuntu/jammy64` box
2. **Install Nginx on VM:**
   ```bash
   sudo apt update && sudo apt install nginx -y
   ```
3. **Create simple HTML app:** Create `index.html` in `/var/www/html` with your content
4. **Configure Nginx:** Edit `/etc/nginx/sites-available/default`, set root and server_name
5. **Test locally:** Access via VM IP in browser, verify app works
6. **Containerize with Docker:** Create Dockerfile:
   ```dockerfile
   FROM nginx:alpine
   COPY index.html /usr/share/nginx/html/
   ```
7. **Build Docker image:**
   ```bash
   docker build -t my-app:v1 .
   ```
8. **Run container locally:**
   ```bash
   docker run -d -p 8080:80 my-app:v1
   ```
9. **Push to Docker Hub:**
   ```bash
   docker tag my-app:v1 username/my-app:v1 && docker push username/my-app:v1
   ```
10. **Deploy to cloud (AWS/Azure/GCP/OCI):** Pull image and run on cloud VM or container service

**GitHub Repositories:**

| Repository | Description |
|------------|-------------|
| [nginx/docker-nginx](https://github.com/nginx/docker-nginx) | Official NGINX Dockerfiles |
| [docker/awesome-compose](https://github.com/docker/awesome-compose) | Docker Compose samples |
| [KyleAMathews/docker-nginx](https://github.com/KyleAMathews/docker-nginx) | Easy static site hosting |

**📺 YouTube Videos:**

- Fireship - "Docker in 100 Seconds"
- Traversy Media - "Docker Tutorial for Beginners"
- TechWorld with Nana - "Docker Compose Tutorial"

**Topics to Cover:**

- [ ] Docker fundamentals (images, containers, volumes, networks)
- [ ] Dockerfile best practices (multi-stage builds, layer optimization)
- [ ] Container registries (Docker Hub, ECR, ACR, GCR)
- [ ] Lift-and-shift migration strategies
- [ ] Web server configuration (Nginx, Apache)

---

### Week 5-8: Multi-Cloud Reality Project

#### Project: Same App Deployed Three Ways

**Part 1: Local Kubernetes with K3s**

```bash
# Install K3s
curl -sfL https://get.k3s.io | sh -

# Verify installation
sudo k3s kubectl get nodes

# Create deployment YAML
# Create service YAML
# Apply configurations
kubectl apply -f deployment.yaml -f service.yaml

# Access the app
curl http://localhost:<nodeport>
```

**Part 2: AWS ECS or EKS**

1. Setup AWS CLI: `aws configure` with your credentials
2. Push image to ECR: Create ECR repo, authenticate Docker, push image
3. Create ECS cluster: Use AWS Console or Terraform to create Fargate cluster
4. Define task definition: Specify container image, CPU, memory requirements
5. Create service: Deploy task with desired count and load balancer

**Part 2: AWS ECS or EKS**

1. Setup AWS CLI: `aws configure` with your credentials
2. Push image to ECR: Create ECR repo, authenticate Docker, push image
3. Create ECS cluster: Use AWS Console or Terraform to create Fargate cluster
4. Define task definition: Specify container image, CPU, memory requirements
5. Create service: Deploy task with desired count and load balancer

**Part 3: Alternative Clouds**

<details>
<summary><strong>🔵 Google Cloud Platform (GKE)</strong></summary>

1. **Create GCP account:** Sign up at [cloud.google.com](https://cloud.google.com) - get $300 free credits for 90 days
2. **Install gcloud CLI:**
   ```bash
   # Install Google Cloud SDK
   curl https://sdk.cloud.google.com | bash
   gcloud init
   ```
3. **Create GKE cluster:**
   ```bash
   # Enable GKE API
   gcloud services enable container.googleapis.com
   
   # Create Autopilot cluster (pay per pod, simpler)
   gcloud container clusters create-auto my-cluster \
     --region=us-central1
   
   # OR create Standard cluster (more control)
   gcloud container clusters create my-cluster \
     --zone=us-central1-a \
     --num-nodes=2 \
     --machine-type=e2-medium
   ```
4. **Connect kubectl:**
   ```bash
   gcloud container clusters get-credentials my-cluster --zone=us-central1-a
   ```
5. **Deploy your app:**
   ```bash
   kubectl apply -f your-deployment.yaml
   ```
6. **Cost:** ~$70/month for 2-node e2-medium cluster (Autopilot can be cheaper for small workloads)

**GCP Docs:** [cloud.google.com/kubernetes-engine/docs](https://cloud.google.com/kubernetes-engine/docs)

</details>

<details>
<summary><strong>🟠 Oracle Cloud Infrastructure (OKE)</strong></summary>

1. **Create OCI account:** Sign up at [oracle.com/cloud](https://www.oracle.com/cloud) - **Always Free Tier** includes:
   - 2 AMD VMs (1 OCPU, 1GB RAM each) - forever free
   - 4 ARM Ampere A1 cores + 24GB RAM - forever free
   - 200GB block storage - forever free
2. **Install OCI CLI:**
   ```bash
   bash -c "$(curl -L https://raw.githubusercontent.com/oracle/oci-cli/master/scripts/install/install.sh)"
   oci setup config
   ```
3. **Create OKE cluster (Console or CLI):**
   ```bash
   # Using OCI Console is recommended for first-time setup
   # Navigate to: Developer Services > Kubernetes Clusters > Create Cluster
   # Select "Quick Create" for simplest setup
   ```
4. **Connect kubectl:**
   ```bash
   # Get kubeconfig from OCI Console or CLI
   oci ce cluster create-kubeconfig \
     --cluster-id <cluster-ocid> \
     --file $HOME/.kube/config \
     --region us-ashburn-1
   ```
5. **Deploy your app:**
   ```bash
   kubectl apply -f your-deployment.yaml
   ```
6. **Cost:** Can be **$0** using Always Free ARM instances! Paid clusters start ~$0.10/hour for control plane

**OCI Docs:** [docs.oracle.com/en-us/iaas/Content/ContEng](https://docs.oracle.com/en-us/iaas/Content/ContEng/home.htm)

</details>

<details>
<summary><strong>🔷 Microsoft Azure (AKS)</strong></summary>

1. **Create Azure account:** Sign up at [azure.microsoft.com](https://azure.microsoft.com) - get $200 free credits for 30 days
2. **Install Azure CLI:**
   ```bash
   # macOS
   brew install azure-cli
   
   # Windows
   winget install Microsoft.AzureCLI
   
   # Linux
   curl -sL https://aka.ms/InstallAzureCLIDeb | sudo bash
   
   az login
   ```
3. **Create resource group and AKS cluster:**
   ```bash
   # Create resource group
   az group create --name myResourceGroup --location eastus
   
   # Create AKS cluster
   az aks create \
     --resource-group myResourceGroup \
     --name myAKSCluster \
     --node-count 2 \
     --node-vm-size Standard_B2s \
     --enable-managed-identity \
     --generate-ssh-keys
   ```
4. **Connect kubectl:**
   ```bash
   az aks get-credentials --resource-group myResourceGroup --name myAKSCluster
   ```
5. **Deploy your app:**
   ```bash
   kubectl apply -f your-deployment.yaml
   ```
6. **Cost:** ~$60/month for 2-node B2s cluster (control plane is FREE on AKS!)

**Azure Docs:** [learn.microsoft.com/azure/aks](https://learn.microsoft.com/en-us/azure/aks/)

</details>

<details>
<summary><strong>🟢 DigitalOcean (DOKS)</strong></summary>

1. **Create DigitalOcean account:** Sign up at [digitalocean.com](https://www.digitalocean.com) - use referral links for $200 free credits
2. **Install doctl CLI:**
   ```bash
   # macOS
   brew install doctl
   
   # Authenticate
   doctl auth init
   ```
3. **Create DOKS cluster:**
   ```bash
   doctl kubernetes cluster create my-cluster \
     --region nyc1 \
     --node-pool "name=default;size=s-2vcpu-2gb;count=2"
   ```
4. **Connect kubectl:**
   ```bash
   doctl kubernetes cluster kubeconfig save my-cluster
   ```
5. **Deploy your app:**
   ```bash
   kubectl apply -f your-deployment.yaml
   ```
6. **Cost:** ~$12/month for basic 2-node cluster (cheapest managed K8s!)

**DO Docs:** [docs.digitalocean.com/products/kubernetes](https://docs.digitalocean.com/products/kubernetes/)

</details>

**💰 Full Cost Comparison:**

| Provider | Control Plane | 2-Node Cluster | Free Tier |
|----------|---------------|----------------|-----------|
| Local K3s | $0 | $0 | ✅ Forever |
| OCI (OKE) | ~$7/month | **$0** (ARM free tier) | ✅ Always Free |
| DigitalOcean | Included | ~$12/month | $200 credits |
| Azure (AKS) | **FREE** | ~$60/month | $200 credits |
| GCP (GKE) | ~$72/month | ~$70/month | $300 credits |
| AWS (EKS) | $72/month | ~$80/month | Limited |

**GitHub Repositories:**

| Repository | Description |
|------------|-------------|
| [k3s-io/k3s](https://github.com/k3s-io/k3s) | Lightweight Kubernetes |
| [oleg-nefedov/k3s-tutorial](https://github.com/oleg-nefedov/k3s-tutorial) | Comprehensive K3s guide |
| [kubernetes/examples](https://github.com/kubernetes/examples) | K8s example applications |
| [digitalocean/Kubernetes-Starter-Kit-Developers](https://github.com/digitalocean/Kubernetes-Starter-Kit-Developers) | DO K8s starter kit |

**📺 YouTube Videos:**

- TechWorld with Nana - "Kubernetes Tutorial for Beginners"
- NetworkChuck - "you need to learn Kubernetes RIGHT NOW"
- Rancher - "Getting Started with K3s"
- freeCodeCamp - "Kubernetes Course - Full Beginners Tutorial"

**Topics to Cover:**

- [ ] Kubernetes architecture (nodes, pods, services, deployments)
- [ ] YAML manifest structure and best practices
- [ ] Container orchestration concepts
- [ ] Cloud cost comparison and optimization
- [ ] Multi-cloud deployment strategies


**GitHub Repositories:**

| Repository | Description |
|------------|-------------|
| [k3s-io/k3s](https://github.com/k3s-io/k3s) | Lightweight Kubernetes |
| [oleg-nefedov/k3s-tutorial](https://github.com/oleg-nefedov/k3s-tutorial) | Comprehensive K3s guide |
| [kubernetes/examples](https://github.com/kubernetes/examples) | K8s example applications |
| [digitalocean/Kubernetes-Starter-Kit-Developers](https://github.com/digitalocean/Kubernetes-Starter-Kit-Developers) | DO K8s starter kit |

**📺 YouTube Videos:**

- TechWorld with Nana - "Kubernetes Tutorial for Beginners"
- NetworkChuck - "you need to learn Kubernetes RIGHT NOW"
- Rancher - "Getting Started with K3s"
- freeCodeCamp - "Kubernetes Course - Full Beginners Tutorial"

**Topics to Cover:**

- [ ] Kubernetes architecture (nodes, pods, services, deployments)
- [ ] YAML manifest structure and best practices
- [ ] Container orchestration concepts
- [ ] Cloud cost comparison and optimization
- [ ] Multi-cloud deployment strategies

---


## Repos to review

- [DevOps Master Class](https://github.com/in28minutes/devops-master-class) – broad DevOps foundations
- [Awesome sysadmin](https://github.com/awesome-foss/awesome-sysadmin) – infra & ops tooling

---

**Next:** [Month 03 – Infrastructure as Code](../Month_03_Infrastructure_as_Code/)
