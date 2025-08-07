# Data Source `tos_zones`

The `tos_zones` Data Source lists Zones from Tufin ST.

## Usage

```terraform
data "tos_zones" "zones_by_name" {
  name = "Zone1"

  domain = var.domain
}
```

## Argument Reference

* `name` - Name of the Zones to be listed (by matching string).
* `domain` - (Required) The Domain Name.

## Attribute Reference

In addition to all arguments above, the following attributes are exported.

List of matching Zones from Tufin ST each containing:

* `id` - Zone Id.
* `name` - Zone Name.
* `comment` - Zone Comment.

### Example

```terraform
zones  = [
  {
    comment = "Zone1 .."
    id      = 1
    name    = "Zone1"
  },
]
```
