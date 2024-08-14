# Resource `tos_service`

The `tos_service` Resource manages Application (Local) and Global Services from Tufin SA.

## Usage

```terraform
resource "tos_service" "service_1" {
  name    = "test_golbal_service1"
  type    = "tcp_service"
  min     = 500
  max     = 512
  comment = "Test Global Service 1 .. Created by Terraform Provider TOS"

  tags = merge(
    var.default_tags,
    {
      name_SA = format("%s", "test_golbal_service1")
    })
}
```

## Argument Reference

* `name` - (Required) The Service Name.
* `app_id` - (Optional) The Application Id required for an Application (Local) Service.
* `type` - (Required) The Service Type.
* `min` - (Required) The min Range Value.
* `max` - (Required) The max Range Value.
* `comment` - (Required) The Service Comment.
* `tags` - (Optional) Resource Tags; see [Tags](tag.md) for details.

## Attribute Reference

In addition to all arguments above, the following attributes are exported:

* `id` - The Service Id.

### Example

```terraform
resource "tos_service" "service_1" {
  name    = "test_golbal_service1"
  type    = "tcp_service"
  min     = 500
  max     = 512
  comment = "Test Global Service 1 .. Created by Terraform Provider TOS"

  tags = merge(
    var.default_tags,
    {
      name_SA = format("%s", "test_golbal_service1")
    })
}
```
