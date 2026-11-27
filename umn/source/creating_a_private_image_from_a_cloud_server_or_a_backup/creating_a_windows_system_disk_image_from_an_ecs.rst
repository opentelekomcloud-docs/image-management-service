:original_name: en-us_topic_0030713149.html

.. _en-us_topic_0030713149:

Creating a Windows System Disk Image from an ECS
================================================

Scenarios
---------

If you have created and configured an ECS based on your service requirements (for example, by installing software and setting up an application environment), you can use this ECS to create a system disk image. Then, all new ECSs created from this image will have the same software and environment preinstalled.

Creating a system disk image does not affect services on the cloud server or cause data loss.

Background
----------

The following figure shows the process of creating a system disk image from a cloud server and using the image to create new cloud servers.


.. figure:: /_static/images/en-us_image_0254928267.png
   :alt: **Figure 1** Creating a system disk image and using it to create new cloud servers

   **Figure 1** Creating a system disk image and using it to create new cloud servers

-  System disk images are often used for application scale-out. They can also be used for hybrid cloud deployment. You can create system disk images for resource synchronization on and off cloud. The procedure is as follows:

   #. Create a system disk image from a cloud server.

      .. note::

         If the cloud server is created from any of the following images, the system disk image cannot be exported:

         -  Private images created from a SUSE, Red Hat, Ubuntu, Oracle Linux, or Windows public image

   #. Export the image to an OBS bucket. For details, see :ref:`Exporting an Image <en-us_topic_0034011241>`.
   #. Download the image file from the OBS bucket.

-  You can create an image from a running cloud server.

   The image creation does not affect services on the cloud server.

   In this process, do not stop, start, or restart the cloud server, or the image creation may fail.

-  The time required for creating an image depends on the system disk size, network quality, and the number of concurrent tasks.

-  A system disk image will be created in the same region as the cloud server that was used to create it.

-  If a cloud server has expired or been released, you can use the system disk image created from the cloud server to restore it.

Prerequisites
-------------

Before creating a private image from a cloud server:

-  Delete any sensitive data the ECS may contain.
-  Ensure that the ECS is in the **Running** or **Stopped** state.
-  Complete all operations in :ref:`Windows Private Images <en-us_topic_0130878748>` or :ref:`Linux Private Images <en-us_topic_0130878749>` to configure the cloud server.

Procedure
---------

#. Log in to the management console.

   a. Under **Computing**, click **Image Management Service**. The IMS console is displayed.

#. Create a system disk image.

   a. Click **Create Image** in the upper right corner.

   b. Set image parameters.

      :ref:`Table 1 <en-us_topic_0030713149__table050019474117>` and :ref:`Table 2 <en-us_topic_0030713149__table6978715749>` list the parameters in the **Image Type and Source** and **Image Information** areas, respectively.

      .. _en-us_topic_0030713149__table050019474117:

      .. table:: **Table 1** Image type and source

         +------------+----------------------------------------------------------------+
         | Parameter  | Description                                                    |
         +============+================================================================+
         | Type       | Select **Create Image**.                                       |
         +------------+----------------------------------------------------------------+
         | Region     | Select a region close to where your services will be provided. |
         +------------+----------------------------------------------------------------+
         | Image Type | Select **System disk image**.                                  |
         +------------+----------------------------------------------------------------+
         | Source     | Select a cloud server with required configurations.            |
         +------------+----------------------------------------------------------------+

      .. _en-us_topic_0030713149__table6978715749:

      .. table:: **Table 2** Image information

         +-----------------------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
         | Parameter                         | Description                                                                                                                                                                                                                      |
         +===================================+==================================================================================================================================================================================================================================+
         | Name                              | Set a name for the image.                                                                                                                                                                                                        |
         +-----------------------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
         | Enterprise Project                | Select an enterprise project from the drop-down list. This parameter is available only if you have enabled enterprise projects or your account is an enterprise account. To enable this function, contact your customer manager. |
         |                                   |                                                                                                                                                                                                                                  |
         |                                   | An enterprise project groups cloud resources, so you can manage resources and users by project.                                                                                                                                  |
         +-----------------------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
         | Tag                               | This parameter is optional. Set tag keys and values for the image to make identification and management easier.                                                                                                                  |
         +-----------------------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
         | Description                       | This parameter is optional. Enter a description for the image.                                                                                                                                                                   |
         +-----------------------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+

   c. Click **Next**.

   d. Confirm the settings and click **Submit**.

#. Go back to the private image list and view the new system disk image.

   The time required for creating an image depends on the ECS system disk size, network quality, and the number of concurrent tasks. When the image status changes to **Normal**, the image creation is complete.

   .. note::

      -  Do not perform any operations on the selected ECS or its associated resources during image creation.
      -  A cloud server created from an encrypted image is also encrypted. The key used for encrypting the cloud server is the same as that used for encrypting the image.
      -  An image created from an encrypted cloud server is also encrypted. The key used for encrypting the image is the same as that used for encrypting the cloud server.
      -  The size of a new image is determined based on the maximum disk space that was ever used, not the current disk usage.

Follow-up Procedure
-------------------

After a system disk image is created, you can:

-  Use the image to create new cloud servers. For details, see :ref:`Creating an ECS from an Image <en-us_topic_0030713200>`.
-  Use the image to change the OSs of existing cloud servers.
