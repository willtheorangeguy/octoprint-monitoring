# Installation

## Requirements

OctoPrint, its Prometheus Exporter plugin, a scrape account and token, Prometheus and Grafana.

## Procedure

Install the OctoPrint Prometheus Exporter plugin, create a token allowed to read its metrics, adapt examples/prometheus-scrape.yml and import dashboards/octoprint-printer.json.

The files under [examples](https://github.com/willtheorangeguy/octoprint-monitoring/tree/HEAD/examples) are reference configuration. Replace example addresses, token paths and bind addresses for your deployment.

Next, review [configuration](configuration.md) and [dashboard usage](usage.md).

## Verify the installation

Check that the configured scrape target is healthy in Prometheus, then import the dashboard in Grafana and confirm its panels return data. Use the target and label names documented in [Getting started](getting-started.md).

## Upgrading

Update the dashboard JSON from this repository when you adopt a newer version. Update any exporter or monitored service using that project's upgrade instructions.

## Uninstalling

Remove the dashboard from Grafana and remove only the scrape or deployment entries you added for this project. Keep shared monitoring services that other dashboards use.
