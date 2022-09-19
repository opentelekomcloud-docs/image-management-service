:original_name: en-us_topic_0106444267.html

.. _en-us_topic_0106444267:

How Do I Create a Full-ECS Image Using an ECS That Has a Spanned Volume?
========================================================================

An ECS used to create a Windows full-ECS image cannot have a spanned volume. If you attempt to create an image from an ECS with a spanned volume, when the image is used to create new ECSs, data may be lost.

If an ECS has a spanned volume, back up data in the spanned volume and then delete this volume from the ECS. Use the ECS to create a full-ECS image. Use the full-ECS image to create an ECS. Then, use the backup to create a spanned volume for the new ECS if necessary.

.. note::

   If a Linux ECS has a volume group or a logical volume consisting of multiple physical volumes, to ensure you do not lose any data, back up data in the volume group or logical volume and delete the volume group or logical volume before using this ECS to create a full-ECS image.
