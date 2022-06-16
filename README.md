## Kafka Snap

This repository is for experimenting with packaging Apache Kafka as a snap, using the upstream
binary [releases](https://kafka.apache.org/downloads).

### Testing

To get started using/testing the snap (assuming you have `snapcraft` already):

```bash
# Kafka requires a Zookeeper to start properly. This 'zk' snap was already in the store, and
# seems to satisfy the requirement enough for testing!
$ sudo snap install zk --beta

# Build this snap
$ git clone https://github.com/jnsgruk/kafka-snap
$ cd kafka-snap
$ snapcraft --use-lxd

# Install the snap
sudo snap install --dangerous kafka_3.2.0_amd64.snap

# Check the logs
sudo snap logs -nall kafka:kafka

# Ensure the metrics scraping is working correctly
curl http://localhost:7071
```

### TODO

- [x] Minimum viable Kafka launch!
- [x] Prometheus exporter integration
- [x] Automated build in Github Actions
- [ ] Configurable JVM memory parameters using `snap set`/`snap get`
- [ ] Configurable Zookeeper instance using `snap set`/`snap get`
- [ ] Automated testing in Github Actions
