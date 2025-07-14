# Data Source `tos_uspes_v2`

The `tos_uspes_v2` Data Source lists Unified Security Policy Exceptions (USPEs) from Tufin Aurora ST.

## Usage

```terraform
data "tos_uspes_v2" "uspes_by_domain" {
  domain = "moon"
  index  = 0
  size   = 100
}
}
```

## Argument Reference

* `domain` - (Required) The Domain Name.
* `index` - (Optional) Start Index (default 0).
* `size` - (Optional) Number of USPEs to deliver (default 10).

## Attribute Reference

In addition to all arguments above, the following attributes are exported.

List of matching USPEs from Tufin ST (see Tufin ST API doc for detailed description).

### Example

```terraform
data "tos_uspes_v2" "uspes_by_domain" {
  domain = "moon"
  id     = "uspes_1724672127"
  index  = 0
  size   = 1
  uspes = [
    {
      __typename  = "UspTrafficException"
      approver    = "Approver X"
      creator     = "script"
      description = "description .."
      destinations = [
        "1.2.3.4/32",
        "1.2.3.5/32",
      ]
      disabled = false
      domain = {
        "id"   = "mCFhsaWQ1_0CymtjF8Rxxx=="
        "name" = "moon"
      }
      id      = "094w6n9RTpyu4GDq1WTxxx=="
      invalid = false
      name    = "EXC-123"
      services = [
        "tcp 1522-1524",
      ]
      sid = "094w6n9RTpyu4GDq1WTxxx=="
      sources = [
        "1.2.3.4/32",
        "1.2.3.5/32",
      ]
      ticket_id    = "123"
      time_created = "2024-08-14T08:50:08Z"
      time_end     = "2030-12-31T23:59:59Z"
      time_start   = "2024-08-14T00:00:00Z"
      usps = [
        {
          usp = {
            "id"   = "YHvjcGfvT1-aCjnqpfYxxx=="
            "name" = "moon-default"
            "sid"  = "YHvjcGfvT1-aCjnqpfYxxx=="
          }
          zone_pairs = [
            {
              from_zone = {
                "id"   = "M1-i8Mb7TxWTWmW3hSoxxx=="
                "name" = "zone1"
                "sid"  = "M1-i8Mb7TxWTWmW3hSoIwg=="
              }
              to_zone = {
                "id"   = "PGisLFkPRN-JudDupibxxx=="
                "name" = "zone2"
                "sid"  = "PGisLFkPRN-JudDupibxxx=="
              }
            },
          ]
        },
      ]
    }
  ]
}
```