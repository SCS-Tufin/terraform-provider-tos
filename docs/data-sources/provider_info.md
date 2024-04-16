# Data Source `tos_providerinfo`

The `tos_providerinfo` Data Source shows basic Provider Informations.

## Usage

```terraform
data "tos_providerinfo" "providerinfo" {
}
```

## Argument Reference

No Arguments

## Attribute Reference

The following attributes are exported:

* `Mode` - Provider Mode.
* `TBA Url` - Tufin Backend API (TBA) URL.
* `TOS SC Url` - Turfin Orchestration Suite (TOS) Secure Change (SC) URL.
* `TOS ST Url` - Turfin Orchestration Suite (TOS) Secure Change (ST) URL.
* `Title` - Provider Title.
* `Version` - Provider Version.

### Example Mode `tba`

```terraform
info = {
  "Mode"        = "tba"
  "TBA Url"     = "https://1.2.3.4"
  "TOS SC Url"  = ""
  "TOS ST Url"  = ""
  "Title"       = "Terraform Provider TOS (Tufin Orchestration Suite)"
  "Version"     = "v1.0.10"
}
```

### Example Mode `tos`

```terraform
 info = {
  "Mode"        = "tos"
  "TOS SC Url"  = "https://1.2.3.4"
  "TOS ST Url"  = "https://1.2.3.4"
  "Title"       = "Terraform Provider TOS (Tufin Orchestration Suite)"
  "Version"     = "v1.2.1"
}
```
