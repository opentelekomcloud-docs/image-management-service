:original_name: en-us_topic_0174703579.html

.. _en-us_topic_0174703579:

Quickly Importing an Image File (Windows)
=========================================

Scenarios
---------

This section describes how to convert the format of an image file on a Windows server and then quickly import it to the cloud platform. You are advised to use a local Windows PC for converting image formats and generating bitmap files.

In Windows, use the open-source tool **qemu-img** to convert image formats. **qemu-img** supports conversion between image files of the VHD, VMDK, QCOW2, RAW, VHDX, QCOW, VDI, and QED formats. Convert an image to the RAW format and then use the **CreateMF.jar** tool to generate a bitmap file.

Prerequisites
-------------

-  The image file has been optimized. For details, see :ref:`Optimization Process <en-us_topic_0047501112>` (Windows) or :ref:`Optimization Process <en-us_topic_0047501133>` (Linux). Ensure that the image file meets the requirements in :ref:`Table 1 <en-us_topic_0030713189__table85212269215>` (Windows) or :ref:`Table 1 <en-us_topic_0030713198__table85212269215>` (Linux).

   .. note::

      Select the reference content based on the OS type in the image file.

-  An OBS bucket has been created on the management console, and OBS Browser has been ready.

Procedure
---------

#. Install the open-source tool **qemu-img**.

#. Run the **cmd** command to go to the **qemu-img** installation directory and run the **qemu-img** command to convert the image file to the RAW format.

   For example, run the following command to convert an **image.qcow2** file to an **image.raw** file:

   **qemu-img convert -p -O raw image.qcow2 image.raw**

#. Use **CreateMF.jar** to generate a bitmap file.

   a. Obtain the **CreateMF.jar** package and decompress it.

      .. table:: **Table 1** CreateMF.jar package

         +--------------------+---------------------------------------------------------------------------------+
         | Tool Package       | How to Obtain                                                                   |
         +====================+=================================================================================+
         | quick-import-tools | https://obs-20181128.ims.obs.eu-de.otc.t-systems.com/DT-image-convert-tools.zip |
         +--------------------+---------------------------------------------------------------------------------+

   b. Ensure that JDK has been installed in the current environment.

      You can verify the installation by running **cmd.exe** and then **java -version**. If Java version information is displayed, JDK has been installed.

   c. Go to the directory where **CreateMF.jar** is stored.

      For example, if you have downloaded **CreateMF.jar** to **D:/test**, run the following commands to access the directory:

      **D:**

      **cd test**

   d. Run the following command to generate a bitmap file for the RAW image file:

      **java -jar CreateMF.jar D:/image01.raw D:/image01.mf**

#. Use OBS Browser to upload the converted image file and its bitmap file to an OBS bucket.

   You must upload the RAW image file and its bitmap file to the same OBS bucket.

#. Register a private image.

   You can register a private image using the converted ZVHD2 or RAW file on the console or using an API.

   Method 1: Register a private image on the console.

   a. Access the IMS console.

      #. Log in to the management console.

      #. Under **Compute**, click **Image Management Service**.

         The IMS console is displayed.

   b. In the upper right corner, click **Create Image**.

   c. In the **Image Type and Source** area, select **System disk image** or **Data disk image** for **Type**.

   d. Select **Image File** for **Source**. Select the bucket storing the ZVHD2 or RAW image file and then select the image file. If the image file is in the RAW format, you also need to select its bitmap file.

   e. Select **Enable Fast Create**, and select the sentence following **Image File Preparation**.


      .. figure:: /_static/images/en-us_image_0210228327.png
         :alt: **Figure 1** Quickly importing an image file

         **Figure 1** Quickly importing an image file

   f. Set parameters as prompted.

      For details about the parameters, see :ref:`Registering an External Image File as a Private Image <en-us_topic_0030713184>` and :ref:`Registering an External Image File as a Private Image <en-us_topic_0030713193>`.

      .. caution::

         -  The OS must be the same as that in the image file.

         -  The system disk size must be greater than the one specified in the image file.

            Run the following command to check the system disk size in the image file:

            **qemu-img-hw** **info** *test.zvhd2*

   Method 2: Register a private image using an API.

   You can use the POST /v2/cloudimages/quickimport/action API to quickly import an image file.

   For details about how to call this API, see "Importing an Image File Quickly" in *Image Management Service API Reference*.
