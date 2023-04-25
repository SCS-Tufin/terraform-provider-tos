# Data Source `tos_service_port`

The `tos_service_port` Data Source lists a single Global service with a port defined by port from Tufin SA.

## Usage

```terraform
data "tos_service_port" "services_by_port" {
  port = "8080"
}
```

## Argument Reference

* `port` - port of the Global Services to be listed.

## Attribute Reference

In addition to all arguments above, the following attributes are exported.

List of matching Services from Tufin SA:

* `id` - Service Id.
* `name` - Service Name.
* `global` - Service Global Flag.
* `type` - Service Type.
* `protocol` - Protocol.
* `min` - Min Port.
* `max` - Max Port.
* `comment` - Service Comment.

### Example

```terraform
services = [
  {
    id       = 84
    name     = "HTTP_and_HTTPS_proxy"
    global   = true
    type     = "tcp_service"
    protocol = ""
    min      = 8080
    max      = 8080
    comment  = "HTTP and HTTPS Proxy"
  },
]
```

