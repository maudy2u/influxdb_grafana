# influxdb_grafana
docker compose for InfluxDB, Grafana and Telegraf

The intent of the respository is to assist Hubitat users with the `InfluxDB Logger` App by using docker-compose to easily stand up an InfluxDB and Grafana environment.
Put the files `docker-compose.yml`, `datasources.yml`, and `mytelegraf.conf` all into the same directory and then creating the `.env` file below the result is:
- InfluxDB will have a userid and password to log in, a default bucket, and known token
- Grafana will have a userid and password to log in, and is default datasource will be InfluxDB using FLux query langauge via the Token, and default bucket.
- `InfluxDB Logger` can then be configured to point to the InfluxDB using the IP:PORT, default bucket, and token

## Setup Notes... 

1. Change the values in `.env` with the "<...>" to  your needs
2. Change the values for Weather in `weather/weather411.conf` change the variables to your install: `APIKEY`, `LAT`, `LON`, `DB`, `TOKEN`, `ORG`, `URL`
3. Save the edits
4. Run `docker-compose up`

**Caveat(s)**: 

a) depending on version of `docker` you can need to manually create the following subdirectories can need to be created: `config`, `data`, `gdata`
b) the User permisions can be prevent writing to the sub folders, make sure the `USERID` in the `.env` matches the host folder and `docker` can write to it.

