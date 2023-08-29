# Data Source `tos_networksuffixes`

The `tos_networksuffixes` Data Source lists Network Suffixes from Tufin Backend API.
only valid in Mode 'tba'.

## Usage

```terraform
data "tos_networksuffixes" "networksuffixes_by_network" {
  network = "1.2.3.4/31"

  customer = var.customer
}

```

## Argument Reference

* `network` - (Required) The Network to get the Network Suffix for.
* `customer` - (Required) The Customer Name.

## Attribute Reference

In addition to all arguments above, the following attributes are exported.

List of matching Network Suffixes from Tufin Backend API:

* `id` - Network Suffix Id.
* `network` - Network.
* `suffix` - Suffix.
* `connected_domains`- List of Connected Domains.
* `comment` - Comment.

### Example`

```terraform
data "tos_networksuffixes" "networksuffixes_by_network" {
  customer        = "scs0"
  id              = "networksuffixes"
  network         = "1.2.3.4/31"
  networksuffixes = [
    {
      comment           = "test"
      connected_domains = [
        "htc0",
        "htc1",
      ]
      id                = 1
      network           = "1.2.3.0/16"
      suffix            = "uco"
    },
  ]
}
```


