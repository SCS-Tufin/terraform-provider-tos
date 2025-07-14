# Resource `tos_connection_to_application_interface`

The `tos_connection_to_application_interface` Resource manages Connections to Application Interfaces in Tufin SC.

## Usage

```terraform
resource "tos_connection_to_application_interface" "conn_to_app_interface1" {
  customer = var.customer
  app      = var.app

  name                     = "CTAI1"
  comment                  = "Connection to Application Interface 1, CTAI1"
  application_interface_id = 162

  servers = [
    "MARS_1",
    "VENUS_1",
    "UNIVERSE",
    "SATURN_2",
    "SATURN_1",
  ]

  tags = merge(
    var.default_tags,
    {
      name_SA = format("%s", "Connection to Application Interface 1, CTAI1")
    })
}
```

## Argument Reference

* `customer` - (Required) The Customer Name.
* `app` - (Required) The Application Name.
* `name` - (Required) The Connection to Application Interface Name.
* `comment` - (Required) The Connection to Application Interface Comment.
* `application_interface_id` - (Required) The Application Interface Id.
* `servers` - (Required) The Servers.
* `tags` - (Optional) Resource Tags; see [Tags](../guides/121_tags.md) for details.

## Attribute Reference

In addition to all arguments above, the following attributes are exported:

* `id` - The Connection to Application Interface Id.

### Example

```terraform
resource "tos_connection_to_application_interface" "conn_to_app_interface1" {
  customer = var.customer
  app      = var.app

  name                     = "CTAI1"
  comment                  = "Connection to Application Interface 1, CTAI1"
  application_interface_id = 162

  servers = [
    "MARS_1",
    "VENUS_1",
    "UNIVERSE",
    "SATURN_2",
    "SATURN_1",
  ]

  tags = merge(
    var.default_tags,
    {
      name_SA = format("%s", "Connection to Application Interface 1, CTAI1")
    })
}
```