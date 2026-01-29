# Month 7: Project 2 – Infrastructure Monitoring (Works Everywhere)

**Focus:** Prometheus, Grafana, exporters, and observability. Build a monitoring stack you can run on-prem or in the cloud.

---

## Prometheus

- [Prometheus installation](https://prometheus.io/docs/prometheus/latest/installation/)
- [Prometheus Docker](https://hub.docker.com/r/prom/prometheus)
- [Prometheus tutorial](https://www.youtube.com/watch?v=h4Sl21AKiDg)

---

## Grafana

- [Grafana getting started](https://grafana.com/docs/grafana/latest/getting-started/)
- [Grafana dashboard tutorial](https://www.youtube.com/watch?v=QNt2HNHNqAE)
- [Grafana + Prometheus](https://prometheus.io/docs/visualization/grafana/)

---

## Exporters

- [Node Exporter](https://github.com/prometheus/node_exporter)
- [Prometheus exporters](https://prometheus.io/docs/instrumentation/exporters/)
- [Default port allocations](https://github.com/prometheus/prometheus/wiki/Default-port-allocations)

---

## Observability

- [Observability best practices (CNCF)](https://www.cncf.io/blog/2021/08/26/observability-best-practices/)
- [Monitoring distributed systems (Google SRE)](https://sre.google/sre-book/monitoring-distributed-systems/)

---

## Project 2: Infrastructure Monitoring (Works Everywhere)

**Detailed Steps:**

1. **Create docker-compose.yml:** Define prometheus, grafana, node-exporter services
2. **Configure Prometheus:** Create `prometheus.yml` with scrape configs
3. **Add node-exporter:** Expose host metrics (CPU, memory, disk, network)
4. **Start stack:**
   ```bash
   docker-compose up -d
   ```
5. **Access Prometheus:** http://localhost:9090, verify targets are up
6. **Configure Grafana:** http://localhost:3000, add Prometheus data source
7. **Import dashboards:** Node Exporter Full (ID: 1860), Docker containers
8. **Create custom dashboard:** Build panels for your specific metrics
9. **Setup alerts:** Configure AlertManager for Slack/email notifications
10. **Deploy to cloud:** Same stack works on any cloud VM

**GitHub Repositories:**

| Repository | Description |
|------------|-------------|
| [prometheus/prometheus](https://github.com/prometheus/prometheus) | Monitoring system |
| [grafana/grafana](https://github.com/grafana/grafana) | Visualization platform |
| [samber/workshop-prometheus-grafana](https://github.com/samber/workshop-prometheus-grafana) | Hands-on workshop |
| [vegasbrianc/github-monitoring](https://github.com/vegasbrianc/github-monitoring) | Docker + Prometheus + Grafana |
| [Einsteinish/Docker-Compose-Prometheus-and-Grafana](https://github.com/Einsteinish/Docker-Compose-Prometheus-and-Grafana) | Complete stack |

**📺 YouTube Videos:**

- TechWorld with Nana - "Prometheus Monitoring"
- DevOps Toolkit - "Prometheus and Grafana Tutorial"

**Topics to Cover:**

- [ ] PromQL query language
- [ ] Metrics types (counter, gauge, histogram)
- [ ] Alerting rules and notification channels
- [ ] Dashboard design principles


**Next:** [Month 08 – CI/CD Pipeline](../Month_08_CICD_Pipeline/)
