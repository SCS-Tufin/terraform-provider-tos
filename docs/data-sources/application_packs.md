# Data Source `tos_application_packs`

The `tos_application_packs` Data Source lists Application Packs from Tufin SC.

## Usage

```terraform
data "tos_application_packs" "application_packs_by_name" {
  customers = [
    "moon",
    "sun"
  ]
  name = "App"
}
```

## Argument Reference

* `customers` - (Required) The List of Customers to list Application Packs from.
* `name` - (Required) The Name (regex) of Application Packs to be listed.

## Attribute Reference

In addition to all arguments above, the following attributes are exported.

List of matching Application Packs from Tufin SC each containing:

* `id` - Application Pack Id.
* `name` - Application Pack Name.
* `comment`- Application Pack Comment.
* `interfaces` - List of Application Interfaces with Interface Name and Tag.

### Example

```terraform
application_packs = [
  {
    id       = 1
    comment  = "Tag Comment .."
    name     = "AppPack moon"
    customer = "moon"
    interfaces     = {
      name = "Application Interfaces Name"
      tag = "Tag Name"
    }
  },
]
```

