:original_name: en-us_topic_0133773658.html

.. _en-us_topic_0133773658:

Overview
========

If an image file is larger than 128 GB, you can import it using fast import. Only the RAW and ZVHD2 formats support fast import. The image file to be imported cannot exceed 1 TB.

Methods
-------

You can import an image file in any of the following methods depending on the file format:

-  ZVHD2

   #. Optimize the image file.
   #. Upload the image file to an OBS bucket.
   #. Register the image file on the cloud platform.

-  RAW

   #. Optimize the image file.
   #. Generate a bitmap file for the image file.
   #. Upload the image file and bitmap file to an OBS bucket.
   #. Register the image file on the cloud platform.

-  Others

   -  If the file format is converted to ZVHD2:

      #. Optimize the image file.
      #. Convert the image file format to ZVHD2.
      #. Upload the image file to an OBS bucket.
      #. Register the image file on the cloud platform.

   -  If the file format is converted to RAW:

      #. Optimize the image file.
      #. Convert the image file format to RAW and generate a bitmap file for the image file.
      #. Upload the image file and bitmap file to an OBS bucket.
      #. Register the image file on the cloud platform.

.. note::

   -  The import of large files depends on lazy loading which defers loading of file data until it is needed. This reduces the initial loading time. However, RAW files do not support this feature. When you upload a RAW file, you need to upload its bitmap together.
   -  For details about how to optimize an image file, see :ref:`Optimization Process <en-us_topic_0047501112>` (Windows) or :ref:`Optimization Process <en-us_topic_0047501133>` (Linux) depending on the OS type specified in the image file.

Import Process
--------------

The following describes how to import an external image file. Assume that you need to convert the file format to ZVHD2 or RAW.

You can use **qemu-img-hw** or the open-source tool **qemu-img** to convert the image format. **qemu-img-hw** can only be used in Linux.

.. note::

   The tool package contains **qemu-img-hw** (for converting image formats) and **CreateMF.jar** (for generating bitmap files).

-  Linux

   You are advised to use an EulerOS ECS to convert the file format.


   .. figure:: /_static/images/en-us_image_0210189238.png
      :alt: **Figure 1** Import process

      **Figure 1** Import process

   For details, see :ref:`Quickly Importing an Image File (Linux) <en-us_topic_0133773660>`.

-  Windows

   You are advised to use a local PC running Windows to convert the file format.

   .. note::

      **qemu-img** cannot convert image files to the ZVHD2 format. You need to convert an image file to the RAW format and then use **CreateMF.jar** to generate a bitmap file.


   .. figure:: /_static/images/en-us_image_0210206922.png
      :alt: **Figure 2** Import process (Windows)

      **Figure 2** Import process (Windows)

   For details, see :ref:`Quickly Importing an Image File (Windows) <en-us_topic_0174703579>`.
