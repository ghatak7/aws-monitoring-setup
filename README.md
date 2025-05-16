

# 🔍 AWS Monitoring Setup with Prometheus, Node Exporter, and Grafana

This project sets up a real-time monitoring stack on an AWS EC2 instance using **Prometheus**, **Node Exporter**, and **Grafana** to collect and visualize system metrics.

---

## 📦 Stack Components

- **Prometheus**: Metrics scraping & time-series DB
- **Node Exporter**: Exposes Linux system metrics to Prometheus
- **Grafana**: Beautiful visualization of metrics from Prometheus

---

## 🛠️ Setup Instructions

### 1. 📍 Environment

- EC2 Amazon Linux 2 instance
- Security Group:
  - Port `9090` (Prometheus)
  - Port `9100` (Node Exporter)
  - Port `3000` (Grafana)

### 2. 📦 Install Prometheus

```bash
# Download and install
wget https://github.com/prometheus/prometheus/releases/download/v2.52.0/prometheus-2.52.0.linux-amd64.tar.gz
tar xvf prometheus-2.52.0.linux-amd64.tar.gz
sudo mv prometheus-2.52.0.linux-amd64 /etc/prometheus
sudo useradd --no-create-home --shell /bin/false prometheus
Set up prometheus.yml and prometheus.service (see files in prometheus/ folder)

3. 📈 Install Node Exporter
bash
Copy
Edit
wget https://github.com/prometheus/node_exporter/releases/download/v1.8.1/node_exporter-1.8.1.linux-amd64.tar.gz
tar xvf node_exporter-1.8.1.linux-amd64.tar.gz
sudo mv node_exporter-1.8.1.linux-amd64 /etc/node_exporter
Set up node_exporter.service (see files in node_exporter/ folder)

4. 📊 Install Grafana
bash
Copy
Edit
sudo yum install -y https://dl.grafana.com/oss/release/grafana-10.2.3-1.x86_64.rpm
sudo systemctl daemon-reexec
sudo systemctl start grafana-server
sudo systemctl enable grafana-server
Access Grafana at http://<EC2_PUBLIC_IP>:3000
(Default login: admin / admin)

5. 📡 Connect Prometheus to Grafana
Add data source → Prometheus → URL: http://localhost:9090

Import dashboards or create custom ones

📸 Screenshots
<p align="center"> <img src="screenshots/grafana-dashboard.png" width="700"/> </p> <p align="center"> <img src="screenshots/prometheus-targets.png" width="700"/> </p>
📁 Project Structure
arduino
Copy
Edit
aws-monitoring-setup/
├── prometheus/
│   ├── prometheus.yml
│   └── prometheus.service
├── node_exporter/
│   └── node_exporter.service
├── grafana/
│   └── grafana-server.service
├── screenshots/
└── README.md
