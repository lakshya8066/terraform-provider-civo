---
# generated by https://github.com/hashicorp/terraform-plugin-docs
page_title: "civo_database Resource - terraform-provider-civo"
subcategory: ""
description: |-
  
---

# civo_database (Resource)



## Example Usage

```terraform
data "civo_size" "small" {
    filter {
        key = "name"
        values = ["db.small"]
        match_by = "re"
    }
    filter {
        key = "type"
        values = ["database"]
    }
}

resource "civo_database" "custom_database" {
    name = "custom_database"
    size = element(data.civo_size.small.sizes, 0).name
    nodes = 2
}
```

<!-- schema generated by tfplugindocs -->
## Schema

### Required

- `name` (String) Name of the database
- `nodes` (Number) Count of nodes
- `size` (String) Size of the database

### Optional

- `firewall_id` (String) The ID of the firewall to use, from the current list. If left blank or not sent, the default firewall will be used (open to all)
- `network_id` (String) The id of the associated network
- `region` (String) The region where the database will be created.
- `timeouts` (Block, Optional) (see [below for nested schema](#nestedblock--timeouts))

### Read-Only

- `id` (String) The ID of this resource.
- `password` (String) The password of the database
- `status` (String) The status of the database
- `username` (String) The username of the database

<a id="nestedblock--timeouts"></a>
### Nested Schema for `timeouts`

Optional:

- `create` (String)
- `delete` (String)
- `update` (String)

## Import

Import is supported using the following syntax:

```shell
# using ID
terraform import civo_database.mydb 29fcd1c4-fb61-44c7-b49c-dc7b98e9927e
```
