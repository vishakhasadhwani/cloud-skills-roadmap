# Month 3: Infrastructure as Code Across Environments

**Focus:** Terraform fundamentals, VMware/local providers, and module design.

---

## Terraform beginner path

- [HashiCorp Terraform tutorials](https://developer.hashicorp.com/terraform/tutorials)
- [Terraform – Automate AWS (FreeCodeCamp)](https://www.youtube.com/watch?v=SLB_c_ayRMo)
- [KodeKloud Terraform course](https://www.youtube.com/watch?v=nvNqfgojocs)

---

## Terraform for VMware / local

- [Terraform VMware (vSphere) provider](https://registry.terraform.io/providers/hashicorp/vsphere/latest/docs)
- [Terraform + Docker (local)](https://developer.hashicorp.com/terraform/tutorials/docker-get-started)

---

## Module design

- [Terraform modules](https://developer.hashicorp.com/terraform/language/modules)
- [Building reusable modules](https://www.terraform.io/docs/language/modules/develop/index.html)

---

## Cost comparison

- [Cloud cost comparison](https://www.cloudzero.com/blog/cloud-cost-comparison)
- [FinOps Foundation](https://www.finops.org/)

---

## Repos to review

- [DevOps Master Class](https://github.com/in28minutes/devops-master-class) – Terraform, K8s, IaC
- [Terraform AWS provider](https://github.com/hashicorp/terraform-provider-aws) – examples & patterns
- [GCP Terraform examples](https://github.com/GoogleCloudPlatform/terraform-google-examples)

---

#### Project: Hybrid Infrastructure with Terraform

**Detailed Steps:**

1. **Setup Terraform workspace:**
   ```
   project/
   ├── modules/
   │   ├── network/
   │   ├── compute/
   │   └── storage/
   ├── environments/
   │   ├── dev/
   │   └── prod/
   ```
2. **Configure providers:** Create `providers.tf` with AWS, Azure, and local providers
3. **Create variables:** Define `variables.tf` with cloud-agnostic naming
4. **Build reusable modules:** Create modules for network, compute, storage
5. **Local VM with libvirt:** Use libvirt provider to manage local VMs
6. **AWS deployment:** Same module deploys EC2 with VPC, security groups
7. **Azure deployment:** Same module deploys Azure VM with resource group
8. **State management:** Configure remote backend (S3/Azure Storage)
9. **Test deployments:** `terraform plan`, `terraform apply` for each environment
10. **Cleanup:** `terraform destroy` to remove resources and avoid costs

**GitHub Repositories:**

| Repository | Description |
|------------|-------------|
| [hashicorp/terraform](https://github.com/hashicorp/terraform) | Official Terraform |
| [stacksimplify/terraform-on-azure-cloud](https://github.com/stacksimplify/terraform-on-azure-cloud) | 25 Azure demos |
| [hajowieland/terraform-kubernetes-multi-cloud](https://github.com/hajowieland/terraform-kubernetes-multi-cloud) | Multi-cloud K8s |
| [ChinmayGajul/Multi-Cloud-Deployment-with-Terraform](https://github.com/ChinmayGajul/Multi-Cloud-Deployment-with-Terraform) | Multi-cloud deployment |
| [alfonsof/terraform-azure-examples](https://github.com/alfonsof/terraform-azure-examples) | Azure examples |

**📺 YouTube Videos:**

- HashiCorp - "Introduction to Terraform"
- freeCodeCamp - "Terraform Course"
- TechWorld with Nana - "Terraform Tutorial"

**Topics to Cover:**

- [ ] Terraform HCL syntax and structure
- [ ] State management (local vs remote backends)
- [ ] Module development and versioning
- [ ] Provider abstraction patterns
- [ ] Workspaces for multi-environment management

---

**Next:** [Month 04 – Configuration + Automation](../Month_04_Configuration_Automation/)
