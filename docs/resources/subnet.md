# Resource `tos_subnet`

The `tos_subnet` Resource manages Subnet Network Objects in Tufin SA.

## Usage

```terraform
resource "tos_subnet" "milkyway" {
  customer = var.customer
  app      = var.app

  name    = "MILKYWAY_1"
  ip      = "1.2.3.0/28"
  comment = "Test Subnet MILKYWAY 1 .."
  tags    = merge(
    var.default_tags,
    {
      network_object_SA = format("%s", "MILKYWAY_1")
    })
}
```

## Argument Reference

* `customer` - (Required) The Customer Name.
* `app` - (Required) The Application Name.
* `name` - (Required) The Subnet Name.
* `ip` - (Required) The Subnet CIDR.
* `comment` - (Required) The Range Comment.
* `tags` - (Optional) Resource Tags; see [Tags](../guides/121_tags.md) for details.

## Attribute Reference

In addition to all arguments above, the following attributes are exported:

* `id` - The Subnet Id.

### Example

```terraform
resource "tos_subnet" "milkyway" {
  app      = "Cloud"
  comment  = "Test Subnet MILKYWAY 1 .. Created by Terraform Provider TOS"
  customer = "moon"
  id       = "1"
  ip       = "1.2.3.0/28"
  name     = "MILKYWAY_1"
  tags     = {
    "description"       = "Terraform Provider TOS Showcase Network Objects"
    "env"               = "Tufin@me"
    "network_object_SA" = "MILKYWAY_1"
    "origin"            = "provider-tufin-tba"
    "project"           = "Terraform Provider TOS"
    "version"           = "1.0.0"
  }
}
```

## Import

The `tos_subnet` Resources are imported using the identifier `id,customer,app`.

### Example

```terraform
terraform import module.networkobjects.tos_subnet.subnet_1 1, moon, Cloud
```


## Note

To avoid errors while creating subnet, don't forget to define subnet mask.