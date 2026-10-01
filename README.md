<h1 align="center">octoprint-monitoring</h1>
<h4 align="center">A Grafana dashboard for printer status, temperatures, print progress and job counters exposed by the OctoPrint Prometheus Exporter plugin.</h4>

<div align="center">
  <img alt="GitHub Issues" src="https://img.shields.io/github/issues/willtheorangeguy/octoprint-monitoring">
  <img alt="GitHub Pull Requests" src="https://img.shields.io/github/issues-pr/willtheorangeguy/octoprint-monitoring">
  <img alt="License: MIT" src="https://img.shields.io/badge/license-MIT-blue">
  <img alt="gitleaks workflow" src="https://github.com/willtheorangeguy/octoprint-monitoring/actions/workflows/gitleaks.yml/badge.svg">
  <img alt="testing workflow" src="https://github.com/willtheorangeguy/octoprint-monitoring/actions/workflows/testing.yml/badge.svg">
</div>

<p align="center">
  <a href="#key-features">Key Features</a> •
  <a href="#installation">Installation</a> •
  <a href="#usage">Usage</a> •
  <a href="#documentation">Documentation</a> •
  <a href="#support">Support</a> •
  <a href="#contributing">Contributing</a> •
  <a href="#license">License</a>
</p>

<!-- Screenshot: after adding octoprint-monitoring/overview.png to .github/icons/, replace this comment with ![Dashboard overview](https://raw.githubusercontent.com/willtheorangeguy/.github/main/icons/octoprint-monitoring/overview.png). -->

A Grafana dashboard for printer status, temperatures, print progress and job counters exposed by the OctoPrint Prometheus Exporter plugin.

## Key Features

- Printer state and current job progress.
- Tool and bed temperatures.
- Print outcome counters and active job timing.
- Commanded fan PWM display.

## Installation

OctoPrint, its Prometheus Exporter plugin, a scrape account and token, Prometheus and Grafana. Install the OctoPrint Prometheus Exporter plugin, create a token allowed to read its metrics, adapt examples/prometheus-scrape.yml and import dashboards/octoprint-printer.json. See [installation](docs/installation.md) for more detail.

## Usage

Import [octoprint-printer.json](dashboards/octoprint-printer.json) in Grafana using **Dashboards → New → Import**. Choose the data source and match the dashboard variables to your monitoring labels. See [dashboard usage](docs/usage.md).

## Documentation

Full documentation lives in [docs/](docs/index.md): [Quickstart](docs/getting-started.md) · [Configuration](docs/configuration.md) · [Architecture](docs/architecture.md) · [Dashboard usage](docs/usage.md) · [Troubleshooting](docs/troubleshooting.md).

## Support

Open a [GitHub Discussion](https://github.com/willtheorangeguy/octoprint-monitoring/discussions/new) or file an [issue](https://github.com/willtheorangeguy/octoprint-monitoring/issues/new/choose).

## Contributing

Contributions welcome. See the org-wide [Contributing Guide](https://github.com/willtheorangeguy/.github/blob/main/CONTRIBUTING.md) and [Code of Conduct](https://github.com/willtheorangeguy/.github/blob/main/CODE_OF_CONDUCT.md).

## License

MIT — see [LICENSE.md](LICENSE.md).
