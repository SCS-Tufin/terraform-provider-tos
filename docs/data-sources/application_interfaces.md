# Data Source `tos_application_interfaces`

The `tos_application_interfaces` Data Source lists Application Interfaces from Tufin SA.

## Usage

```terraform
data "tos_application_interfaces" "application_interfaces" {
  customer = var.customer
  app      = var.app
}
```

## Argument Reference

* `customer` - (Required) The Customer Name.
* `app` - (Required) The Application Name.

## Attribute Reference

In addition to all arguments above, the following attributes are exported.

List of matching Application Interfaces (with Application Interface Connections) from Tufin SA:

* `id` - Application Interface Id.
* `name` - Application Interface Name.
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
application_interfaces = [
  {
    application_id        = 1
    comment               = "Cloud Tufin Interfaces .."
    id                    = 2
    interface_connections = [
      {
        comment      = ""
        destinations = [
          {
            comment = ""
            id      = 3
            name    = "MARS"
            type    = "group"
          },
        ]
        id       = 4
        name     = "Cloud-Interfaces"
        services = [
          {
            comment  = ""
            global   = false
            id       = 5
            max      = 0
            min      = 0
            name     = "tcp8443"
            protocol = 0
            timeout  = ""
            type     = ""
          },
          {
            comment  = ""
            global   = false
            id       = 6
            max      = 0
            min      = 0
            name     = "tcp7443"
            protocol = 0
            timeout  = ""
            type     = ""
          },
          {
            comment  = ""
            global   = false
            id       = 7
            max      = 0
            min      = 0
            name     = "tcp7543"
            protocol = 0
            timeout  = ""
            type     = ""
          },
        ]
        sources = []
      },
    ]
    name      = "Cloud-Interfaces"
    published = false
  },
  {
    application_id        = 8
    comment               = "MARS .."
    id                    = 9
    interface_connections = [
      {
        comment      = "Application Interface Connection .."
        destinations = []
        id           = 10
        name         = "app_int_connection"
        services     = [
          {
            comment  = ""
            global   = false
            id       = 11
            max      = 0
            min      = 0
            name     = "http"
            protocol = 0
            timeout  = ""
            type     = ""
          },
          {
            comment  = ""
            global   = false
            id       = 12
            max      = 0
            min      = 0
            name     = "https"
            protocol = 0
            timeout  = ""
            type     = ""
          },
        ]
        sources = [
          {
            comment = ""
            id      = 13
            name    = "VENUS"
            type    = "group"
          },
        ]
      },
      {
        comment      = "Application Interface Connection .."
        destinations = [
          {
            comment = ""
            id      = 14
            name    = "VENUS"
            type    = "group"
          },
        ]
        id       = 15
        name     = "app_interface_connection"
        services = [
          {
            comment  = ""
            global   = false
            id       = 16
            max      = 0
            min      = 0
            name     = "https"
            protocol = 0
            timeout  = ""
            type     = ""
          },
        ]
        sources = []
      },
    ]
    name      = "app_interface"
    published = false
  },
]
```
