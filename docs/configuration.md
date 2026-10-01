# Configuration

## Precedence

This repository combines dashboard defaults with settings for external services. It defines no shared command-line, environment variable and configuration-file override order; each external service resolves its own settings.

## Integration settings

The sample scrape uses /plugin/prometheus_exporter/metrics on port 5000 with Bearer authorization. Keep the token in a Prometheus credentials_file. Set dashboard variables job_octoprint, instance, tool_identifier and bed_identifier to values emitted by your plugin.

## Dashboard variables

| Option | Type | Default | Description |
| --- | --- | --- | --- |
| `octoprint-printer.json / prometheus_ds` | datasource | `prometheus` | Grafana data source selected by the dashboard. |
| `octoprint-printer.json / job_octoprint` | textbox | `octoprint` | Dashboard variable whose value selects a scrape job, instance or endpoint. |
| `octoprint-printer.json / instance` | query | `label_values(up{job="${job_octoprint}"}, instance)` | Queries the data source for available values. |
| `octoprint-printer.json / tool_identifier` | textbox | `T0` | Dashboard variable whose value selects a scrape job, instance or endpoint. |
| `octoprint-printer.json / bed_identifier` | textbox | `B` | Dashboard variable whose value selects a scrape job, instance or endpoint. |

## Prometheus jobs

The supplied [scrape example](https://github.com/willtheorangeguy/octoprint-monitoring/blob/HEAD/examples/prometheus-scrape.yml) defines `octoprint`. Copy its entries into your own scrape_configs and replace documentation hostnames. Job names can change if the dashboard variables change with them.

## Examples

The complete scrape job examples are in [`examples/prometheus-scrape.yml`](https://github.com/willtheorangeguy/octoprint-monitoring/blob/HEAD/examples/prometheus-scrape.yml). Copy the relevant job into your Prometheus configuration and replace the example targets.
