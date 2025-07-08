# MonitoringApps

## Prometheus

Setting up Prometheus in Mac

Step1 : Install Homebrew, if you do not already have it installed

```bash
/bin/bash -c "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/HEAD/install.sh)"
```

Step2: Then install prometheus

```bash
brew install prometheus
```

Step3: Then you will be prompted the following message

```bash
To start prometheus now and restart at login:
  brew services start prometheus
Or, if you don't want/need a background service you can just run:
  /opt/homebrew/opt/prometheus/bin/prometheus_brew_services
```

Step4: You can decide whether or not you want the service to run all the time and also restart at login.

```bash
brew services stop prometheus -> stops the service
brew services cleanup -> cleans up, so that it does not restart on login
```

Step5: Use one of the following commands depending on where newly installed files are stored to locate the configuration file

```bash
cat /opt/homebrew/etc/prometheus.yml 
```

Step6: This is what it would look like

```bash
global:
  scrape_interval: 15s

scrape_configs:
  - job_name: "prometheus"
    static_configs:
    - targets: ["localhost:9090"]
```

Step7: We can open browser to get visual aid for checking the metrics data, open localhost:9090 from your browser

![alt text](image.png)


## Install Prometheus Node Exporter using Homebrew

Step1: Install Node Exporter via Homebrew

```bash
brew install node_exporter
```

Step2: Run it in the background

```bash
nohup node_exporter > /tmp/node_exporter.log 2>&1 &
```

Step3: Open in browser

```bash
http://localhost:9100/metrics
```
