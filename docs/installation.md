# octoprint-monitoring — Installation

## Requirements

OctoPrint, its Prometheus Exporter plugin, a scrape account and token, Prometheus and Grafana.

## Procedure

Install the OctoPrint Prometheus Exporter plugin, create a token allowed to read its metrics, adapt examples/prometheus-scrape.yml and import dashboards/octoprint-printer.json.

The files under [examples](../examples) are reference configuration. Replace example addresses, token paths and bind addresses for your deployment.

Next, review [configuration](./configuration.md) and [dashboard usage](./usage.md).
