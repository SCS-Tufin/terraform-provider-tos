# Resource `tos_application`

The `tos_application` Resource manages Applications in Tufin SC.

## Usage

```terraform
resource "tos_application" "application_1" {
  name     = "APP_1"
  customer = var.customer

  owner   = "OwnerName"
  editors = [
    "Editor X",
    "Editor Y",
    "Editor UserGroup"
  ]
  inherit_editors = false
  viewers = [
    "Viewer X",
    "Viewer Y",
    "Viewer UserGroup"
  ]

  comment  = "APP 1 .."

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
* `owner` - (Required) The Application Owner.
* `editors` - (Required) The Application Editors.
* `viewers` - (Required) The Application Viewer.
* `comment` - (Required) The Application Comment.
* `tags` - (Optional) Resource Tags; see [Tags](../guides/121_tags.md) for details.
* `inherit_editors` - (Optional) Inherits CSE group to editors of the application.
  * When inherit_editors was set to true, CSE group will be added to editors.
  * When inherit_editors was set to false, CSE group will not be added to editors.


## Attribute Reference

In addition to all arguments above, the following attributes are exported:

* `id` - The Application ID.

### Example

```terraform
resource "tos_application" "application_1" {
  id      = "1"
  customer  = "moon"
  name    = "APP_1"
  comment = "App 1 .."
  owner   = "owner1"
  editors = [
    "editor1",
    "editor2",
  ]
  inherit_editors = false
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

## Import Existing Application to Terraform State 

The `tos_application` Resources can be imported using the identifier `id`.

### How to Import by Terraform? 
- Define following import block with the id and destination resource address.
```HCL
import {
  id = "application_id_to_import"
  to = tos_application.example_name
}
```
- Execute terraform plan with -generate-config-out flag.
```bash
terraform plan -generate-config-out="imported_resources.tf"
```
- You can view the imported_resources.tf file for imported resource.
- Edit the imported_resources.tf file, and run terraform plan. 
- Note: You may need to remove/add some of the arguments. 

### How to Import Manually?
- Add following empty resource block to your configuration.
```HCL
resource "tos_application" "application_import" {}
```
- Import resource from real infrastructure
```bash
terraform import [resource_adress] [resource_id_to_import]
terraform import tos_application.application_import 774
```
- If empty resource is in a module,
```bash
terraform import [resource_address_with_module] [resource_id_to_import]
terraform import module.applications.tos_application.application_import 774
```
- Find your imported resource in terraform state file
```bash
terraform state list | grep [resource_name]
terraform state list | grep application_import
- module.applications.tos_application.application_import
```
- Read the resource details from terraform state file
```bash
terraform state show [resource_address] 
terraform state show module.applications.tos_application.application_import
```
- Replace the output of "terraform state show [resource_address]" with your empty resource, remove the id and add the customer manually. 
- Execute terraform plan and apply, these will add the customer to statefile. When you execute terraform plan again you will see no changes.
- Now you can start managing the imported application by Terraform.
- For more details, please check official documentation provided by Terraform.