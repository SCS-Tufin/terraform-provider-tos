---
page_title: "Release Notes"
subcategory: "Versions"
---

# Release Notes

### TOS Terraform Provider v.1.3.9

July 9th, 2025

__New Features__
- __resource tos_uspe_v2      :__ Manages Unified Security Policy Exceptions (USPEs) from Tufin Aurora ST.

__Note:__
Please check your provider version by executing `terraform version` command in the terminal.
```
+ provider hashicorp.com/rc/tos v1.3.9
```
To be able to use the latest version __please update your provider version__ in `provider.tf` file as following, and initialize your configuration by `terraform init` command.
```
terraform {
  required_providers {
    tos = {
      version = "~> 1.3.9"
      source  = "hashicorp.com/rc/tos"
    }
  }
}
```

### TOS Terraform Provider v.1.3.8

March 26th, 2025

__Updated__
- Documentations updated.


### TOS Terraform Provider v.1.3.7

February 18th, 2025

__New Features__
- __resource tos_connection_to_application_interface :__ Manages Connections to Application Interfaces in Tufin SC.
- __resource tos_application_pack_tag :__ Manages Application Pack Tags in Tufin SC
- __resource tos_application_interface__ with optional Application Pack Id and Tag

__Upcoming__
- __resource tos_zones_v2     :__ Manages Zones in Tufin Aurora ST.
- __resource tos_uspe_v2      :__ Manages Unified Security Policy Exceptions (USPEs) from Tufin Aurora ST.


### TOS Terraform Provider v.1.3.6

January 29th, 2025

__New Features__
- __data_source tos_zones_v2  :__ Lists Zones from Tufin Aurora ST.


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
