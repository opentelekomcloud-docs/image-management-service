:original_name: en-us_topic_0030713188.html

.. _en-us_topic_0030713188:

Creating a Windows ECS from an Image
====================================

Scenarios
---------

After registering an external image file as a private image on the cloud platform, you can use the image to create ECSs or change the OSs of existing ECSs.

This section describes how to create an ECS from an image.

Procedure
---------

Create an ECS by referring to :ref:`Creating an ECS from an Image <en-us_topic_0030713200>`.

Note the following when setting the parameters:

-  **Region**: Select the region where the private image is located.
-  **Specifications**: Select a flavor based on the OS type in the image and the OS versions described in :ref:`OSs Supported by Different Types of ECSs <en-us_topic_0030713142>`.
-  **Image**: Select **Private image** and then the created image from the drop-down list.
-  (Optional) **Data Disk**: Add data disks. These data disks are created from a data disk image generated together with a system disk image. In this way, you can migrate the data of data disks together with system disk data from the VM on the original platform to the current cloud platform.

Follow-up Procedure
-------------------

After a system disk image is created, you can use it to change the OS of an ECS.
