:original_name: en-us_topic_0199396602.html

.. _en-us_topic_0199396602:

How Can I Use a Backup to Create an EVS Disk or ECS?
====================================================

You can use CSBS backups to create ECSs and use VBS backups to create EVS disks.

-  CSBS backups cannot be directly used to create ECSs. You need to use a backup to create a private image and then use the private image to create ECSs.

   For details about how to create a private image from a CSBS backup, see :ref:`Creating a Full-ECS Image from a CSBS Backup <en-us_topic_0093344231>`. For details about how to create ECSs from a private image, see :ref:`Creating an ECS from an Image <en-us_topic_0030713200>`.

-  VBS backups can be directly used to create EVS disks. For details, see "Using a Backup to Create a Disk" in *Cloud Backup and Recovery User Guide*.
