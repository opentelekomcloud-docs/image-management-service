:original_name: en-us_topic_0030713200.html

.. _en-us_topic_0030713200:

Creating an ECS from an Image
=============================

Scenarios
---------

You can use a public, private, or shared image to create an ECS.

-  If you use a public image, the created ECS contains an OS and preinstalled public applications. You need to install applications as needed.
-  If you use a private or shared image, the created ECS contains an OS, preinstalled public applications, and a user's personal applications.

Procedure
---------

#. Access the IMS console.

   a. Log in to the management console.

   b. Under **Compute**, click **Image Management Service**.

      The IMS console is displayed.

#. Click the **Public Images**, **Private Images**, or **Images Shared with Me** tab to display the image list.

#. Locate the row that contains your desired image and click **Apply for Server** in the **Operation** column.

#. For details about how to create an ECS, see *Elastic Cloud Server User Guide*.

   When you use a system disk image to create an ECS, you can set the ECS specifications and system disk type without considering those in the image, but the system disk size can only be larger than that in the image.

   .. note::

      If a full-ECS image contains multiple data disks, it takes some time to load and display the disk information.
