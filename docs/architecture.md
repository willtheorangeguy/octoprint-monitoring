# octoprint-monitoring — Architecture

OctoPrint plugin /plugin/prometheus_exporter/metrics -> authenticated Prometheus scrape -> Grafana dashboard.

## Components

- [dashboards/](../dashboards): Grafana dashboard definitions
- [examples/](../examples): deployment and scrape examples

## Data interpretation

Active job timing and progress metrics may be absent while idle. Job outcome counters reset on OctoPrint restart. The fan panel shows commanded PWM derived from M106/M107, not measured RPM.
