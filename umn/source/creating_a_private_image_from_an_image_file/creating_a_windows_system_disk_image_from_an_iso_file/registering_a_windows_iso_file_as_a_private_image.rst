:original_name: en-us_topic_0146474782.html

.. _en-us_topic_0146474782:

Registering a Windows ISO File as a Private Image
=================================================

Scenarios
---------

Register an external ISO file on the cloud platform as a private image (ISO image). Before registering an image, ensure that the ISO file with VirtIO drivers integrated has been uploaded to an OBS bucket.

An ISO image cannot be replicated, encrypted, or exported.

Prerequisites
-------------

-  The file to be registered must be in ISO format.
-  The ISO file has been uploaded to an OBS bucket. For details, see :ref:`Uploading an Image File <en-us_topic_0030713183>`.

Procedure
---------

#. Log in to the management console.

   a. Under **Computing**, click **Image Management Service**. The IMS console is displayed.

#. Register an ISO file as an ISO image.

   a. Click **Create Image** in the upper right corner.

   b. In the **Image Type and Source** area, select **Import Image** for **Type** and then select **ISO image** for **Image Type**.

   c. In the image file list, select the bucket and then the image file.


      .. figure:: /_static/images/en-us_image_0000001817919181.png
         :alt: **Figure 1** Creating a private image from an ISO file

         **Figure 1** Creating a private image from an ISO file

   d. In the **Image Information** area, set required parameters.


      .. figure:: /_static/images/en-us_image_0000001771320182.png
         :alt: **Figure 2** Configuring image information

         **Figure 2** Configuring image information

      -  **Boot Mode**: Select **BIOS** or **UEFI**. Ensure that the selected boot mode is the same as that in the image file, or the ECSs created from this image will not be able to boot up.
      -  **OS**: Select the OS specified in the ISO file to ensure that the image can be created and used properly.
      -  **System Disk**: Set the system disk capacity (value range: 40 GB to 1024 GB), which must be no less than the capacity of the system disk in the image file.
      -  **Name**: Enter a name for the image to be created.
      -  **Enterprise Project**: Select the enterprise project your image belongs to.
      -  (Optional) **Tag**: Add a tag to the image to be created.
      -  (Optional) **Description**: Describe the image as needed.

   e. Click **Next**.

   f. Confirm the settings and click **Submit**.

#. Switch back to the **Image Management Service** page to check the image status.

   When the image status changes to **Normal**, the image is registered successfully.
