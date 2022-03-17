---
layout: "vkcs"
page_title: "VKCS: vpnaas_endpoint_group"
description: |-
  Manages a Neutron Endpoint Group resource within OpenStack.
---

# vkcs\_vpnaas\_endpoint\_group

Manages a Neutron Endpoint Group resource within OpenStack.

## Example Usage

```hcl
resource "vkcs_vpnaas_endpoint_group" "group_1" {
	name = "Group 1"
	type = "cidr"
	endpoints = [
		"10.2.0.0/24",
		"10.3.0.0/24",
	]
}
```

## Argument Reference

The following arguments are supported:

* `description` - (Optional) The human-readable description for the group.
	Changing this updates the description of the existing group.

* `name` - (Optional) The name of the group. Changing this updates the name of
	the existing group.

* `region` - (Optional) The region in which to obtain the Networking client.
	A Networking client is needed to create an endpoint group. If omitted, the
	`region` argument of the provider is used. Changing this creates a new
	group.

* `type` -  The type of the endpoints in the group. 
	A valid value is subnet, cidr, network, router, or vlan.
	Changing this creates a new group.
	
* `endpoints` - List of endpoints of the same type, for the endpoint group. 
	The values will depend on the type.
	Changing this creates a new group.

## Attributes Reference

The following attributes are exported:

* `region` - See Argument Reference above.
* `name` - See Argument Reference above.
* `description` - See Argument Reference above.
* `type` - See Argument Reference above.
* `endpoints` - See Argument Reference above.

## Import

Groups can be imported using the `id`, e.g.

```
$ terraform import vkcs_vpnaas_endpoint_group.group_1 832cb7f3-59fe-40cf-8f64-8350ffc03272
```
