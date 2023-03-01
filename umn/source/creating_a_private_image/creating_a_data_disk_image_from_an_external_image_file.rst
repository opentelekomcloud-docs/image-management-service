:original_name: en-us_topic_0084064672.html

.. _en-us_topic_0084064672:

Creating a Data Disk Image from an External Image File
======================================================

Scenarios
---------

A data disk image contains only service data. You can create a data disk image using a local image file or an external image file (image file on another cloud platform). Then, you can use the data disk image to create EVS disks and migrate your service data to the cloud.

Background
----------

The following figure shows the process of creating a data disk image from an external image file.


.. figure:: /_static/images/en-us_image_0254985106.png
   :alt: **Figure 1** Creating a data disk image from an external image file

   **Figure 1** Creating a data disk image from an external image file

#. Prepare an external image file. The file must be in VHD, VMDK, QCOW2, RAW, VHDX, QCOW, VDI, QED, ZVHD, or ZVHD2 format. If you want to use an image file in other formats, convert the file into any of the listed formats before importing it to the cloud platform.
#. When uploading the external image file, you must select an OBS bucket with standard storage. For details, see :ref:`Uploading an External Image File <en-us_topic_0030713192>`.
#. Create a data disk image. For details, see :ref:`Procedure <en-us_topic_0084064672__section17888236123013>`.
#. Use the data disk image to create data disks. For details, see :ref:`Follow-up Procedure <en-us_topic_0084064672__section14131852173714>`.

.. _en-us_topic_0084064672__section17888236123013:

Procedure
---------

#. Access the IMS console.

   a. Log in to the management console.

   b. Under **Compute**, click **Image Management Service**.

      The IMS console is displayed.

#. Create a data disk image.

   a. Click **Create Image** in the upper right corner.

   b. In the **Image Type and Source** area, select **Data disk image** for **Type**.

   c. Select **Image File** for **Source**. Select the bucket storing the image file from the list and then select the image file.


      .. figure:: /_static/images/en-us_image_0162744031.png
         :alt: **Figure 2** Creating a data disk image

         **Figure 2** Creating a data disk image

   d. To register the image file using the Fast Create function, select **Enable Fast Create**.

      .. note::

         -  Currently, this function supports only image files in ZVHD2 or RAW format.
         -  For how to convert image file formats and generate bitmap files, see :ref:`Quickly Importing an Image File <en-us_topic_0030713151>`.

      After you select **Enable Fast Create**, select the confirmation information following **Image File Preparation** if you have prepared the required files.

   e. In the **Image Information** area, set the following parameters.

      -  **OS Type**: The value is **Windows** or **Linux**.
      -  **Data Disk**: The value ranges from 1 GB to 2048 GB and must be no less than the data disk size in the image file.
      -  **Name**: Enter a name for the image.
      -  (Optional) **Encryption**: If you want to encrypt the image, select **KMS encryption** and then select the key to be used from the key list.
      -  **Enterprise Project**: Select an enterprise project from the drop-down list. This parameter is available only if you have enabled enterprise projects or your account is an enterprise account. To enable this function, contact your customer manager. An enterprise project provides central management of cloud resources on a project.
      -  (Optional) **Tag**: Set a tag key and a tag value for the image to easily identify and manage it.
      -  (Optional) **Description**: Enter description of the image.

   f. Click **Create Now**.

   g. Confirm the settings and click **Submit**.

#. Go back to the **Private Images** page and view the new data disk image.

   When the image status changes to **Normal**, the image creation is complete.

.. _en-us_topic_0084064672__section14131852173714:

Follow-up Procedure
-------------------

If you want to use the created data disk image to create an EVS disk and attach it to an ECS, you can perform either of the following operations:

-  Locate the row that contains the created data disk image and click **Create Data Disk** to create one or multiple data disks. Then attach the data disks to an ECS.
-  On the page for creating ECSs, click **Create Disk from Data Disk Image** and select the data disk image.

   .. note::

      A data disk image can be used to create a data disk for an ECS only once.
