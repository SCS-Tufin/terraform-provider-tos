# Resource `tos_uspe_v2`

The `tos_uspe_v2` Resource manages Unified Security Policy Exceptions (USPEs) from Tufin Aurora ST.

## Usage

```terraform
resource "tos_uspe_v2" "USPE_2" {
  domain          = "moon"
  name            = "USPE_2"
  ticket_id       = "123"
  requester       = "requester"
  approver        = "approver"
  expiration_date = "2024-12-31"
  description     = "USPE_2 tos.."

  source_networks = [
    "1.2.3.4/32",
    "1.2.3.0/24"
  ]

  source_zone {
     zone_id = data.tos_zones_v2.source_zones.zones[0].sid
  }
  
  source_zone {
    zone_name = data.tos_zones_v2.source_zones.zones[0].name
    domain    = "domain"
  }


  services = [
    "tcp",
    "udp"
  ]

  destination_networks = [
    "1.2.3.4/32",
    "1.2.3.0/24"
  ]

  destination_zone {
    zone_id = data.tos_zones_v2.destination_zones1.zones[0].sid
  }

  destination_zone {
    zone_name = data.tos_zones_v2.destination_zones.zones[0].name
    domain = "domain"
  }

  security_requirement {
    from_zone   = "from_zone"
    to_zone     = "to_zone"
    policy_name = "moon-default"
  }

  security_requirement {
    from_zone   = "from_zone2"
    to_zone     = "to_zone2"
    policy_name = "moon-default"
  }

  tags = merge(
    var.default_tags,
    {
      uspe_ST = format("%s", "USPE_2 tos")
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
* `description` - (Optional) The USPE Description.
* `comment` - (Optional) The Traffic Comment.
* `source_networks` - (Optional) The Source Networks.
* `source_zone` - (Optional) The Source Zone Block(s).
* `service` - (Optional) The Service Block(s).
* `destination_networks` - (Optional) The Destination Networks.
* `destination_zone` - (Optional) The Destination Zone Block(s).
* `security_requirement` - (Required) The Security Requirements.
* `tags` - (Optional) Resource Tags; see [Tags](../guides/121_tags.md) for details.

Either `source_networks` or `source_zone` must be set.
`source_zone` can be defined with `zone_id` or `zone_name` and `domain`.

Either `destination_networks` or `destination_zone` must be set.
`destination_zone` can be defined with `zone_id` or `zone_name` and `domain`.

## Attribute Reference

In addition to all arguments above, the following attributes are exported:

* `id` - The USPE Id.

### Example

```terraform
resource "tos_uspe_v2" "many_uspes" {
  approver    = "moon1"
  description = "description .."
  destination_networks = [
    "1.2.3.0/24",
    "1.2.3.4/32",
  ]

  destination_zone {
    zone_id = "zone_id"
  }

  destination_zone {
    zone_name = "zone_name"
    domain    = "domain"
  }
  
  domain          = "moon"
  expiration_date = "2024-12-31"
  id              = "J_P-7OG1TFyqBDP52-kxxx=="
  name            = "USPE_Number_0199"
  requester       = "requester"
  services = [
    "tcp",
    "udp",
  ]
  source_networks = [
    "1.2.3.0/24",
    "1.2.3.10/32",
    "1.2.3.4/32",
    "1.2.3.5/32",
  ]

  source_zone {
    zone_id = "zone_id"
  }

  source_zone {
    zone_name = "zone_name"
    domain    = "domain"
  }
  
  ticket_id = "123"

  security_requirement {
    from_zone   = "from_zone"
    policy_name = "moon-default"
    to_zone     = "to_zone"
  }
  security_requirement {
    from_zone   = "from_zone2"
    policy_name = "moon-default"
    to_zone     = "to_zone2"
  }
}
```

## Import

The `tos_uspe_v2` Resources are imported using the identifier `id,domain,name`.

### Example

```terraform
terraform import module.uspes.tos_uspe_v2.uspe1 1, moon
```
