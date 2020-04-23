### 1. Install Influx DB

- `curl -sL https://repos.influxdata.com/influxdb.key | sudo apt-key add -`

- `source /etc/lsb-release`

- `echo "deb https://repos.influxdata.com/${DISTRIB_ID,,} ${DISTRIB_CODENAME} stable" | sudo tee /etc/apt/sources.list.d/influxdb.list`

- `apt update`

- `apt install influxdb`

- `systemctl start influxdb`

- `systemctl enable influxdb`

- `netstat -tupan`


### 2. Create database and user

- `influx`

- `create database telegraf`

- `use telegraf`

- `create user itnetwork with password 'itnetwork'`

- `show databases`

- `show users`


### 3. Install telegraf

- `apt install telegraf`

- `systemctl start telegraf`

- `systemctl enable telegraf`

- `systemctl status telegraf`


### 4. Configure telegraf

- `cd /etc/telegraf`

- `mv telegraf.conf telegraf.conf.orig`

- `vi telegraf.conf`

- Paste the following into telegraph.conf:

```
# Global Config
[global_tags]


# Agent Config
[agent]
  interval = "10s"
  round_interval = true
  metric_batch_size = 1000
  metric_buffer_limit = 10000
  collection_jitter = "0s"
  flush_interval = "10s"
  flush_jitter = "0s"
  precision = ""
  hostname = "tig-stack"
  omit_hostname = false


# Output Config
[[outputs.influxdb]]
  urls = ["http://127.0.0.1:8086"]
  database = "telegraf"
   username = "itnetwork"
   password = "itnetwork"


# Input Config
[[inputs.cpu]]
  percpu = true
  totalcpu = true
  collect_cpu_time = false
  report_active = false
[[inputs.disk]]
  ignore_fs = ["tmpfs", "devtmpfs", "devfs", "iso9660", "overlay", "aufs", "squashfs"]
[[inputs.diskio]]
[[inputs.kernel]]
[[inputs.mem]]
[[inputs.processes]]
[[inputs.swap]]
[[inputs.system]]
[[inputs.net]]
[[inputs.netstat]]
```

- `systemctl restart telegraf`


### 5. Install Grafana

- `apt install apt-transport-https`

- `wget -q -O - https://packages.grafana.com/gpg.key | sudo apt-key add -`

- `add-apt-repository "deb https://packages.grafana.com/oss/deb stable main"`

- `apt update`

- `apt install grafana`

- `systemctl start grafana-server`

- `systemctl enable grafana-server`

- `netstat -tupan`


### 6. Setup Grafana Data Source

- Open web browser and go to `http://your.ip.address:3000`

- Login with the default user `admin` with password `admin`

- Change the admin password

- Click add data source

- Click InfluxDB

- In URL field enter: `http://localhost:8086`

- In Database field enter: `telegraf`

- In User filed enter: `itnetwork`

- In Password field enter: `itnetwork`

- Click Save & Test


### 7. Setup a Dashboard

- Click Dashboards --> Manage in side bar

- Click Import

- Add the following URL to the Grafana.com Dashboard field: `https://grafana.com/grafana/dashboards/5955`

- Give it a name: tig-stack

- Select the datasource InfuxDB

- Click import
