# Troubleshooting

| Symptom | Check |
| --- | --- |
| Scrape 401 | check plugin token and Prometheus credentials_file. |
| Temperature panels blank | inspect tool and bed identifier labels. |
| Progress absent while idle | this is expected until the plugin emits an active job. |

## First checks

Check the selected Grafana data source and dashboard variables in [configuration](configuration.md). For Prometheus, inspect the target state and the exact job and instance labels before changing panel queries.
