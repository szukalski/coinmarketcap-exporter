# coinmarketcap-exporter

Stolen from <https://github.com/bonovoxly/coinmarketcap-exporter>. All credit there.

I just added the EUR values to the scraper, plus some dashboard jsons for EUR values.

A prometheus exporter for <https://coinmarketcap.com/>. Provides Prometheus metrics from the API endpoint of Coinmarketcap, such as US price, Bitcoin price, trading volume, etc. [Blog post found here](http://blog.billyc.io/2017/12/02/a-prometheus-exporter-for-cryptocurrency-values-using-the-coinmarketcap-api/).

When running this exporter with both Prometheus and Grafana, [you can create dashboards like](https://grafana.com/dashboards/3890):

![coinmarketcap-single-dashboard](https://github.com/bonovoxly/coinmarketcap-exporter/raw/master/img/coinmarketcap.png "coinmarketcap-exporter with Prometheus and Grafana")

# Developing

- Build the image:

```
./build.sh
```

or

```
docker build -t szukalski/coinmarketcap-exporter:latest .
```

- Run it while listening on localhost:9100:

```
docker run --rm -p 127.0.0.1:9101:9101 szukalski/coinmarketcap-exporter:latest
```

- Run it interactively:

```
docker run --rm -it --entrypoint=/bin/bash -p 127.0.0.1:9101:9101 -v ${PWD}:/opt/coinmarketcap-exporter szukalski/coinmarketcap-exporter:latest
```

- Then to launch:

```
python coinmarketcap.py
```

# Testing the Prometheus Grafana Stack

- In the `prometheus-compose` directory, run:

```
docker-compose up -d
```

- Go to <http://host:3000>.  Log in as `admin/admin`. 
- To import the dashboard, click the "Home" button at the top, then on the right, click "Import Dashboard".
- Load the json in the git repo.
- Select the "prometheus" data source.
- Modify the other settings as preferred. Click "Import".
- The new dashboard should be selectable.
- The Prometheus interface can be accessed at <http://host:9090>

# Thanks and Links

- Coinmarketcap API link - <https://coinmarketcap.com/api/>
- Prometheus exporters - <https://prometheus.io/docs/instrumenting/writing_exporters/>
- Writing JSON exporters in Python from Robust Perception - <https://www.robustperception.io/writing-json-exporters-in-python/>
- Grafana Dashboard - <https://grafana.com/dashboards/3890>

If you find this useful and want to contribute:

- BTC: `1C4aooXtb45WwmouPiLENDJp4FWn8cfabG`
