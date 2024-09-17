:original_name: en-us_topic_0049196766.html

.. _en-us_topic_0049196766:

How Can I Back Up the Current Status of an ECS for Restoration in the Case of a System Fault?
=============================================================================================

You can back up the ECS in any of the following ways:

-  (Recommended) Use CBR to create a scheduled backup for the ECS. If the ECS fails, select a backup you want to use to restore the ECS, create a full-ECS image from the backup, and use the image to create a new ECS or to reinstall the OS of the ECS.
-  Create a system disk image from the ECS. If the ECS fails, use the system disk image to create a new ECS or to reinstall the OS.
-  Create a snapshot for the system disk of the ECS. If the ECS fails, you can restore the system disk data from the snapshot.
