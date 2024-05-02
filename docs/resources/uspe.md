# Resource `tos_uspe`

The `tos_uspe` Resource manages Unified Security Policy Exceptions (USPEs) from Tufin ST.

## Usage

```terraform
resource "tos_uspe" "uspe1" {
  domain       = "moon"
  name         = "USPE_1"
  ticket_id    = "123"
  requested_by = "requester"
  approved_by  = "approver"
  expiration_date = "2024-12-31"

  source_networks = []
  source_zone_ids = [
    1,
    2,
    3
  ]
  source_zone {
    zone_name = "TestZone1"
    domain    = "mars"
  }
  
  service {
    protocol = "tcp"
    port     = "22"
  }

  destination_networks = [
    "1.2.3.4/32"
  ]
  destination_zone_ids = []

  security_requirement {
    from_domain = "mars"
    from_zone   = "zone1"
    to_domain   = "venus"
    to_zone     = "zone2"
    policy_name = "default-policy"
  }

  tags = merge(
    var.default_tags,
    {
      uspe_ST = format("%s", "USPE_1")
    })
}
```

## Argument Reference

* `domain` - (Required) The Domain Name.
* `name` - (Required) The USPE Name.
* `ticket_id` - (Optional) The Ticket Id.
* `requested_by` - (Optional) The Requester.
* `approved_by` - (Optional) The Approver.
* `expiration_date` - (Optional) The Expiration Date.
* `source_networks` - (Required) The Source Networks.
* `source_zone_ids` - (Required) The Source Zone Ids.
* `source_zone` - (Required) The Source Zone Block(s).
* `service` - (Optional) The Service Block(s).
* `destination_networks` - (Required) The Destination Networks.
* `destination_zone_ids` - (Required) The Destination Zone Ids.
* `destination_zone` - (Required) The Destination Zone Block(s).
* `tags` - (Optional) Resource Tags; see [Tags](tag.md) for details.

Either `source_networks` or `source_zone_ids` and `source_zone` must be set (but not both).

Either `destination_networks` or `destination_zone_ids` and `destination_zone` must be set (but not both).

## Attribute Reference

In addition to all arguments above, the following attributes are exported:

* `id` - The USPE Id.

### Example

```terraform
resource "tos_uspe" "uspe1" {
  domain       = "moon"
  name         = "USPE_1"
  ticket_id    = "123"
  requested_by = "requester"
  approved_by  = "approver"
  expiration_date = "2024-12-31"

  source_zone_ids = [
    data.tos_zones.source_zones.zones[0].id,
  ]

  service {
    protocol = "tcp"
    port     = "22"
  }

  destination_zone_ids = [
    data.tos_zones.destination_zones.zones[0].id,
  ]

  security_requirement {
    from_domain = "mars"
    from_zone   = "zone1"
    to_domain   = "venus"
    to_zone     = "zone2"
    policy_name = "default-policy"
  }

  tags = merge(
    var.default_tags,
    {
      uspe_ST = format("%s", "USPE_1")
    })
}
```

## Import

The `tos_uspe` Resources are imported using the identifier `id,domain,name`.

### Example

```terraform
terraform import module.uspes.tos_uspe.uspe1 1, moon
```
