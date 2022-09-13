:original_name: en-us_topic_0300978092.html

.. _en-us_topic_0300978092:

Checking the Disk Capacity of an Image
======================================

Scenarios
---------

You can check the disk capacity of a private image.

-  To check the disk capacity of a system disk image, data disk image, or ISO image, see :ref:`Check the Disk Capacity of a System Disk Image, Data Disk Image, or ISO Image <en-us_topic_0300978092__section4605745191513>`.
-  To check the disk capacity of a full-ECS image, see :ref:`Check the Disk Capacity of a Full-ECS Image <en-us_topic_0300978092__section712514158290>`.

.. _en-us_topic_0300978092__section4605745191513:

Check the Disk Capacity of a System Disk Image, Data Disk Image, or ISO Image
-----------------------------------------------------------------------------

Check the disk capacity in the **Disk Capacity** column of the private image list.

#. Access the IMS console.

   a. Log in to the management console.

   b. Under **Compute**, click **Image Management Service**.

      The IMS console is displayed.

#. Click the **Private Images** tab to display the image list.
#. Check the value in the **Disk Capacity** column. The unit is **GB**.

.. _en-us_topic_0300978092__section712514158290:

Check the Disk Capacity of a Full-ECS Image
-------------------------------------------

The disk capacity of a full-ECS image is the sum of the system disk capacity and data disk capacity in the backup from which the full-ECS image is created.

#. Access the IMS console.

   a. Log in to the management console.

   b. Under **Compute**, click **Image Management Service**.

      The IMS console is displayed.

#. Click the **Private Images** tab to display the image list.

   The value in the **Disk Capacity** column is **--**.

#. Click the full-ECS image name.

#. Click the **Backups** tab and view the capacities of the system disk and data disks in the backup.

   Disk capacity of a full-ECS image = Capacity of the system disk in the backup + Capacity of data disks in the backup

   For example:

   -  If the system disk capacity is 40 GB and no data disk is attached, the capacity of the full-ECS image disk is 40 GB.
   -  If the system disk capacity is 40 GB and data disk capacity is 40 GB, the full-ECS image disk capacity is 80 GB.
