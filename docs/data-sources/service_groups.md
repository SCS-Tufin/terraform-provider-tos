# Data Source `tos_service_groups`

The `tos_service_groups` Data Source lists Global Service Groups from Tufin SA.

## Usage

```terraform
data "tos_service_groups" "service_groups_by_name" {
  name         = "ServiceGroup"
  globals_only = false
  app_id       = 123
}
```

## Argument Reference

* `name` - Name (Wildcard) of the Global Service Groups to be listed.

## Attribute Reference

In addition to all arguments above, the following attributes are exported.

List of matching Service Groups from Tufin SA:

* `id` - Service Id.
* `name` - Service Name.
* `globals_only` - Globals Only Flag.
* `app_id` - Specify application id to search in Application (Local) Services
* `type` - Service Type.
* `members` - List of Service Group Members (which are Services).
* `comment` - Service Comment.

### Example

```terraform
service_groups = [
  {
    id     = 1
    name   = "ServiceGroup"
    global = false
    type   = "group"
    members = [
      "ftp",
      "http",
      "https",
      "shell",
      "smtp",
      "ssh",
    ]
    comment = "comment .."
  },
]
```

