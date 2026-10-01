# octoprint-monitoring — Configuration

The sample scrape uses /plugin/prometheus_exporter/metrics on port 5000 with Bearer authorization. Keep the token in a Prometheus credentials_file. Set dashboard variables job_octoprint, instance, tool_identifier and bed_identifier to values emitted by your plugin.

## Dashboard variables

| Dashboard | Variable | Type | Default or query |
|---|---|---|---|
| `octoprint-printer.json` | `prometheus_ds` | datasource | `prometheus` |
| `octoprint-printer.json` | `job_octoprint` | textbox | `octoprint` |
| `octoprint-printer.json` | `instance` | query | `label_values(up{job="${job_octoprint}"}, instance)` |
| `octoprint-printer.json` | `tool_identifier` | textbox | `T0` |
| `octoprint-printer.json` | `bed_identifier` | textbox | `B` |

## Prometheus jobs

The supplied [scrape example](../examples/prometheus-scrape.yml) defines `octoprint`. Copy its entries into your own scrape_configs and replace documentation hostnames. Job names can change if the dashboard variables change with them.
