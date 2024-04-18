:original_name: en-us_topic_0290353431.html

.. _en-us_topic_0290353431:

Why Can't I Find My Private Image When I Want to Use It to Create an ECS or Change the OS of an ECS?
====================================================================================================

The possible cause is the incompatible boot modes.

-  If a private image is created from an ECS configured for BIOS boot or if you use an external image file to create such an image, this image will not be available as a choice when you create an ECS configured for UEFI boot or change the OS of an ECS booted from UEFI.
-  Likewise, images configured for UEFI will not be available as a choice when you create an ECS configured for BIOS boot or change the OS of an ECS booted from BIOS.
