# Data Source `tos_services`

The `tos_services` Data Source lists Global Services from Tufin SA.

## Usage

```terraform
data "tos_services" "services_by_name" {
  name = "https"
  min_port = 443
  max_port = 443
  service_type = "tcp"
  app_id = -1
}
```

## Argument Reference

* `name` - Name (Wildcard) of the Services to be listed.
* `min_port` - Min Port of the Services to be listed
* `max_port` - Max Port of the Services to be listed
* `service_type` - Service type of the Services to be listed (eg. tcp, udp, icmp)
* `app_id` - Specify application id to search in Application (Local) Services
* `globals_only` - Specify to search for Global or Application (Local) Services

Note: All arguments are optional. 

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
    id       = 1
    name     = "https"
    global   = true
    type     = "tcp_service"
    protocol = ""
    min      = 443
    max      = 443
    comment  = "HTTP protocol over TLS/SSL"
  },
] 
```

