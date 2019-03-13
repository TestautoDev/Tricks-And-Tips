https://www.blazemeter.com/blog/how-to-create-a-lightweight-performance-monitoring-solution-with-docker-grafana-and-influxdb

https://www.blazemeter.com/blog/gatling-tests-monitoring-with-grafana-and-influxdb

### Taurus for docker:
- Create folder name taurus
- Create sub folder name artifact
```
docker run --rm -v C:\ccviews\taurus:/bzt-configs -v C:\ccviews\taurus\artifact:/tmp/artifacts blazemeter/taurus taurus_execution1.yml
```
