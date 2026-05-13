---
page_title: "Versions"
subcategory: "Versions"
---

# Latest Version

## v1.6.0

* v1.6.0 has been published on 13.05.2026.

Please be sure that you defined the latest version on your configuration files(provider.tf).

```terraform
terraform {
  required_providers {
    tos = {
      version = "~> 1.6.0"
      source  = "hashicorp.com/rc/tos"
    }
  }
}
```

# Release Candidates
None are published at this moment.

# Deprecated Versions
All versions prior to v1.1.0 must not be used!
