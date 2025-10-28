# Data Source `tos_applications`

The `tos_applications` Data Source lists Applications from Tufin SC.

## Usage

```terraform
data "tos_applications" "applications_by_name" {
  name = "mars"
}
```

## Argument Reference

* `name` - (Required) The Name of Applications to be listed.

## Attribute Reference

In addition to all arguments above, the following attributes are exported.

List of matching Applications from Tufin SC each containing:

* `id` - Application Id.
* `name` - Application Name.
* `comment`- Application Comment.
* `customer`- Application Customer.
* `owner`- Application Owner.
* `editors`- Application Editors.
* `viewers`- Application Viewers.

### Example

```terraform
applications = [
  {
    id       = 1
    name     = "mars"
    comment  = "Test Application"
    customer = "sun"
    owner    = "api"
    editors  = [
      "user1",
    ]
    viewers = [
      "user2",
    ]
  }
]
```
