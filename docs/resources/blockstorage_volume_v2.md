---
subcategory: "Elastic Volume Service (EVS)"
description: ""
page_title: "flexibleengine_blockstorage_volume_v2"
---

# flexibleengine_blockstorage_volume_v2

Manages a V2 volume resource within FlexibleEngine.

## Example Usage

```hcl
resource "flexibleengine_blockstorage_volume_v2" "volume_1" {
  name        = "volume_1"
  description = "first test volume"
  size        = 3
  metadata = {
    __system__encrypted = "1"
    __system__cmkid     = "kms_id"
  }
}
```

## Argument Reference

The following arguments are supported:

* `region` - (Optional) The region in which to create the volume. If
    omitted, the `region` argument of the provider is used. Changing this
    creates a new volume.

* `size` - (Required) The size of the volume to create (in gigabytes).

* `availability_zone` - (Optional) The availability zone for the volume.
    Changing this creates a new volume.

* `consistency_group_id` - (Optional) The consistency group to place the volume
    in.

* `description` - (Optional) A description of the volume. Changing this updates
    the volume's description.

* `image_id` - (Optional) The image ID from which to create the volume.
    Changing this creates a new volume.

* `metadata` - (Optional) Metadata key/value pairs to associate with the volume.
    Changing this updates the existing volume metadata.
    The EVS encryption capability with KMS key can be set with the following parameters:
    + `__system__encrypted` - The default value is set to '0', which means
      the volume is not encrypted, the value '1' indicates volume is encrypted.
    + `__system__cmkid` - (Optional) The ID of the kms key.

* `name` - (Optional) A unique name for the volume. Changing this updates the
    volume's name.

* `snapshot_id` - (Optional) The snapshot ID from which to create the volume.
    Changing this creates a new volume.

* `source_replica` - (Optional) The volume ID to replicate with.

* `source_vol_id` - (Optional) The volume ID from which to create the volume.
    Changing this creates a new volume.

* `volume_type` - (Optional) The type of volume to create.
    Changing this creates a new volume.

* `cascade` - (Optional, Default:false) Specifies to delete all snapshots associated with the EVS disk.

* `multiattach` - (Optional) Specifies whether the EVS disk is shareable.

* `tags` - (Optional) The key/value pairs to associate with the volume.

## Attributes Reference

The following attributes are exported:

* `region` - See Argument Reference above.
* `size` - See Argument Reference above.
* `name` - See Argument Reference above.
* `description` - See Argument Reference above.
* `availability_zone` - See Argument Reference above.
* `image_id` - See Argument Reference above.
* `source_vol_id` - See Argument Reference above.
* `snapshot_id` - See Argument Reference above.
* `metadata` - See Argument Reference above.
* `volume_type` - See Argument Reference above.
* `multiattach` - See Argument Reference above.
* `tags` - See Argument Reference above.
* `attachment` - If a volume is attached to an instance, this attribute will
    display the Attachment ID, Instance ID, and the Device as the Instance
    sees it.

## Import

Volumes can be imported using the `id`, e.g.

```shell
terraform import flexibleengine_blockstorage_volume_v2.volume_1 ea257959-eeb1-4c10-8d33-26f0409a755d
```
