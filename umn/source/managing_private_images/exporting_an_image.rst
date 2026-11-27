:original_name: en-us_topic_0034011241.html

.. _en-us_topic_0034011241:

Exporting an Image
==================

Scenarios
---------

You can export a private image to a standard OBS bucket and then download it to your local PC.

Background
----------

You can export images of cloud servers from the cloud platform and then use the exported images to create cloud servers for use in on-premises clusters or private clouds. The following figure shows the process of exporting an image.


.. figure:: /_static/images/en-us_image_0255101497.png
   :alt: **Figure 1** Exporting an image

   **Figure 1** Exporting an image

Constraints
-----------

.. table:: **Table 1** Constraints on exporting images

   +-----------------------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Item                              | Description                                                                                                                                                                                                        |
   +===================================+====================================================================================================================================================================================================================+
   | Region                            | An image can only be exported to a Standard bucket that is in the same region as the image.                                                                                                                        |
   +-----------------------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Image type                        | The following private images cannot be exported:                                                                                                                                                                   |
   |                                   |                                                                                                                                                                                                                    |
   |                                   | -  Full-ECS images                                                                                                                                                                                                 |
   |                                   | -  ISO images                                                                                                                                                                                                      |
   |                                   | -  Private images created from a Windows, SUSE, Red Hat, Ubuntu, or Oracle Linux public image                                                                                                                      |
   |                                   |                                                                                                                                                                                                                    |
   |                                   | .. note::                                                                                                                                                                                                          |
   |                                   |                                                                                                                                                                                                                    |
   |                                   |    -  Fast export is unavailable for encrypted images. To export an encrypted image, decrypt it first.                                                                                                             |
   +-----------------------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Image format                      | -  You can export images to the ZVHD2, QCOW2, VMDK, VHD, or ZVHD format. By default, a private image is created in ZVHD2 format. The size of an exported image may vary depending on the export format you select. |
   |                                   | -  Fast export only supports the ZVHD2 format. If you need to export the image in another format, you can use the qemu-img-hw tool to convert the image to the required format after the image is exported.        |
   +-----------------------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Image size                        | The image size must be less than 1 TiB. Images larger than 128 GiB and smaller than 1 TiB only support fast export.                                                                                                |
   +-----------------------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Time                              | The time required for exporting an image depends on the image size and the number of concurrent export tasks.                                                                                                      |
   +-----------------------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+

Prerequisites
-------------

-  You have Administrator permissions for OBS.

-  An OBS bucket is available for storing the private image in the region where the private image is located.

   If no OBS bucket is available, create one by referring to *Object Storage Service User Guide*. Select **Standard** for **Storage Class**.

Procedure
---------

#. Log in to the management console.

   a. Under **Computing**, click **Image Management Service**. The IMS console is displayed.

#. Locate the row that contains the image to be exported, click **More** in the **Operation** column and select **Export**.

#. In the displayed **Export Image** dialog box, set the following parameters:

   -  **Fast Export**: To export an image larger than 128 GiB, you must enable fast export, and you cannot specify the format of the exported image (which can only be ZVHD2). After exporting an image, you can use **qemu-img-hw** to convert it to your desired format. For details, see :ref:`Converting the Image Format Using qemu-img-hw <en-us_topic_0171668652>`.

      .. note::

         For details about the differences between standard and fast export, see :ref:`What Are the Differences Between Standard and Fast Import/Export? <en-us_topic_0199451475>`

   -  **Format**: Select one from **qcow2**, **vmdk**, **vhd**, and **zvhd** as you need.
   -  **Name**: Enter a name that is easy to identify.
   -  **Storage Path**: Click |image1| to expand the bucket list and select an OBS bucket for storing the exported image.

      .. note::

         An image can only be exported to a Standard bucket that is in the same region as the image. So, only such buckets are listed.

#. Click **OK**.

   You can view the image export progress above the private image list.

Follow-up Procedure
-------------------

After the image is exported, you can download it from the OBS bucket through the management console or OBS Browser+.

.. |image1| image:: /_static/images/en-us_image_0180986761.png
