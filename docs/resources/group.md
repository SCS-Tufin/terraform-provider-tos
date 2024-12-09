# Resource `tos_group`

The `tos_group` Resource manages Groups of Network Objects (Servers, Subnets, Ranges) in Tufin SA.

## Usage

```terraform
resource "tos_group" "group_1" {
  customer = var.customer
  app      = var.app

  name    = "GROUP_1"
  comment = "GROUP 1 .."

  members = [
    "ASTEROIDS_1",
    "MARS_1",
    "MILKYWAY_1",
    "PLUTO_1",
  ]

  create_ticket = "new"
  
  tags = merge(
    var.default_tags,
    {
      network_object_SA = format("%s", "GROUP_1")
    })
}
```

## Argument Reference

* `customer` - (Required) The Customer Name.
* `app` - (Required) The Application Name.
* `name` - (Required) The Group Name.
* `comment` - (Required) The Group Comment.
* `members` - (Required) The Group Members.
* `tags` - (Optional) Resource Tags; see [Tags](tag.md) for details.
* `create_ticket` - (Optional) Create ticket for the connection. Use "new" to Create a ticket for pushing changes to firewall. Use "closed" to create a Closed Ticket. Closed ticket will not affect the firewalls.



## Attribute Reference

In addition to all arguments above, the following attributes are exported:

* `id` - The Group Id.

### Example

```terraform
resource "tos_group" "group_1" {
  id       = "1"
  customer = "moon"
  app      = "Cloud"
  name     = "GROUP_1"
  comment  = "GROUP 1 .."
  members  = [
    "ASTEROIDS_1",
    "MARS_1",
    "MILKYWAY_1",
    "PLUTO_1",
  ]

  ticket_info     = [
    {
      create_ticket = "new"
      id            = 6
      subject       = "AUT-ADD-"
      warnings      = []
    },
  
  tags = {
    "description"       = "Terraform Provider TOS Showcase Network Objects"
    "env"               = "Tufin@me"
    "network_object_SA" = "GROUP_1"
    "origin"            = "provider-tufin-tba"
    "project"           = "Terraform Provider TOS"
    "version"           = "1.0.0"
  }
}
```