# Data Source `tos_zone_entries`

The `tos_zone_entries` Data Source lists Zone Entries from Tufin ST.

## Usage

```terraform
data "tos_zone_entries" "zone_id" {
  zone_id   = 1
  zone_name = "Zone1"

  domain = var.domain
}
```

## Argument Reference

* `zone_id` - Id of the Zone for which the Zone Entries to be listed.
* `zone_name` - Name of the Zone for which the Zone Entries to be listed.
* `domain` - (Required) The Domain Name.

Either `zone_id` or `zone_name` must be set (but not both).

## Attribute Reference

In addition to all arguments above, the following attributes are exported.

List of matching Zone Entries from Tufin ST each containing:

* `id` - Zone Entry Id.
* `zone_id` - Zone Id.
* `ip` - Ip.
* `netmask` - Netmask.
* `prefix` - Prefix.
* `comment` - Zone Comment.

### Example

```terraform
zone_entries = [
  {
    id      = 1
    zone_id = 2
    ip      = "10.217.127.192"
    netmask = "255.255.255.248"
    prefix  = "29"
    comment = "Comment .."
  }
]
```
