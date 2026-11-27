:original_name: en-us_topic_0030713200.html

.. _en-us_topic_0030713200:

Creating an ECS from an Image
=============================

Scenarios
---------

You can use a public, private, or shared image to create an ECS.

-  If you use a public image, the created ECS contains an OS and preinstalled public applications. You need to install other applications as needed.
-  If you use a private or shared image, the created ECS contains an OS, preinstalled public applications, and a user's personal applications.

Procedure
---------

#. Log in to the management console.

   a. Under **Computing**, click **Image Management Service**. The IMS console is displayed.

#. Click the **Public Images**, **Private Images**, or **Images Shared with Me** tab to display the image list.
#. Locate the row that contains your desired image and click **Apply for Server** in the **Operation** column.
#. For details about how to create an ECS, see *Elastic Cloud Server User Guide*.

   .. note::

      -  If you create an ECS from a private system disk image, you can change the instance specifications and system disk type, but the system disk size must be greater than that in the image.
      -  If you create an ECS from a private full-ECS image that contains one or more data disks, the system automatically sets the data disk parameters for the ECS. You can increase the capacity of a system disk or data disks, but cannot decrease it.
      -  If a full-ECS image contains multiple data disks, it takes some time to load and display the disk information.
