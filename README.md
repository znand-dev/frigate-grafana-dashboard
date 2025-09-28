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

## Importing the Dashboard into Grafana

There are two easy ways to import this dashboard:

### 1. Import JSON file (recommended)
1. In Grafana, click **Dashboards → New → Import**.  
2. Upload the file `dashboard.json` from this repository.  
3. Select your **Prometheus** data source when prompted.  
4. Click **Import** → the dashboard will appear in your list.

### 2. Copy & Paste JSON
1. Open `dashboard.json` in a text editor.  
2. Copy the entire JSON content.  
3. In Grafana, go to **Dashboards → New → Import**.  
4. Paste the JSON into the text box and click **Load**.  
5. Choose your **Prometheus** data source → click **Import**.

I've also uploaded it on the [Grafana](https://grafana.com/grafana/dashboards/24165) so you can import the ID to your Grafana.

---

## Prometheus Configuration
Add this job to your `prometheus.yml`:

```yaml
scrape_configs:
  - job_name: 'frigate'
    static_configs:
      - targets: ['192.168.1.50:5000']   # Replace with your Frigate host:port
    metrics_path: /api/metrics
