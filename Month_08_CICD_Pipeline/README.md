# Month 8: Project 3 – CI/CD Pipeline (Multi-Cloud Deployments)

**Focus:** GitHub Actions, Docker builds, Trivy security scanning, and deployment platforms. Build a pipeline that deploys across clouds.

---

## GitHub Actions

- [GitHub Actions docs](https://docs.github.com/en/actions)
- [GitHub Actions tutorial](https://www.youtube.com/watch?v=R8_veQiYBjI)
- [Abhishek – GitHub Actions](https://youtu.be/K3RqgDPCjYs?si=IkxA2Z_t1nme6btY)

---

## Docker build pipeline

- [Docker CI/CD with GitHub Actions](https://docs.docker.com/build/ci/github-actions/)
- [Building Docker images in CI](https://youtu.be/7I6tHw68DMQ?si=5aJ_OKKWNl6CJxdY)

---

## Trivy (security scanning)

- [Trivy docs](https://aquasecurity.github.io/trivy/)
- [Trivy GitHub Action](https://github.com/aquasecurity/trivy-action)
- [Container security scanning](https://youtu.be/gLJdrXPn0ns?si=7upXadywa_S6p4g7)

---

## Deployment platforms

- [Fly.io](https://fly.io/docs/)
- [Render](https://render.com/docs)
- [DigitalOcean App Platform](https://docs.digitalocean.com/products/app-platform/)

---

## Repos to review

- [Awesome GitHub Actions](https://github.com/sdras/awesome-actions)
- [Jenkins pipeline examples](https://github.com/jenkinsci/pipeline-examples)
- [GitLab CI examples](https://docs.gitlab.com/ee/ci/examples/)
- [Ultimate DevOps project (Abhishek, Udemy)](https://www.udemy.com/course/ultimate-devops-project-with-resume-preparation/)

### Project Steps:

**Detailed Steps:**

1. **Create GitHub repository:** Initialize with README, .gitignore
2. **Add Dockerfile:** Multi-stage build for optimized images
3. **Create workflow directory:**
   ```bash
   mkdir -p .github/workflows
   ```
4. **Write CI workflow:** `ci.yml` with build, test, lint jobs
5. **Add security scanning:** Trivy for container vulnerability scanning
6. **Setup Docker Hub secrets:** Add `DOCKER_USERNAME`, `DOCKER_PASSWORD` in GitHub
7. **Add push step:** Push image to registry on main branch
8. **Add deployment targets:** Fly.io, Railway, Render, or DigitalOcean
9. **Create staging/prod environments:** Separate deployment jobs with approvals
10. **Test the pipeline:** Push changes, verify workflow runs successfully

**Sample GitHub Actions Workflow:**

```yaml
name: CI/CD Pipeline
on:
  push:
    branches: [main]

jobs:
  build-test-push:
    runs-on: ubuntu-latest
    steps:
      - uses: actions/checkout@v4
      - uses: docker/setup-buildx-action@v3
      - uses: docker/login-action@v2
        with:
          username: ${{ secrets.DOCKER_USERNAME }}
          password: ${{ secrets.DOCKER_PASSWORD }}
      - run: docker build -t app:${{ github.sha }} .
      - run: docker run app:${{ github.sha }} npm test
      - uses: aquasecurity/trivy-action@master
        with:
          image-ref: 'app:${{ github.sha }}'
      - run: docker push app:${{ github.sha }}
```

**GitHub Repositories:**

| Repository | Description |
|------------|-------------|
| [actions/starter-workflows](https://github.com/actions/starter-workflows) | GitHub Actions templates |
| [docker/build-push-action](https://github.com/docker/build-push-action) | Build and push Docker images |
| [aquasecurity/trivy-action](https://github.com/aquasecurity/trivy-action) | Security scanning |

**📺 YouTube Videos:**

- GitHub - "GitHub Actions Tutorial"
- TechWorld with Nana - "Complete CI/CD Tutorial"
- Fireship - "GitHub Actions in 100 Seconds"

**Topics to Cover:**

- [ ] GitHub Actions workflow syntax
- [ ] Secrets and environment variables
- [ ] Container security scanning
- [ ] Multi-environment deployment strategies


---

**Next:** [Month 09 – Hybrid + Migration Interviews](../Month_09_Hybrid_Migration_Interviews/)
