---
page_title: "Release Notes"
subcategory: "Versions"
---

# Release Notes

### TOS Terraform Provider v.1.3.7

Coming soon! 

### TOS Terraform Provider v.1.3.6

January 29th, 2025

__New Features__
- __data_source tos_zones_v2  :__ Lists Zones from Tufin Aurora ST.

__Upcoming__
- __resource tos_zones_v2     :__ Manages Zones in Tufin Aurora ST.
- __resource tos_uspe_v2      :__ Zone based Manages Unified Security Policy Exceptions (USPEs) from Tufin Aurora ST.
- __resource tos_tag          :__ Manages Tufin Application pack tags
- __resource tos_application_interface__ with optional Application Pack Id and Tag
- New resource __tos_connection_to_application_interface__

__Note:__
Please check your provider version by executing `terraform version` command in the terminal.
```
+ provider hashicorp.com/rc/tos v1.3.6
```
To be able to use the latest version __please update your provider version__ in `provider.tf` file as following, and initialize your configuration by `terraform init` command.
```
terraform {
  required_providers {
    tos = {
      version = "~> 1.3.6"
      source  = "hashicorp.com/rc/tos"
    }
  }
}
```

### TOS Terraform Provider v.1.3.5 

December 9th, 2024

__New Features__
- __resource_tos_application  :__ You can use User Groups as "viewer" or "editor" of the application. See the details on documentation page.

__Updated__
- Documentation page updated.
- SDKv2 dependencies and Go version have been updated.

__Fixed__
- __resource_tos_uspe:__ Creating Unified Security Policy Exceptions (USPEs) without valid network object and zone has been fixed.  
- Removed __resource_tos_tag__.

__Upcoming__
- __data_source_tos_zones_v2  :__ Lists Zones from Tufin Aurora ST.



