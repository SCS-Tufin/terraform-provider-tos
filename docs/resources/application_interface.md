# Resource `tos_application_interface`

The `tos_application_interface` Resource manages Application Interfaces in Tufin SA.

## Usage

```terraform
resource "tos_application_interface" "application_interface1" {
  name    = "app_interface_1"
  comment = "app interface 1 .."

  application_pack_id = length(data.tos_application_packs.packs_for_interface.application_packs) > 0 ?data.tos_application_packs.packs_for_interface.application_packs[0].id : 0
  tag                 = length(data.tos_application_packs.packs_for_interface.application_packs[0].tags) > 0 ? data.tos_application_packs.packs_for_interface.application_packs[0].tags[0] : ""

  domain = var.domain
  app    = var.app

  interface_connection {
    name    = "app_interface_connection_1"
    comment = "app interface connection 1 .."

    sources = [
      "VENUS_1",
      "MARS_1",
      "UNIVERSE",
    ]
    services = [
      "http",
      "https",
    ]
  }

  interface_connection {
    name    = "app_interface_connection_NEWer"
    comment = "app interface connection NEWer .."

    services = [
      "http",
    ]
    sources = [
      "MARS_1",
    ]
  }

  tags = merge(
    var.default_tags,
    {
      application_interface_SA = format("%s", "app interface 1")
    })
}
```

## Argument Reference

* `domain` - (Required) The Domain Name.
* `app` - (Required) The Application Name.
* `name` - (Required) The Application Interface Name.
* `comment` - (Required) The Application Interface Comment.
*
* `application_pack_id` - (Required) The Application Pack Id to connect the Application Interface to.
* `tag` - (Optional) The Tag Name used in the Application Pack Connection (defaults to Application Interaface Name).
* 
* `interface_connection` - (Required) Application Interface Connection Block(s) with
* `name` - (Required) The Application Interface Connection Name.
* `comment` - (Required) The Application Interface Connection Comment.
* `sources` - (Required) The Application Interface Connection Sources (by Name); either `sources` or `destinations` are
  allowed but not both.
* `services` - (Required) The Application Interface Connection Services (by Name).
* `destinations` - (Required) The Application Interface Connection Destinations (by Name); either `sources`
  or `destinations` are allowed but not both.

* `tags` - (Optional) Resource Tags; see [Tags](tag.md) for details.

## Attribute Reference

In addition to all arguments above, the following attributes are exported:

* `id` - The Application Interface Id.

### Example

```terraform
resource "tos_application_interface" "application_interface1" {
  app                 = "Cloud"
  application_pack_id = 1438
  comment             = "app interface 1 .."
  domain              = "scs0"
  id                  = "242"
  name                = "app_interface_1"
  tag                 = "app_interface_1"
  tags                = {
    "application_interface_SA" = "app interface 1"
    "description"              = "Terraform Provider TOS Showcase Application Interfaces"
    "env"                      = "Tufin@Swisscom"
    "origin"                   = "provider-tufin-tba"
    "project"                  = "Terraform Provider TOS"
    "version"                  = "1.0.0"
  }

  interface_connection {
    comment      = "app interface connection 1 .."
    destinations = []
    name         = "app_interface_connection_1"
    services     = [
      "http",
      "https",
    ]
    sources = [
      "VENUS_1",
      "MARS_1",
      "UNIVERSE",
    ]
  }
  interface_connection {
    comment      = "app interface connection 2 .."
    destinations = [
      "RANGE_1",
      "MARS_1",
      "VENUS_1",
    ]
    name     = "app_interface_connection_2"
    services = [
      "https",
    ]
    sources = []
  }
  interface_connection {
    comment      = "app interface connection NEWer .."
    destinations = []
    name         = "app_interface_connection_NEWer"
    services     = [
      "http",
    ]
    sources = [
      "MARS_1",
    ]
  }
}
```

