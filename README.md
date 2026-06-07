# nexus-monitoring

Prometheus + Grafana monitoring stack for the **Nexus** decentralized ecosystem.

This repository provides a ready-to-use observability setup for:

- `nexus-daemon` (mesh + blockchain + AI layers)
- Yggdrasil / xMesh / QNET nodes
- XCoin / QCoin blockchain nodes
- Host metrics
- Future AI agent metrics

## Quick Start

### 1. Start the monitoring stack

```bash
git clone https://github.com/digitaldesignerjazz/nexus-monitoring.git
cd nexus-monitoring

docker compose up -d
```

### 2. Access the services

| Service     | URL                          | Default Credentials      |
|-------------|------------------------------|--------------------------|
| Prometheus  | http://localhost:9090        | -                        |
| Grafana     | http://localhost:3000        | admin / nexus123         |
| Node Exporter | http://localhost:9100/metrics | -                      |
| Alertmanager | http://localhost:9093      | -                        |

### 3. Access Alertmanager

Alertmanager is available at: http://localhost:9093

It is pre-configured to route alerts. You can customize notification channels (Slack, email, PagerDuty, etc.) in `alertmanager/alertmanager.yml`.

### 4. Add Nexus Daemon metrics (future)

Once `nexus-daemon` exposes a Prometheus metrics endpoint (planned), the following alerts will become active:

- `NexusDaemonDown`
- `MeshLowPeerCount`
- `MeshHighLatency`
- `AISwarmLowAgents`
- `BlockchainSyncStalled`
- And more (see `prometheus/alerts/nexus.yml`)

## What's Included

- **Prometheus** — Time-series database + scraping + alerting rules
- **Alertmanager** — Alert routing and notifications (Slack ready)
- **Grafana** — Dashboards with provisioning
- **Node Exporter** — Host CPU, memory, disk, network metrics
- Pre-configured `prometheus.yml` ready for Nexus components
- Pre-defined alerting rules for Nexus infrastructure, mesh, blockchain, and AI swarm
- Docker Compose for easy local development

## Planned Metrics from Nexus

| Component       | Metrics Examples                              | Status     |
|-----------------|-----------------------------------------------|------------|
| nexus-daemon    | `nexus_mesh_peers`, `nexus_ai_agents`, `nexus_blockchain_height` | Planned |
| Mesh Layer      | Peer latency, message throughput, routing decisions | Planned |
| Blockchain      | Block height, tx rate, rune executions        | Planned |
| AI Swarm        | Agent count, emotional state, task completion | Planned |

## Directory Structure

```
nexus-monitoring/
├── docker-compose.yml
├── prometheus/
│   ├── prometheus.yml
│   └── alerts/
├── alertmanager/
├── grafana/
│   └── provisioning/
└── alerts/                  # Alertmanager rules (future)
└── README.md
```

## Integration with Nexus Ecosystem

This monitoring stack is designed to work alongside:

- [nexus-daemon](https://github.com/digitaldesignerjazz/nexus-daemon) — Core Rust daemon
- Mesh networking (Yggdrasil, xMesh, QNET)
- XCoin / QCoin blockchain
- AI agent swarms

## Next Steps / Roadmap

- [ ] Add example Grafana dashboard JSON for Nexus
- [ ] Implement Prometheus metrics endpoint in `nexus-daemon`
- [ ] Create alerting rules for mesh health, chain sync, AI swarm state
- [ ] Add Loki (logs) and Tempo (tracing) for full observability
- [ ] Production deployment examples (Kubernetes, systemd)

## Contributing

Pull requests and ideas for better observability of decentralized systems are very welcome!

---

**Part of the Nexus project** — Building intelligent, self-improving, privacy-first decentralized infrastructure.
