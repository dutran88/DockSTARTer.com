# Telegraf

---

[Telegraf](https://www.influxdata.com/time-series-platform/telegraf/) is an agent written in Go for collecting performance metrics from the system it's running on and the services running on that system. The collected metrics are output to InfluxDB or or other supported data stores.

- App: 
- Docker Image: 

---

When you first install telegraf from DS, you will encounter an error simular the log below:

```.logs
[outputs.influxdb] when writing to [http://localhost:8086]: connect: connection refused ....
```

To correct this, you must install Telegraf locally. 

**Ubuntu** Add the InfluxData repository with the following commands:


```bash
wget -qO- https://repos.influxdata.com/influxdb.key | sudo apt-key add -
source /etc/lsb-release
echo "deb https://repos.influxdata.com/${DISTRIB_ID,,} ${DISTRIB_CODENAME} stable" | sudo tee /etc/apt/sources.list.d/influxdb.list

```

***Debian***: Add the InfluxData repository with the following commands:

```bash
# Before adding Influx repository, run this so that apt will be able to read the repository.

sudo apt-get update && sudo apt-get install apt-transport-https

# Add the InfluxData key

wget -qO- https://repos.influxdata.com/influxdb.key | sudo apt-key add -
source /etc/os-release
test $VERSION_ID = "7" && echo "deb https://repos.influxdata.com/debian wheezy stable" | sudo tee /etc/apt/sources.list.d/influxdb.list
test $VERSION_ID = "8" && echo "deb https://repos.influxdata.com/debian jessie stable" | sudo tee /etc/apt/sources.list.d/influxdb.list
test $VERSION_ID = "9" && echo "deb https://repos.influxdata.com/debian stretch stable" | sudo tee /etc/apt/sources.list.d/influxdb.list
test $VERSION_ID = "10" && echo "deb https://repos.influxdata.com/debian buster stable" | sudo tee /etc/apt/sources.list.d/influxdb.list

```

Install and start Telegraf service:

```bash
sudo apt-get update && sudo apt-get install telegraf
sudo service telegraf start
```

After you install telegraf, your *telegraf.conf* is installed in /etc/telegraf/telegraf.conf

Finally, you must link your container to your telegraf.conf. To do that, create an override.yaml. 

```yaml
  telegraf:
    volumes:
    - ${DOCKERCONFDIR}/telegraf/telegraf.conf:/etc/telegraf/telegraf.conf:ro 
```

Restart your containter 

```bash
docker restart telegraf
```

Now when you look at your log files, you should see:

```logs
2019-11-28T00:58:51Z I! Starting Telegraf 1.12.6,
2019-11-28T00:58:51Z I! Using config file: /etc/telegraf/telegraf.conf,
2019-11-28T00:58:51Z I! Loaded inputs: cpu disk diskio kernel mem processes swap system,
2019-11-28T00:58:51Z I! Loaded aggregators: ,
2019-11-28T00:58:51Z I! Loaded processors: ,
2019-11-28T00:58:51Z I! Loaded outputs: influxdb,
2019-11-28T00:58:51Z I! Tags enabled: host=192.168.1.x,
2019-11-28T00:58:51Z I! [agent] Config: Interval:10s, Quiet:false, Hostname:"192.168.1.x", Flush Interval:10s,
```

All done!