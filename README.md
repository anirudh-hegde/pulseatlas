# PulseAtlas: Enterprise-Grade SRE Monitoring Dashboard

A complete, enterprise-grade health monitoring and SRE metrics dashboard for tracking services, APIs, and microservices with professional-grade SLO tracking, Prometheus integration, and Grafana visualization.

---

## Table of Contents

- [Features](#features)
- [Quick Start](#quick-start)
- [Local Development](#local-development)
- [Production Deployment](#production-deployment)
- [Architecture](#architecture)
- [Tech Stack](#tech-stack)
- [SRE Metrics](#sre-metrics)
- [API Endpoints](#api-endpoints)
- [Grafana Integration](#grafana-integration)
- [Troubleshooting](#troubleshooting)
- [Contributing](#contributing)

---

## Features

- ✅ **Real-time SRE Dashboard**: Color-coded health indicators with all key metrics visible on a single pane of glass
- ✅ **Production-Grade Metrics**: Tracks P95/P99 latencies, Apdex score, error rates, and uptime
- ✅ **Professional Visualization**: Pre-built Grafana dashboards for deep-diving into time-series data
- ✅ **Prometheus Integration**: Automatically exports and scrapes metrics for historical analysis and alerting
- ✅ **Smart Alerts**: Multi-signal alerting logic (status + Apdex + error rate) with Redis-backed deduplication
- ✅ **Kafka Event Streaming**: Publishes health check results to Kafka topics for real-time, event-driven integrations
- ✅ **Type-Safe Code**: Built with TypeScript frontend and Python 3.11 backend with Pydantic
- ✅ **Docker Ready**: Deploy the entire 9-service stack with a single command
- ✅ **Embedded Grafana**: View service dashboards directly from the main UI

---

## What It Does

**PulseAtlas** is an all-in-one monitoring solution that:

1. **Monitors Services**: Performs periodic, configurable HTTP health checks on any URL
2. **Calculates SRE Metrics**: Computes P95/P99 latencies, Apdex scores, error rates, uptime percentages
3. **Displays a Real-Time Dashboard**: Shows all metrics in a sleek, dark-themed UI that auto-refreshes
4. **Stores Time-Series Data**: Uses Prometheus for robust historical analysis
5. **Visualizes Trends**: Integrates with Grafana for beautiful pre-configured dashboards
6. **Triggers Smart Alerts**: Sends alerts via Slack webhooks with intelligent deduplication
7. **Streams Health Events**: Pushes check results to Kafka for consumption by other services

---

## Quick Start

### ⚡ With Docker (Recommended - 2 minutes)

```bash
# 1. Clone the repository
git clone https://github.com/MeghVyas3132/Metrics-Health-Tracker.git
cd Metrics-Health-Tracker

# 2. Start all services
docker compose up --build -d

3. Access the dashboard
Frontend:    http://localhost:3000
Grafana:     http://localhost:3001 (admin/admin)
API Docs:    http://localhost:8000/docs
Prometheus:  http://localhost:9090
```

**Verify services are running:**
```bash
docker compose ps
```

# Check backend metrics endpoint
```bash
curl http://localhost:8000/metrics
```

### Create a service via API

```bash
# Check backend metrics endpoint
curl http://localhost:8000/metrics

# Create a service via API
curl -X POST http://localhost:8000/services \
  -H "Content-Type: application/json" \
  -d '{
    "name": "My API",
    "url": "https://httpbin.org/status/200",
    "interval_seconds": 60,
    "timeout_seconds": 10
  }'

# View in frontend
# Open http://localhost:3000
```