# Data Source `tos_application_connections`

The `tos_application_connections` Data Source lists Application Connections from Tufin SA.

## Usage

```terraform
data "tos_application_connections" "application_connections" {
  name = "Application Connection 1"

  customer = var.customer
  app      = var.app
}
```

## Argument Reference

* `name` - (Required) Name (Wildcard) of the Application Connections to be listed.
* `customer` - (Required) The Customer Name.
* `app` - (Required) The Application Name.

## Attribute Reference

In addition to all arguments above, the following attributes are exported.

List of matching Application Connections from Tufin SA:

* `id` - Application Connection Id.
* `name` - Application Connection Name.
* `sources`- Source Servers of the Application Connection with list servers each containing:
    * `id` - Server Id.
    * `name` - Server Name.
* `services`- Services of the Application Connection with list services each containing:
    * `id` - Service Id.
    * `name` - Service Name.
* `destinations`- Destination Servers of the Application Connection with list of servers each containing:
    * `id` - Server Id.
    * `name` - Server Name.
* `comment`- Application Connection Comment.

### Example

```terraform
application_connections = [
  {
    comment      = "Application Connection 1 .."
    destinations = [
      {
        id   = 1
        name = "MILKYWAY_1"
      },
      {
        id   = 2
        name = "MARS_1"
      },
    ]
    id       = 3
    name     = "Application Connection 1"
    services = [
      {
        id   = 4
        name = "http"
      },
      {
        id   = 5
        name = "https"
      },
    ]
    sources = [
      {
        id   = 6
        name = "MARS_1"
      },
    ]
  },
]
```
