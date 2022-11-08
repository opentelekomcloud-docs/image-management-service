:original_name: en-us_topic_0090099339.html

.. _en-us_topic_0090099339:

Exporting Image List
====================

Scenarios
---------

You can export the public or private image list in the current region as a CSV file to your local PC.

-  For public images, the file describes the image name, image status, OS, image type, image creation time, system disk, and minimum memory.
-  For private images, the file describes the image name, image ID, image status, OS, image type, image creation time, disk sizes, shared disks, image size, minimum memory, and encryption.

Exporting Private Image Information
-----------------------------------

#. Access the IMS console.

   a. Log in to the management console.

   b. Under **Compute**, click **Image Management Service**.

      The IMS console is displayed.

#. Click the **Private Images** tab and click |image1|.

   The system will automatically export all private images in the current region under your account to a local directory.

   .. note::

      The file name is in the format of **private-images-**\ *Region ID*\ ``-``\ *Export time*.

Exporting Public Image Information
----------------------------------

#. Access the IMS console.

   a. Log in to the management console.

   b. Under **Compute**, click **Image Management Service**.

      The IMS console is displayed.

#. Click the **Public Images** tab and click |image2|.

   The system will automatically export all public images in the current region to a local directory.

   .. note::

      The file name is in the format of **public-images-**\ *Region ID*\ ``-``\ *Export time*.

.. |image1| image:: /_static/images/en-us_image_0142360062.png
.. |image2| image:: /_static/images/en-us_image_0144424631.png
