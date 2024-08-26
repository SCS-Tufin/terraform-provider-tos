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

  services = [
    "tcp",
    "udp"
  ]

  destination_networks = [
    "1.2.3.4/32",
    "1.2.3.0/24"
  ]

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
* `tags` - (Optional) Resource Tags; see [Tags](tag.md) for details.

Either `source_networks` or `source_zone` must be set (but not both).

Either `destination_networks` or `destination_zone` must be set (but not both).

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
  domain          = "moon"
  expiration_date = "2024-12-31"
  id              = "J_P-7OG1TFyqBDP52-kxxx=="
  name            = "USPE_Number_0199"
  requester       = "taaroch0"
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
