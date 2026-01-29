# Month 5: Container Orchestration Beyond Kubernetes

**Focus:** Docker Compose, Docker Swarm, and HashiCorp Nomad.

---

## Docker Compose

- [Docker Compose getting started](https://docs.docker.com/compose/gettingstarted/)
- [Docker Compose for beginners](https://www.youtube.com/watch?v=HG6yIjZapSA)

---

## Docker Swarm

- [Docker Swarm mode](https://docs.docker.com/engine/swarm/)
- [Docker Swarm tutorial](https://www.youtube.com/watch?v=Tm0Q5zr3FL4)

---

## Nomad

- [HashiCorp Nomad intro](https://www.nomadproject.io/intro)
- [Nomad tutorials](https://developer.hashicorp.com/nomad/tutorials)

---

## Kubernetes deep dive (optional)

- [Kubernetes tutorials](https://kubernetes.io/docs/tutorials/)
- [Kubernetes the Hard Way](https://github.com/kelseyhightower/kubernetes-the-hard-way)

---

## Repos to review

- [Ansible for Kubernetes](https://github.com/geerlingguy/ansible-for-kubernetes) – K8s + config automation
- [DevOps Master Class](https://github.com/in28minutes/devops-master-class) – orchestration examples

---
#### Project: Deploy Same App on Multiple Orchestrators

**Part 1: Docker Swarm** (Learn in 2 hours vs 2 weeks for K8s)

```bash
# Initialize Swarm
docker swarm init

# Deploy stack
docker stack deploy -c docker-compose.yml myapp

# Scale services
docker service scale myapp_web=5

# Monitor
docker service ls
docker service ps myapp_web
```

**Part 2: HashiCorp Nomad**

```bash
# Install Nomad
# Download from HashiCorp, add to PATH

# Start dev mode
nomad agent -dev

# Create job file (HCL)
# Run job
nomad job run myapp.nomad

# Access UI
# http://localhost:4646
```

**GitHub Repositories:**

| Repository | Description |
|------------|-------------|
| [dockersamples/example-voting-app](https://github.com/dockersamples/example-voting-app) | Multi-container app |
| [hashicorp/nomad](https://github.com/hashicorp/nomad) | Workload orchestrator |

**Topics to Cover:**

- [ ] Orchestrator comparison (K8s vs Swarm vs Nomad)
- [ ] Service discovery and load balancing
- [ ] Rolling updates and deployments
- [ ] Resource constraints and scheduling

---

**Next:** [Month 06 – RAG Pipeline](../Month_06_RAG_Pipeline/)
