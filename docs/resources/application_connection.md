# Resource `tos_application_connection`

The `tos_application_connection` Resource manages Application Connections in Tufin SA.

## Usage

```terraform
resource "tos_application_connection" "application_connection1" {
  count = length(data.tos_networkobjects.sources.networkobjects) > 0 && length(data.tos_networkobjects.sources.networkobjects) > 0 && length(data.tos_services.services.services) > 0  ? 1 : 0

  name       = "Application Connection 1"
  source_ids = [
    data.tos_networkobjects.sources.networkobjects[0].id,
  ]

  destination_ids = [
    data.tos_networkobjects.sources.networkobjects[0].id,
    data.tos_networkobjects.destinations.networkobjects[0].id,
  ]

  service_ids = [
    data.tos_services.services.services[0].id,
    data.tos_services.services2.services[0].id
  ]

  comment       = "Application Connection 1 .."
  create_ticket = true

  customer = var.customer
  app      = var.app

  tags = merge(
    var.default_tags,
    {
      application_connection_SA = format("%s", "Application Connection 1")
    })
}
```

## Argument Reference

* `customer` - (Required) The Customer Name.
* `app` - (Required) The Application Name.
* `name` - (Required) The Application Connection Name.
* `comment` - (Required) The Application Connection Comment.
* `source_ids` - (Required) The Application Connection's Source Server Ids.
* `service_ids` - (Required) The Application Connection's Service Server Ids.
* `destination_ids` - (Required) Application Connection's Destination Server Ids.
* `tags` - (Optional) Resource Tags; see [Tags](tag.md) for details.

## Attribute Reference

In addition to all arguments above, the following attributes are exported:

* `id` - The Application Connection Id.

### Example

```terraform
resource "tos_application_connection" "application_connection1" {
  id       = "1"
  customer = "sun"
  app      = "mars"

  name    = "Application Connection 1"
  comment = "Application Connection 1 .."

  source_ids = [
    1,
    2,
  ]
  service_ids = [
    3,
    4,
  ]
  destination_ids = [
    5,
  ]
  tags = {
    "description"               = "Terraform Provider TOS Showcase Application Connection Objects"
    "env"                       = "Tufin@me"
    "origin"                    = "provider-tufin-tba"
    "project"                   = "Terraform Provider TOS"
    "application_connection_SA" = "Application Connection 1"
    "version"                   = "1.0.0"
  }
}
```

## Import

The `tos_application_connection` Resources are imported using the identifier `id,customer,app`.

### Example

```terraform
terraform import module.networkobjects.tos_application_connection.application_connection_1 1, moon, App1
```
