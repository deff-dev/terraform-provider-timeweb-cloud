---
page_title: "twc_ssh_keys Data Source - Timeweb Cloud"
subcategory: ""
description: |-
  Data source that provides capability for filtering and SSH key selection. All parameters are filters, so you can use only needed
---

# twc_ssh_keys (Data Source)

Data source that provides capability for filtering and SSH key selection. All parameters are filters, so you can use only needed

## Примеры использования

```terraform
data "twc_os" "example" {
  name = "ubuntu"
  version = "22.04"
}

data "twc_presets" "example" {
  price_filter {
    from = 300
    to = 400
  }
}

# Select SSH key with name = "Example"
data "twc_ssh_keys" "example" {
  name = "Example"
}

# Usage example of selected SSH key
resource "twc_server" "example-server" {
  name = "Example server"
  os_id = data.twc_os.os.id

  preset_id = data.twc_presets.example.id

  ssh_keys_ids = [data.twc_ssh_keys.example.id]
}
```

<!-- schema generated by tfplugindocs -->
## Schema

### Required

- `name` (String) Name of specified SSH Key

### Read-Only

- `body` (String) Public part of specified SSH Key
- `created_at` (String) Time of creation specified SSH Key in ISO8601 format
- `id` (String) The ID of this resource.
