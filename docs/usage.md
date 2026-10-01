# octoprint-monitoring — Dashboard Usage

Import the JSON files using **Grafana → Dashboards → New → Import**. Set the data source and variables listed in [configuration](./configuration.md).

## OctoPrint Printer

Source: [octoprint-printer.json](../dashboards/octoprint-printer.json). Refresh: `30s`.

<!-- Screenshot: after adding octoprint-printer.png to .github/icons/octoprint-monitoring/, replace this comment with ![OctoPrint Printer](https://raw.githubusercontent.com/willtheorangeguy/.github/main/icons/octoprint-monitoring/octoprint-printer.png). -->

### Panels

| Panel | Type | What it shows |
|---|---|---|
| Printer State | stat | Reported OctoPrint printer state. |
| Print Progress | stat | Present only when the plugin reports an active job. |
| Nozzle Actual | stat | See the query reference below. |
| Bed Actual | stat | See the query reference below. |
| Elapsed Job Time | stat | Active-job reading only; absent until the plugin emits timing. |
| Estimated Time Left | stat | OctoPrint estimate, not a guaranteed finish time. |
| Nozzle Temperature | timeseries | See the query reference below. |
| Bed Temperature | timeseries | See the query reference below. |
| Print Progress History | timeseries | Series disappears when no active job is reported. |
| Active Job Timing | timeseries | Timing gauges exist only while the plugin emits active-job data. |
| Started Since Restart | stat | See the query reference below. |
| Completed Since Restart | stat | See the query reference below. |
| Failed Since Restart | stat | Plugin counter since OctoPrint restart. |
| Cancelled Since Restart | stat | See the query reference below. |
| Completed Print Time | stat | Accumulated completed-print runtime since OctoPrint restart; not the current job's elapsed time. |
| Print Outcome Counters | timeseries | These counters reset when OctoPrint restarts. |
| Commanded Print Fan | timeseries | Derived from M106/M107 S values (0â€“255); this is commanded PWM, not measured fan RPM. |

<!-- Screenshot: add a focused panel or section image here after uploading it to .github/icons/octoprint-monitoring/. -->

### Reading the results

Active job timing and progress metrics may be absent while idle. Job outcome counters reset on OctoPrint restart. The fan panel shows commanded PWM derived from M106/M107, not measured RPM.

### Query reference

These expressions are copied from the dashboard JSON. Grafana substitutes the dashboard variables at runtime.

#### Printer State

```promql
max by(state_string) (octoprint_printer_state_info{job="${job_octoprint}",instance="$instance"})
```

#### Print Progress

```promql
max(octoprint_print_progress{job="${job_octoprint}",instance="$instance"})
```

#### Nozzle Actual

```promql
octoprint_temperatures_actual{job="${job_octoprint}",instance="$instance",identifier="$tool_identifier"}
```

#### Bed Actual

```promql
octoprint_temperatures_actual{job="${job_octoprint}",instance="$instance",identifier="$bed_identifier"}
```

#### Elapsed Job Time

```promql
max(octoprint_print_time_elapsed{job="${job_octoprint}",instance="$instance"})
```

#### Estimated Time Left

```promql
max(octoprint_print_time_left_estimate{job="${job_octoprint}",instance="$instance"})
```

#### Nozzle Temperature

```promql
octoprint_temperatures_actual{job="${job_octoprint}",instance="$instance",identifier="$tool_identifier"}
octoprint_temperatures_target{job="${job_octoprint}",instance="$instance",identifier="$tool_identifier"}
```

#### Bed Temperature

```promql
octoprint_temperatures_actual{job="${job_octoprint}",instance="$instance",identifier="$bed_identifier"}
octoprint_temperatures_target{job="${job_octoprint}",instance="$instance",identifier="$bed_identifier"}
```

#### Print Progress History

```promql
max(octoprint_print_progress{job="${job_octoprint}",instance="$instance"})
```

#### Active Job Timing

```promql
max(octoprint_print_time_elapsed{job="${job_octoprint}",instance="$instance"})
max(octoprint_print_time_left_estimate{job="${job_octoprint}",instance="$instance"})
```

#### Started Since Restart

```promql
octoprint_started_prints_total{job="${job_octoprint}",instance="$instance"}
```

#### Completed Since Restart

```promql
octoprint_done_prints_total{job="${job_octoprint}",instance="$instance"}
```

#### Failed Since Restart

```promql
octoprint_failed_prints_total{job="${job_octoprint}",instance="$instance"}
```

#### Cancelled Since Restart

```promql
octoprint_cancelled_prints_total{job="${job_octoprint}",instance="$instance"}
```

#### Completed Print Time

```promql
octoprint_printing_time_total{job="${job_octoprint}",instance="$instance"}
```

#### Print Outcome Counters

```promql
octoprint_started_prints_total{job="${job_octoprint}",instance="$instance"}
octoprint_done_prints_total{job="${job_octoprint}",instance="$instance"}
octoprint_failed_prints_total{job="${job_octoprint}",instance="$instance"}
octoprint_cancelled_prints_total{job="${job_octoprint}",instance="$instance"}
```

#### Commanded Print Fan

```promql
100 * octoprint_print_fan_speed{job="${job_octoprint}",instance="$instance"} / 255
```
