# Resource `tos_service_group`

The `tos_service_group` Resource manages Application (Local) and Global Service Groups from Tufin SA.

## Usage

```terraform
resource "tos_service_group" "local_service_group_1" {
  name    = "local_service_group_1"
  app_id  = 999
  comment = "Test Application Local Service Group 1 .. Created by Terraform Provider TOS"
  members = [
    tos_service.local_service_1.services[0].id,
    tos_service.local_service_2.services[0].id
  ]
  tags = merge(
    var.default_tags,
    {
      name_SA = format("%s", "local_service_group_1")
    })
}
```

## Argument Reference

* `name` - (Required) The Service Name.
* `app_id` - (Optional) The Application Id required for an Application (Local) Service.
* `comment` - (Required) The Service Comment.
* `members` - (Required) The List of Service Group Member Ids.

## Attribute Reference

In addition to all arguments above, the following attributes are exported :

* `id` - The Service Id.

### Example

```terraform
resource "tos_service_group" "local_service_group_1" {
  app_id  = 999
  comment = "Test Application Local Service Group 1 .. Created by Terraform Provider TOS"
  id      = "12345"
  members = [
    123,
    321,
  ]
  name = "local_service_group_1"
  tags = {
    "description" = "Terraform Provider TOS Showcase Services"
    "env"         = "Tufin@Swisscom"
    "name_SA"     = "local_service_group_1"
    "origin"      = "provider-tufin-tba"
    "project"     = "Terraform Provider TOS"
    "version"     = "1.0.0"
  }
}
```
