:original_name: en-us_topic_0102644450.html

.. _en-us_topic_0102644450:

Creating a Data Disk Image from an ECS
======================================

Scenarios
---------

A data disk image contains only service data. You can create a data disk image from an ECS and then use the image to create new EVS disks. This is a convenient way to migrate data from an ECS to EVS disks.

For example, you can create a data disk image to clone the data of an ECS whose disk is about to expire.

Background
----------

The following figure shows the process of creating a data disk image from an ECS.


.. figure:: /_static/images/en-us_image_0254963039.png
   :alt: **Figure 1** Creating a data disk image and using it to create data disks

   **Figure 1** Creating a data disk image and using it to create data disks

Prerequisites
-------------

-  A data disk has been attached to the ECS, and the ECS is running or stopped. For details about how to attach a data disk, see *Elastic Cloud Server User Guide*.

-  The data disk capacity of the ECS must be no greater than 1 TB.

   If the capacity is greater than 1 TB, you can only use the ECS to create a full-ECS image.

Procedure
---------

#. Access the IMS console.

   a. Log in to the management console.

   b. Under **Computing**, click **Image Management Service**.

      The IMS console is displayed.

#. Create a data disk image.

   a. Click **Create Image** in the upper right corner.

   b. In the **Image Type and Source** area, select **Create Image** for **Type** and then select **Data disk image** for **Image Type**.

   c. Select **ECS** for **Source** and then select a data disk of the ECS.


      .. figure:: /_static/images/en-us_image_0162743998.png
         :alt: **Figure 2** Creating a data disk image

         **Figure 2** Creating a data disk image

   d. In the **Image Information** area, set **Name**, **Tag**, and **Description**.

   e. In the **Image Information** area, set **Name**, **Tag**, and **Description**, and select an enterprise project.

   f. Click **Create Now**.

   g. Confirm the settings and click **Submit**.

#. Go back to the **Private Images** page and view the new data disk image.

Follow-up Procedure
-------------------

If you want to use the created data disk image to create an EVS disk and attach it to an ECS, you can perform either of the following operations:

-  Locate the row that contains the created data disk image and click **Create Data Disk** to create one or multiple data disks. Then attach the data disks to an ECS.

-  On the page for creating ECSs, click **Create Disk from Data Disk Image** and select the data disk image.

   .. note::

      In this way, a data disk image can be used to create a data disk for an ECS only once. For example, a data disk created from data disk image **data_disk_image** has been added to the ECS. No any other data disk created from this image can be added to the ECS.


   .. figure:: /_static/images/en-us_image_0186473007.png
      :alt: **Figure 3** Adding data disks

      **Figure 3** Adding data disks
