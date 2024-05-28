# influxdb_grafana
docker compose for InfluxDB, Grafana and Telegraf

The intent of the respository is to assist Hubitat users with the `InfluxDB Logger` App by using docker-compose to easily stand up an InfluxDB and Grafana environment.
Put the files `docker-compose.yml`, `datasources.yml`, and `mytelegraf.conf` all into the same directory and then creating the `.ENV` file below the result is:
- InfluxDB will have a userid and password to log in, a default bucket, and known token
- Grafana will have a userid and password to log in, and is default datasource will be InfluxDB using FLux query langauge via the Token, and default bucket.
- `InfluxDB Logger` can then be configured to point to the InfluxDB using the IP:PORT, default bucket, and token

## .env 

1. Create the .ENV with a text editor, and save it in the same location as the other three files
2. Change the values with the "<...>" to  your needs
3. Save the edits
4. Run `docker-compose up`

**Caveat**: depending on version of docker-compose the following subdirectories can need to be created: 
`config`, `data, `gdata`

``` 
# INFLUXDB2 INIT
# REF: https://hub.docker.com/_/influxdb
DOCKER_INFLUXDB_INIT_USERNAME=<PUT YOUR USERNAME HERE>
DOCKER_INFLUXDB_INIT_PASSWORD=<PUT YOUR PASSWORD HERE>
DOCKER_INFLUXDB_INIT_ORG=<ENTER YOUR ORG NAME>
DOCKER_INFLUXDB_INIT_BUCKET=<NAME OF THE BUCKET TO USE, e.g. Hubitat>
DOCKER_INFLUXDB_INIT_ADMIN_TOKEN=<ENTER A WHATEVER YOU WANT FOR THIS TOKEN TO USE>
INFLUXDB_IP=<IP OR HOSTNAME FOR THE HOST MACHINE>

# INFLUXDB default is 8086, choose what works for you
INFLUXDB_PORT=<YOUR DESIRE PORT FOR INFLUXDB>

# REF: https://grafana.com/docs/grafana/latest/setup-grafana/configure-grafana/#override-configuration-with-environment-variables
# GRAFANA INIT
GF_SECURITY_ADMIN_USER=<ENTER USER NAME FOR GRAFANA>
GF_SECURITY_ADMIN_PASSWORD=<ENTER YOUR PASSWORD FOR GRAFANA>
GF_SECURITY_ADMIN_EMAIL=<ENTER YOUR EMAIL FOR GRAFANA>

# GRAFANA default is 3000, choose what works for you
GRAFANA_PORT=<YOUR DESIRED PORT FOR GRAFANA>

# Attempt using typical first user: 1000
# id -u can provide correct ID, if it fails directory creation
USER_ID=<YOUR DESIRED USER IF FOR LINUX>

# TELGRAF CONF
# REF: https://raw.githubusercontent.com/InfluxCommunity/InfluxDBv2_Telegraf_Docker/main/telegraf/mytelegraf.conf
``` 
