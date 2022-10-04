:original_name: en-us_topic_0093344231.html

.. _en-us_topic_0093344231:

Creating a Full-ECS Image from a CSBS Backup
============================================

Scenarios
---------

Create a full-ECS image from a CSBS backup. This image can then be used to create ECSs.

Constraints
-----------

-  When creating a full-ECS image from a CSBS backup, ensure that the source ECS of the CSBS backup has been properly configured, or the image creation may fail.
-  A CSBS backup used to create a full-ECS image cannot have shared disks.
-  Only an available CSBS backup can be used to create a full-ECS image. A CSBS backup can be used to create only one full-ECS image.
-  A full-ECS image cannot be exported or replicated.

Procedure
---------

#. Access the IMS console.

   a. Log in to the management console.

   b. Under **Compute**, click **Image Management Service**.

      The IMS console is displayed.

#. Create a full-ECS image.

   a. Click **Create Image** in the upper right corner.

   b. In the **Image Type and Source** area, select **Full-ECS image** for **Type**.

   c. Select **CSBS Backup** for **Source** and then select a backup from the list.


      .. figure:: /_static/images/en-us_image_0120595964.png
         :alt: **Figure 1** Creating a full-ECS image using a CSBS backup


         **Figure 1** Creating a full-ECS image using a CSBS backup

   d. In the **Image Information** area, configure basic image details, such as the image name and description.

   e. Click **Create Now**.

   f. Confirm the parameters and click **Submit**.

#. Switch back to the **Image Management Service** page to monitor the image status.

   When the image status changes to **Normal**, the image creation is complete.

Follow-up Procedure
-------------------

-  If you want to use the full-ECS image to create ECSs, click **Apply for Server** in the **Operation** column. On the displayed page, create ECSs by following the instructions in *Elastic Cloud Server User Guide*.

   .. note::

      If a full-ECS image contains one or more data disks, the system configures data disk parameters automatically when you use the image to create ECSs.

-  If you use a full-ECS image to change an ECS OS, only the system disk data can be written into the ECS. Therefore, if you want to restore or migrate the data disk data of an ECS by using a full-ECS image, you can only use the image to create a new ECS rather than use it to change the ECS OS.
-  If you want to share a full-ECS image with other tenants, you must migrate resources to the CBR service because only full-ECS images created from CBR backups can be shared.
