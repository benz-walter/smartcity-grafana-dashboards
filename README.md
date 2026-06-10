# Grafana Dashboards

Provides several custom dashboards for Grafana.

If you update any files, please update this README and any links pointing to their sources, too.

# Dashboards

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


# Update/Export/Import dashboards

To update the provided dashboards, some steps need to be considered.  
The workflow might improve in the future; however, right now it is important to export the dashboards as JSON in V2 format, excluding any internal attributes.  
As provisioned dashboards might not be editable at all and the export option only works after saving changes, the following steps proved to be working for any edge-cases.

1. Select the provisioned dashboard in your Grafana instance you want to update.
2. Enter the edit mode and make any changes you like
3. **Save as copy** to a new dashboard
4. **Export as code** this newly created dashboard.
   * Advances options: Select _V2 Resource_ as the model
   * Advances options: Select _JSON_ as the format
   * Activate _Share dashboard with another instance_
5. Replace the content of the dashboard's file with your exported JSON
   * Revert `metadata.name`. This is the unique identifier, otherwise Grafana might create a duplicated dashboard.
   * Revert and increase `metadata.generation`.
6. Commit your changes

Restart your Grafana instance so that the sidecar pulls the dashboards from the repository again.

If it happens that the dashboard does not update, check that GitHub refreshed the HTTP cache,
as sometimes older versions are still being provided if the commit and pull are done within seconds.
This can happen if the URL used to pull does not change between commits (e.g., directly pointing to the `main` version without a hash) 
