# Grafana Dashboards

Provides several custom dashboards for Grafana.

If you update any files, please update this README and any links pointing to their sources, too.

## Airflow

* `component-airflow.json`  
  Custom dashboard manually created.

## OPA (Open Policy Agent)

* `component-opa.json`  
  Dashboard previously published at [Grafana Dashboards](https://grafana.com/grafana/dashboards/13965-metrics/) but was not updated to reflect the latest official changes within the [OPA contrib repository](https://github.com/open-policy-agent/contrib/tree/main/grafana-dashboard).  
  Thus, the dashboard was [downloaded directly from the repository](https://github.com/open-policy-agent/contrib/blob/86a67e2a11f415f24faf08104886b3ddd512ab64/grafana-dashboard/dashboard.json).

## PostgreSQL (CloudNativePG)

* `component-postgres-pooler.json`  
  Dashboard for the Pooler (bgBouncer).  
  Taken from an [issue-discussion](https://github.com/cloudnative-pg/grafana-dashboards/issues/7#issuecomment-3804857545) as there is no official one yet.
