# Resource 'tos_application_pack_tag'

The 'tos_application_pack_tag' Manages Application Pack Tags in Tufin SC

## Usage

```terraform
resource "tos_application_pack_tag" "app_pack_tag123" {
  customer = var.customer
  app_pack_id = 123
  app_pack_name = "ApplicationPackName"
  tag_name = "Tag1"
  tags = merge(
    var.default_tags,
    {
      name_SA = format("%s", "Application Pack Tag")
    })
}
```

## Argument Reference

* `customer` - (Required) The Customer Name.
* `app_pack_id` - (Optional) Application Pack ID.
* `app_pack_name` - (Optional) Application Pack Name.
* `tag_name` - (Required) The Tag Name.
* `tags` - (Optional) Resource Tags; see [Tags](../guides/121_tags.md) for details.

Either `app_pack_id` or `app_pack_name` must be set (but not both).

## Attribute Reference

In addition to all arguments above, the following attributes are exported:

* `id` - The Application Pack Tag Id.

### Example 

```terraform
resource "tos_application_pack_tag" "app_pack_tag123" {
  customer = moon
  app_pack_name = "UNIVERSE"
  tag_name = "VENUS_1"
  tags = merge(
    var.default_tags,
    {
      name_SA = format("%s", "Application Pack Tag")
    })
}
```