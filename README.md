# tick-kubernetes-webinar

A set of files for the Monitoring Kubernetes with InfluxData Webinar

### Prerequisites

- Running Kubernetes Cluster
- Helm installed with Tiller running in-cluster
  - [Install Helm](https://github.com/kubernetes/helm/blob/master/docs/install.md)
  - [Initalize `tiller`](https://github.com/kubernetes/helm/blob/master/docs/install.md#installing-tiller) -> `helm init`

### DEPLOY IT!

```bash
# InfluxDB
helm install --name influxdb --namespace tick stable/influxdb
# Chronograf
helm install --name chronograf --namespace tick --values chronograf.yaml stable/chronograf
# Telegraf
helm install --name telegraf --namespace tick --values telegraf.yaml stable/telegraf
# Kapacitor
helm install --name kapacitor --namespace tick --values kapacitor.yaml stable/kapacitor
```

### CONFIGURE IT!

```ruby
"InfluxDB URL" => "http://influxdb-influxdb.tick:8086"
"Kapacitor URL" => "http://kapacitor-kapacitor.tick:9092"
```

### DESTROY IT!

```bash
# Delete your helm releases
helm delete influxdb kapacitor telegraf chronograf --purge
# Drop the namespace
kubectl delete ns tick
```