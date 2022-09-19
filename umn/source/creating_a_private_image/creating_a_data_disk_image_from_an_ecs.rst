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

.. _en-us_topic_0102644450__fig776414944511:

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

   b. Under **Compute**, click **Image Management Service**.

      The IMS console is displayed.

#. Create a data disk image.

   a. Click **Create Image** in the upper right corner.

   b. In the **Image Type and Source** area, select **Data disk image** for **Type**.

   c. Select **ECS** for **Source** and then select a data disk of the ECS.

      .. _en-us_topic_0102644450__fig197535202193:

      .. figure:: /_static/images/en-us_image_0120595879.png
         :alt: **Figure 2** Creating a data disk image


         **Figure 2** Creating a data disk image

   d. In the **Image Information** area, set **Name**, **Tag**, and **Description**.

   e. Click **Create Now**.

   f. Confirm the parameters and click **Submit**.

#. Go back to the **Private Images** page and view the new data disk image.

Follow-up Procedure
-------------------

If you want to use the created data disk image to create an EVS disk and attach it to an ECS, you can perform either of the following operations:

-  Locate the row that contains the created data disk image and click **Create Data Disk** to create a data disk. Then attach the data disk to an ECS.
-  On the page for creating ECSs, click **Create Disk from Data Disk Image** and select the data disk image.

   .. note::

      A data disk image can be used to create a data disk for an ECS only once.
