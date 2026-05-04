# Data Source `tos_networkobjects`

The `tos_networkobjects` Data Source lists Network Objects from Tufin SA.

## Usage

```terraform
data "tos_networkobjects" "networkobjects_by_name_host" {
  name = "MARS"

  customer = var.customer
  app      = var.app
}
```

## Argument Reference

* `name` - (Required) The Network Object Name (Filter).
* `customer` - (Required) The Customer Name.
* `app` - (Required) The Application Name.

## Attribute Reference

In addition to all arguments above, the following attributes are exported.

List of matching Network Objects from Tufin SA distinguished by type each containing:

* `id` - Network Object Id.
* `name` - Network Object Name.
* `type`- Network Object Type; Types are:
    * `host`
    * `range`
    * `subnet`
    * `group`
* `ip`- Network Object Ip (not set for type `group`).
* `members`- Network Object Members (only set for type `group`).
* `comment`- Application Viewers.

### Example Type `host`

```terraform
networkobjects = [
  {
    id      = 1
    name    = "MARS-1"
    type    = "host"
    ip      = "1.2.3.4/32"
    members = []
    comment = "Test Host"
  },
]
```

### Example Type `range`

```terraform
networkobjects = [
  {
    id      = 1
    name    = "RANGE-1"
    type    = "range"
    ip      = "1.2.3.1-1.2.3.4"
    members = []
    comment = "Test Range"
  },
]
```

### Example Type `subnet`

```terraform
networkobjects = [
  {
    id      = 1
    name    = "SUBNET-1"
    type    = "subnet"
    ip      = "10.255.250.0/24"
    members = []
    comment = "Test Subnet"
  }
]
```

### Example Type `group`

```terraform
networkobjects = [
  {
    id      = 1
    name    = "GROUP-1"
    type    = "group"
    ip      = ""
    members = [
      "MARS_1",
      "ASTEROIDS_1",
      "MILKYWAY_1",
    ],
    comment = "Test Group"
  },
]
```

