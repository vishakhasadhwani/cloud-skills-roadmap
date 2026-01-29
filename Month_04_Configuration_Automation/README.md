# Month 4: Configuration + Automation (Cloud-First)

**Focus:** Cloud-specific configuration (AWS, Azure, GCP), networking fundamentals, and a small automation project. Ansible is kept to basics and used for the project only.

---

## Cloud-specific configuration

### AWS

- [Parameter Store](https://docs.aws.amazon.com/systems-manager/latest/userguide/systems-manager-parameter-store.html) – config & secrets
- [Secrets Manager](https://docs.aws.amazon.com/secretsmanager/) – rotation, DB creds

### Azure

- [App Configuration](https://learn.microsoft.com/en-us/azure/azure-app-configuration/) – app settings, feature flags
- [Key Vault](https://learn.microsoft.com/en-us/azure/key-vault/) – secrets, certs, keys

### GCP

- [Secret Manager](https://cloud.google.com/secret-manager/docs) – API keys, passwords, certs

---

## Networking fundamentals

- [Computer networking course](https://www.youtube.com/watch?v=qiQR5rTSshw)
- [Practical Networking – how data moves](https://www.practicalnetworking.net/index/networking-fundamentals-how-data-moves-through-the-internet/)
- [Subnetting made easy](https://www.youtube.com/watch?v=s_Ntt6eTn94)
- [UFW firewall (DigitalOcean)](https://www.digitalocean.com/community/tutorials/ufw-essentials-common-firewall-rules-and-commands)

---

## Ansible fundamentals (for the project)

- [Ansible getting started](https://docs.ansible.com/ansible/latest/getting_started/index.html)
- [Ansible for beginners (Jeff Geerling)](https://www.youtube.com/watch?v=goclfp6a2IQ)

---

## Mini project: Automate VM configuration

Use Ansible to automate VM setup (packages, config, users). Study these, then build your own.

- [Ansible for DevOps (Geerling)](https://github.com/geerlingguy/ansible-for-devops)
- [Ansible playbook examples](https://github.com/ansible/ansible-examples)

---

## Repos to review

- [Ansible for DevOps](https://github.com/geerlingguy/ansible-for-devops)
- [Ansible playbook examples](https://github.com/ansible/ansible-examples)

---

**Next:** [Month 05 – Container Orchestration](../Month_05_Container_Orchestration/)
