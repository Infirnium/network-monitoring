# Node Exporter Setup (Linux)

1. Download the latest Node Exporter binary:
   wget https://github.com/prometheus/node_exporter/releases/latest/download/node_exporter-1.7.0.linux-amd64.tar.gz

2. Extract and move binary:
   tar xvf node_exporter-1.7.0.linux-amd64.tar.gz
   sudo mv node_exporter-*/node_exporter /usr/local/bin/

3. Create systemd service:
   sudo nano /etc/systemd/system/node_exporter.service

   [Unit]
   Description=Node Exporter
   After=network.target

   [Service]
   ExecStart=/usr/local/bin/node_exporter

   [Install]
   WantedBy=default.target

4. Start and enable:
   sudo systemctl daemon-reexec
   sudo systemctl start node_exporter
   sudo systemctl enable node_exporter

Node Exporter runs on port 9100 by default.