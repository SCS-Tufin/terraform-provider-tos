# Resource `tos_uspe`

The `tos_uspe` Resource manages Unified Security Policy Exceptions (USPEs) from Tufin Classic ST.

## Usage

```terraform
resource "tos_uspe_v2" "USPE_2" {
  domain          = "htc1"
  name            = "USPE_2"
  ticket_id       = "123"
  requester       = "taaroch0"
  approver        = "taaroch1"
  expiration_date = "2024-12-31"
  description     = "USPE_2 tos.."

  source_networks = [
    "1.2.3.4/32",
    "1.2.3.0/24"
  ]

  services = [
    "tcp",
    "udp"
  ]

  destination_networks = [
    "1.2.3.4/32",
    "1.2.3.0/24"
  ]

  security_requirement {
    from_zone   = "ctdcg_ss1"
    to_zone     = "ctdcg_aze"
    policy_name = "htc1-default"
  }

  security_requirement {
    from_zone   = "ctdcg_ss2"
    to_zone     = "ctdcg_aze"
    policy_name = "htc1-default"
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
* `source_networks` - (Required) The Source Networks.
* `source_zone` - (Required) The Source Zone Block(s).
* `service` - (Optional) The Service Block(s).
* `destination_networks` - (Required) The Destination Networks.
* `destination_zone` - (Required) The Destination Zone Block(s).
* `tags` - (Optional) Resource Tags; see [Tags](tag.md) for details.

Either `source_networks` or `source_zone` must be set (but not both).

Either `destination_networks` or `destination_zone` must be set (but not both).

## Attribute Reference

In addition to all arguments above, the following attributes are exported:

* `id` - The USPE Id.

### Example

```terraform
resource "tos_uspe" "uspe1" {
  domain          = "moon"
  name            = "USPE_1"
  ticket_id       = "123"
  requested_by    = "requester"
  approved_by     = "approver"
  expiration_date = "2024-12-31"
  description     = "USPE Description .."
  comment         = "Traffic Comment .."
  
  source_zone {
    zone_name = "zone1"
    domain    = "moon"
  }
  source_zone {
    zone_id = 123
    domain  = "moon"
  }
  source_zone {
    zone_name = "zone3"
    domain    = "mars"
  }

  service {
    protocol = "tcp"
    port     = "22"
  }

  destination_zone {
    zone_name = "zone4"
    domain    = "mars"
  }

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
