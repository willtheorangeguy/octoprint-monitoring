# OctoPrint printer dashboard

Portable monitoring bundle with example configuration. Replace example addresses and token paths for your installation; no live credentials are included.

## Requirements

The OctoPrint Prometheus Exporter plugin and a Prometheus scrape of its authenticated metrics endpoint.

## Dashboards

- `dashboards/octoprint-printer.json`

Import the JSON in Grafana using **Dashboards > New > Import**. Select your data source from the dashboard variable(s) at the top. Update the Prometheus job variables to match your `scrape_configs` job names; use the Instance selector when present. The dashboard's JSON is also suitable for file provisioning after you have selected or provisioned data source UIDs.

Expected default job labels:

- `octoprint-printer.json`: octoprint

## Monitoring code

See the code and example configuration in this folder, if present. Keep API keys and metrics bearer tokens in local secret files or another secret manager; never commit them. Scrape examples use documentation addresses and must be edited for your network.

## Before publishing

Test against the application and Grafana versions you intend to support. Add a license you choose and check attribution for upstream components. No release or Grafana catalog upload has been performed.

## OctoPrint setup

Install the OctoPrint Prometheus Exporter plugin, create an OctoPrint account allowed to scrape it, and configure a Prometheus job named `octoprint` with its bearer token in a protected `credentials_file`. Import the dashboard and choose the correct job and instance. Set the tool and bed identifier variables to the identifiers your plugin emits. Add your own OctoPrint UI link after import if desired.

A sample `scrape_configs` fragment is in `examples/prometheus-scrape.yml`; replace the example hosts and token paths.
