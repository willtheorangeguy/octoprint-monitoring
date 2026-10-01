# octoprint-monitoring — Quickstart

## Prerequisites

OctoPrint, its Prometheus Exporter plugin, a scrape account and token, Prometheus and Grafana.

## Set up

Install the OctoPrint Prometheus Exporter plugin, create a token allowed to read its metrics, adapt examples/prometheus-scrape.yml and import dashboards/octoprint-printer.json.

The example Prometheus scrape job names are `octoprint`.

## Confirm data

In Prometheus, check `up{job="octoprint"}` and inspect a panel query in Grafana.
For missing data, see [troubleshooting](./troubleshooting.md).
