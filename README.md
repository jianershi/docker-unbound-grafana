# Docker Unbound Grafana

this repository is a docker version of [Unbound-Config](https://github.com/jianershi/unbound-config)

this build unbound and grafana separately so you have the choice of using other unbound docker. 

![screenshot](screenshot.png)
## Pre-requisite
1. have a custom docker network `my-network`
    * `docker network create my-network`
2. have all SSL certificate configured in unbound.conf under `/etc/unbound`
    *  `docker run -v /etc/unbound:/etc/unbound unbound-mine ./unbound-control-setup`
3. assumes prometheus configure file in `/etc/prometheus`

if you choose to use your own docker unbound container, change the name in `grafana-prometheus-unbound-exporter/docker-compose.yml`
## License
MIT
