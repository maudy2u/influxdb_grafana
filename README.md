# influxdb_grafana
docker compose for InfluxDB, Grafana and Telegraf

The intent of the respository is to assist Hubitat users with the `InfluxDB Logger` App by using docker-compose to easily stand up an InfluxDB and Grafana environment.
Put the files `docker-compose.yml`, `datasources.yml`, and `mytelegraf.conf` all into the same directory and then creating the `.env` file below the result is:
- InfluxDB will have a userid and password to log in, a default bucket, and known token
- Grafana will have a userid and password to log in, and is default datasource will be InfluxDB using FLux query langauge via the Token, and default bucket.
- `InfluxDB Logger` can then be configured to point to the InfluxDB using the IP:PORT, default bucket, and token

## Some quick instructions

1. Edit the .env changing the "<...>" to  your needs
2. Save the edits
3. Depending on version of docker-compose the following subdirectories can need to be created: 
      `config`, `data`, `gdata`

4. Ensure the above directories have same access user and the docker user identified with `id -u` per the docker-cmpose.yml notes
   - e.g. can need to chown -R 1000:1000 .  in the docker-compose folder, where 1000 is the id returned by `id -u` and used in `.env` as well.
     
5. You will need to manual edit the weather.weather411.conf file... if you plan to use Weather 411
6. Run `docker compose up` or `docker-compose up`, depending on verison

## Sample `.env`
``` 
# INFLUXDB2 INIT
# REF: https://hub.docker.com/_/influxdb
DOCKER_INFLUXDB_INIT_USERNAME=guest
DOCKER_INFLUXDB_INIT_PASSWORD=12345$789*
DOCKER_INFLUXDB_INIT_ORG=hubitat
DOCKER_INFLUXDB_INIT_BUCKET=dashboards
DOCKER_INFLUXDB_INIT_ADMIN_TOKEN=34uibeucbasdkjcb4
INFLUXDB_IP=192.168.1.1

# INFLUXDB default is 8086, choose what works for you
INFLUXDB_PORT=8086

# REF: https://grafana.com/docs/grafana/latest/setup-grafana/configure-grafana/#override-configuration-with-environment-variables
# GRAFANA INIT
GF_SECURITY_ADMIN_USER=guest
GF_SECURITY_ADMIN_PASSWORD=12345$789*
GF_SECURITY_ADMIN_EMAIL=testing@the.net

# GRAFANA default is 3000, choose what works for you
GRAFANA_PORT=3001


# GRAFANA PLUGIN
# ADD YOUR PLUGINS HERE as a single line using ", " to separate
# e.g. 
GF_PLUGINS=grafana-piechart-panel, https://github.com/yesoreyeram/yesoreyeram-boomtable-panel/releases/download/v1.5.0-alpha.3/yesoreyeram-boomtable-panel-1.5.0-alpha.3.zip, yesoreyeram-boomtable-panel, fetzerch-sunandmoon-datasource, simpod-json-datasource


# Attempt using typical first user: 1000
# id -u can provide correct ID, if it fails directory creation
USER_ID=1000

``` 
