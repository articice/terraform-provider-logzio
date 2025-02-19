# Grafana Dashboard Provider

Provides a Logz.io Grafana dashboard resource. This can be used to create and manage Grafana dashboards in Logz.io.

* Learn more about Logz.io's Grafana dashboard API in [Logz.io Docs](https://docs.logz.io/api/#tag/Grafana-dashboards).

## Example Usage

```hcl
resource "logzio_grafana_dashboard" "my_dashboard" {
  dashboard_json = <<EOD
{
  "title": "a title",
  "uid": "my_dashboard_uid",
  "panels": []
}
EOD
  folder_uid = "my_folder_uid"
  message = "my message"
  overwrite = true
}
```

## Argument Reference

### Required:

* `folder_uid` - (String) The unique identifier (uid) of a folder to store your dashboard. You cannot use `General` folder or the folder generated by logz.io - `Logz.io Dashboards` - to place your alerts.
* `dashboard_json` - (String) The complete dashboard model, to create a new dashboard, in a JSON format. **Note** that your model should contain a `uid` field. Once created, you cannot change tha uid.

### Optional:

* `message` - (String) A commit message for the version history.
* `overwrite` - (Boolean) Set to true if you want to overwrite existing dashboard with newer version.

## Attribute Reference

* `dashboard_id` - (Int) The identifier (id) of a dashboard.
* `dashboard_uid` - (String) The unique identifier (uid) of a dashboard.
* `url` - (String) Dashboard url.
* `version` - (Int) Dashboard version.

### Import Logz.io Grafana Dashboard as Terraform resource

You can import existing dashboard as follows:

```
terraform import logzio_grafana_dashboard.my_dashboard <FETCHER-ID>
```