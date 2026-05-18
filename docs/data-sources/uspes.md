# Data Source `tos_uspes`

The `tos_uspes` Data Source lists Unified Security Policy Exceptions (USPEs) from Tufin Classic ST.

## Usage

```terraform
data "tos_uspes" "uspes_by_domain" {
  domain = "moon"
  index = 0
  size = 100
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
security_policy_exceptions = [
  {}
]
```