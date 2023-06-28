# Data Source `tos_application_interfaces`

The `tos_application_interfaces` Data Source lists Application Interfaces from Tufin SA.

## Usage

```terraform
data "tos_application_interfaces" "application_interfaces" {
  domain = var.domain
  app    = var.app
}
```

## Argument Reference

* `domain` - (Required) The Domain Name.
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
    application_id        = 538
    comment               = "Cloud Tufin Interfaces .."
    id                    = 129
    interface_connections = [
      {
        comment      = ""
        destinations = [
          {
            comment = ""
            id      = 19148
            name    = "draco-242-dolomit-tufint-int_ora-opn_dco_Tufin-Tools-INT"
            type    = "group"
          },
        ]
        id           = 1502
        name         = "Cloud-Tufin-Interfaces"
        services     = [
          {
            comment  = ""
            global   = false
            id       = 270
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
            id       = 1265
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
            id       = 4717
            max      = 0
            min      = 0
            name     = "tcp7543"
            protocol = 0
            timeout  = ""
            type     = ""
          },
        ]
        sources      = []
      },
    ]
    name                  = "Cloud-Tufin-Interfaces"
    published             = false
  },
  {
    application_id        = 538
    comment               = "app app_interface_riccardo .."
    id                    = 207
    interface_connections = [
      {
        comment      = "app interface connection 1 modified"
        destinations = []
        id           = 2781
        name         = "app_int_connection_1_modified"
        services     = [
          {
            comment  = ""
            global   = false
            id       = 83
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
            id       = 85
            max      = 0
            min      = 0
            name     = "https"
            protocol = 0
            timeout  = ""
            type     = ""
          },
        ]
        sources      = [
          {
            comment = ""
            id      = 19148
            name    = "draco-242-dolomit-tufint-int_ora-opn_dco_Tufin-Tools-INT"
            type    = "group"
          },
        ]
      },
      {
        comment      = "app interface connection riccardo ..."
        destinations = [
          {
            comment = ""
            id      = 19148
            name    = "draco-242-dolomit-tufint-int_ora-opn_dco_Tufin-Tools-INT"
            type    = "group"
          },
        ]
        id           = 2769
        name         = "app_interface_connection_ric"
        services     = [
          {
            comment  = ""
            global   = false
            id       = 85
            max      = 0
            min      = 0
            name     = "https"
            protocol = 0
            timeout  = ""
            type     = ""
          },
        ]
        sources      = []
      },
    ]
    name                  = "app_interface_riccardo"
    published             = false
  },
]
```
