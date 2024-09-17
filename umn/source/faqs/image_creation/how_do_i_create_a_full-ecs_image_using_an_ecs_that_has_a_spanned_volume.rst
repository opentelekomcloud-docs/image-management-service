:original_name: en-us_topic_0106444267.html

.. _en-us_topic_0106444267:

How Do I Create a Full-ECS Image Using an ECS That Has a Spanned Volume?
========================================================================

You are not advised to use a Windows ECS that has a spanned volume to create a full-ECS image. If you create such an image and then use it to create new ECSs, data may be lost.

If an ECS has a spanned volume, back up data in the spanned volume and then delete the volume. Use the ECS to create a full-ECS image. You can then use the full-ECS image to create an ECS and use the backup to create a spanned volume for the new ECS if necessary.

.. note::

   If a Linux ECS has a volume group or a logical volume consisting of multiple physical volumes, to ensure you do not lose any data, back up data in the volume group or logical volume and delete the volume group or logical volume before using this ECS to create a full-ECS image.
