# Resource `tos_connection_to_application_pack`

The `tos_application` Resource manages Connections to Application Packs in Tufin SC.

## Usage

```terraform
resource "tos_connection_to_application_pack" "connection_to_application_pack1" {
  customer = var.customer
  app      = var.app
  name     = "PACK_3"
  comment  = "PACK 3 .."

  application_pack {
    id       = 367
    customer = "moon"
  }

  network_objects_tag {
    network_objects = [
      "MARS_1",
    ]
    tag = "Internet-IP-1"
  }

  create_ticket = "new"
  
  tags = merge(
    var.default_tags,
    {
      connection_to_application_pack_SA = format("%s", "PACK_2")
    })
}
```

## Argument Reference

* `customer` - (Required) The Customer Name.
* `app` - (Required) The Application Name.
* `name` - (Required) The Connection to Application Pack Name.
* `comment` - (Required) The Connection to Application Pack Comment.
* `customer` - (Required) The Connection to Application Pack Customer.
* `server_tags` - (Required) The Server Tags.
* `application_pack` - (Required) The Application Pack Block.
* `network_objects_tag` - (Required) The Network Objects Tag Block(s).
* `tags` - (Optional) Resource Tags; see [Tags](tag.md) for details.
* `create_ticket` - (Optional) Create ticket for the connection. Use "new" to Create a ticket for pushing changes to firewall. Use "closed" to create a Closed Ticket. Closed ticket will not affect the firewalls.

## Attribute Reference

In addition to all arguments above, the following attributes are exported:

* `id` - The Connection to Application Pack Id.

### Example

```terraform
resource "tos_connection_to_application_pack" "connection_to_application_pack1" {
  app      = "Cloud"
  comment  = "comment on conn_to_app_AppPack_1"
  customer = "moon"
  id       = "1"
  name     = "conn_to_app_AppPack_1"
  tags     = {
    "connection_to_application_pack_SA" = "conn_to_app_AppPack_1"
    "description"                       = "Terraform Provider TOS Showcase Connection to Application Packs"
    "env"                               = "Tufin@Swisscom"
    "origin"                            = "provider-tufin-tba"
    "project"                           = "Terraform Provider TOS"
    "version"                           = "1.0.0"
  }

  ticket_info     = [
    {
      create_ticket = "new"
      id            = 6
      subject       = "AUT-ADD-"
      warnings      = []
    },
    
  application_pack {
    customer = "sun"
    id       = 2
  }

  network_objects_tag {
    network_objects = [
      "ASTEROIDS_1",
    ]
    tag = "Internet-IP-2"
  }
  network_objects_tag {
    network_objects = [
      "RANGE_1",
      "MARS_1",
    ]
    tag = "Internet-IP-1"
  }
}
```