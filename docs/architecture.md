# Architecture

This project connects its data source to its Grafana dashboard through the components shown below.

## Overview

This diagram shows the data path for this project.

```mermaid
graph LR
  A[OctoPrint] -->|exposes metrics through| B[Prometheus Exporter plugin]
  B -->|scraped by| C[Prometheus]
  C -->|queried by| D[Grafana dashboard]
```

## Components

### Data source

OctoPrint Prometheus Exporter plugin -> authenticated /plugin/prometheus_exporter/metrics scrape -> Prometheus -> Grafana.

### Dashboard

`dashboards/octoprint-printer.json` contains the Grafana dashboard definition.

## Data flow

OctoPrint Prometheus Exporter plugin -> authenticated /plugin/prometheus_exporter/metrics scrape -> Prometheus -> Grafana. Grafana evaluates dashboard queries against the selected data source and label values.

## Directory layout

```text
.
├── dashboards/  Grafana dashboard JSON files
├── examples/  Scrape and deployment examples
├── docs/        Documentation source
└── README.md    Project overview and quick links
```
