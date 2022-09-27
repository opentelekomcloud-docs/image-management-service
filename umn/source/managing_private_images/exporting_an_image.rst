:original_name: en-us_topic_0034011241.html

.. _en-us_topic_0034011241:

Exporting an Image
==================

Scenarios
---------

You can export a private image to a standard OBS bucket and then download it to your local PC.

Background
----------

-  You can reproduce cloud servers and their running environments in on-promises clusters or private clouds by exporting their images from the cloud platform. The following figure shows the process of exporting an image.


   .. figure:: /_static/images/en-us_image_0255101497.png
      :alt: **Figure 1** Exporting an image


      **Figure 1** Exporting an image

-  The time required for exporting an image depends on the image size and the number of concurrent export tasks.

-  You can export images in QCOW2, VMDK, VHD, or ZVHD format. Images exported in different formats may vary in size.

-  If an image is greater than 128 GB, you can select **Enable** for **Fast Export** when exporting the image to an OBS bucket. In this case, you cannot specify the format of the exported image. You can convert the image format after it is exported.

   .. note::

      **Fast Export** is unavailable for encrypted images.

Constraints
-----------

-  The following private images cannot be exported:

   -  Full-ECS images
   -  Private images created from a Windows or SUSE public image

-  The image size must be less than 1 TB. Images larger than 128 GB support only fast export.

Prerequisites
-------------

An OBS bucket is available in the region where the private image is located.

If no OBS bucket is available, create one by referring to *Object Storage Service User Guide*. Select **Standard** for **Storage Class**.

Procedure
---------

#. Access the IMS console.

   a. Log in to the management console.

   b. Under **Compute**, click **Image Management Service**.

      The IMS console is displayed.

#. Locate the row that contains the image to be exported, click **More** in the **Operation** column and select **Export**.

#. In the displayed **Export Image** dialog box, set the following parameters:

   -  **Fast Export**: To export an image larger than 128 GB, you must enable fast export, and you cannot specify the format of the exported image (which can only be ZVHD2). After exporting the image, you can use **qemu-img-hw** to convert it to your desired format. For details, see :ref:`Converting the Image Format Using qemu-img-hw <en-us_topic_0171668652>`.

      .. note::

         For details about differences between export and fast export, see :ref:`What Are the Differences Between Import/Export and Fast Import/Export? <en-us_topic_0199451475>`

   -  **Format**: Select one from **qcow2**, **vmdk**, **vhd**, and **zvhd** as you need.
   -  **Name**: Enter a name that is easy to identify.
   -  **Storage Path**: Click |image1| to expand the bucket list and select an OBS bucket for storing the exported image.

#. Click **OK**.

   You can view the image export progress above the private image list.

Follow-up Procedure
-------------------

After the image is exported successfully, you can download it from the OBS bucket through the management console or OBS Browser+.

.. |image1| image:: /_static/images/en-us_image_0180986761.png
