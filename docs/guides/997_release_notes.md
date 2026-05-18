---
page_title: "Release Notes"
subcategory: "Versions"
---
# Release Notes
## TOS Terraform Provider v.1.6.1
May 18th, 2026

**Fixed**
- **resource tos_uspe_v2:** The bug while creating USPE with empty sources and destinations has been fixed

**Note:**
Please check your provider version by executing `terraform version` command in the terminal.
```
+ provider hashicorp.com/rc/tos v1.6.1
```
To be able to use the latest version **please update your provider version** in `provider.tf` file as following, and initialize your configuration by `terraform init` command.
```
terraform {
  required_providers {
    tos = {
      version = "~> 1.6.1"
      source  = "hashicorp.com/rc/tos"
    }
  }
}
```

## TOS Terraform Provider v.1.6.0
May 13th, 2026

**Updated**
- **resource tos_application:** New Optional "inherit_editors" argument added. See the details [here](https://registry.terraform.io/providers/SCS-Tufin/tos/latest/docs/resources/application).

## TOS Terraform Provider v.1.5.2
May 4th, 2026

**Fixed**
- USPE v2 schema issues has been fixed.

### TOS Terraform Provider v.1.5.1
October 28th, 2025

**Fixed**
- Documentation page updated.

### TOS Terraform Provider v.1.5.0
October 27th, 2025

**Updated**
- **datasource tos_application_packs:** "interfaces" flag added. "interfaces" displays Application Interfaces with Interface Name and Tags.

### TOS Terraform Provider v.1.4.2

August 11th, 2025

**Fixed**
- Documentation page updated.

### TOS Terraform Provider v.1.4.1

August 07th, 2025

**Fixed**
- **resource tos_uspe:** The bug while creating Unified Security Policy Exceptions (USPEs) has been fixed.

### TOS Terraform Provider v.1.4.0

July 30th, 2025

**Fixed**
- **resource application_interface:** Creating Application Interface by using Service Groups has been fixed.


### TOS Terraform Provider v.1.3.9

July 14th, 2025

**New Features**
- **resource tos_uspe_v2      :** Manages Unified Security Policy Exceptions (USPEs) from Tufin Aurora ST.


### TOS Terraform Provider v.1.3.8

March 26th, 2025

**Updated**
- Documentations updated.


### TOS Terraform Provider v.1.3.7

February 18th, 2025

**New Features**
- **resource tos_connection_to_application_interface :** Manages Connections to Application Interfaces in Tufin SC.
- **resource tos_application_pack_tag :** Manages Application Pack Tags in Tufin SC
- **resource tos_application_interface** with optional Application Pack Id and Tag

**Upcoming**
- **resource tos_uspe_v2      :** Manages Unified Security Policy Exceptions (USPEs) from Tufin Aurora ST.


### TOS Terraform Provider v.1.3.6

January 29th, 2025

**New Features**
- **data_source tos_zones_v2  :** Lists Zones from Tufin Aurora ST.


### TOS Terraform Provider v.1.3.5 

December 9th, 2024

**New Features**
- **resource_tos_application  :** You can use User Groups as "viewer" or "editor" of the application. See the details on documentation page.

**Updated**
- Documentation page updated.
- SDKv2 dependencies and Go version have been updated.

**Fixed**
- **resource_tos_uspe:** Creating Unified Security Policy Exceptions (USPEs) without valid network object and zone has been fixed.
- Removed **resource_tos_tag**.
