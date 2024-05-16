# influxdb_grafana
docker compose for InfluxDB, Grafana and Telegraf

## CREATE FILE .ENV in the same location as the othe rthree files
``` 
# INFLUXDB2 INIT
# REF: https://hub.docker.com/_/influxdb
DOCKER_INFLUXDB_INIT_USERNAME=<PUT YOUR USERNAME HERE>
DOCKER_INFLUXDB_INIT_PASSWORD=<PUT YOUR PASSWORD HERE>
DOCKER_INFLUXDB_INIT_ORG=<ENTER YOUR ORG NAME>
DOCKER_INFLUXDB_INIT_BUCKET=hubitat
DOCKER_INFLUXDB_INIT_ADMIN_TOKEN=<ENTER A WHATEVER YOU WANT FOR THIS TOKEN TO USE>
INFLUXDB_IP=<enter your ip>

# INFLUXDB default is 8086, choose what works for you
INFLUXDB_PORT=8086

# REF: https://grafana.com/docs/grafana/latest/setup-grafana/configure-grafana/#override-configuration-with-environment-variables
# GRAFANA INIT
GF_SECURITY_ADMIN_USER=<ENTER USER NAME FOR GRAFANA>
GF_SECURITY_ADMIN_PASSWORD=<ENTER YOUR PASSWORD FOR GRAFANA>
GF_SECURITY_ADMIN_EMAIL=<ENTER YOUR EMAIL FOR GRAFANA>

# GRAFANA default is 3000, choose what works for you
GRAFANA_PORT=3001

# Attempt using typical first user: 1000
# id -u can provide correct ID, if it fails directory creation
USER_ID=1000

# TELGRAF CONF
# REF: https://raw.githubusercontent.com/InfluxCommunity/InfluxDBv2_Telegraf_Docker/main/telegraf/mytelegraf.conf
``` 
