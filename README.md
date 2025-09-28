![Grafana](https://img.shields.io/badge/Grafana-Dashboard-F46800?logo=grafana&logoColor=white)
![Prometheus](https://img.shields.io/badge/Prometheus-Metrics-E6522C?logo=prometheus&logoColor=white)
![License](https://img.shields.io/badge/License-MIT-green.svg)

# Frigate Grafana Dashboard

This repository contains a Grafana dashboard for monitoring [Frigate](https://github.com/blakeblackshear/frigate) with Prometheus.

## Features
- Python runtime & Garbage Collector (GC) monitoring
- CPU & memory usage (system + per-process)
- Camera FPS (input, processed, detection, skipped)
- Object detection inference speed
- Storage utilization (recordings, clips, cache, shm)
- Frigate service uptime & version info

## Requirements
- Grafana ≥ 9.x
- Prometheus
- Frigate with `/api/metrics` enabled

## Prometheus Configuration
Add this job to your `prometheus.yml`:

```yaml
scrape_configs:
  - job_name: 'frigate'
    static_configs:
      - targets: ['192.168.1.50:5000']   # Replace with your Frigate host:port
    metrics_path: /api/metrics
