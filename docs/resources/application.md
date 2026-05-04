# Resource `tos_application`

The `tos_application` Resource manages Applications in Tufin SC.

## Usage

```terraform
resource "tos_application" "application_1" {
  customer = var.customer
  name     = "APP_1"
  comment  = "APP 1 .."

  owner   = "OwnerName"
  editors = [
    "Editor X",
    "Editor Y",
    "Editor UserGroup"
  ]
  viewers = [
    "Viewer X",
    "Viewer Y",
    "Viewer UserGroup"
  ]

  tags = merge(
    var.default_tags,
    {
      application_SC = format("%s", "APP_1")
    })
}
```

## Argument Reference

* `customer` - (Required) The Customer Name.
* `name` - (Required) The Application Name.
* `comment` - (Required) The Application Comment.
* `owner` - (Required) The Application Owner.
* `editors` - (Required) The Application Editors.
* `viewers` - (Required) The Application Viewer.
* `tags` - (Optional) Resource Tags; see [Tags](../guides/121_tags.md) for details.

## Attribute Reference

In addition to all arguments above, the following attributes are exported:

* `id` - The Application Id.
* `domain` - The Application Domain (Customer).

### Example

```terraform
resource "tos_application" "application_1" {
  id      = "1"
  domain  = "moon"
  name    = "APP_1"
  comment = "App 1 .."
  owner   = "owner1"
  editors = [
    "editor1",
    "editor2",
  ]
  viewers = [
    "viewer1",
  ]
  tags = {
    "application_SC" = "Test App 2"
    "description"    = "Terraform Provider TOS Showcase Applications"
    "env"            = "Tufin@me"
    "origin"         = "provider-tufin-tba"
    "project"        = "Terraform Provider TOS"
    "version"        = "1.0.0"
  }
}
```

## Import

The `tos_application` Resources are imported using the identifier `id`.

### Example

```terraform
terraform import module.applications.tos_application.application_import 774
```
