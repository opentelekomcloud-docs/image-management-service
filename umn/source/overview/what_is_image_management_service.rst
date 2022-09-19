:original_name: en-us_topic_0013901609.html

.. _en-us_topic_0013901609:

What Is Image Management Service?
=================================

Overview
--------

An image is a server or disk template that contains an operating system (OS) or service data and necessary software, such as database software. IMS provides public, private, and shared images.

Image Management Service (IMS) allows you to manage the entire lifecycle of your images. You can create ECSs or BMSs from public, private, or shared images. You can also create a private image from a cloud server or an external image file to make it easier to migrate workloads to the cloud or on the cloud.

Image Types
-----------

Images are classified as public, private, and shared. Public images are provided by the cloud platform, private images are those you created yourself, and shared images are private images that other tenants have shared with you.

+-----------------------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
| Image Type                        | Description                                                                                                                                                                                                                                                                                                                                                                                                                         |
+===================================+=====================================================================================================================================================================================================================================================================================================================================================================================================================================+
| Public image                      | A public image is a standard, widely used image. It contains an OS and preinstalled public applications and is available to all users. Public images are very stable and their OS and any included software have been officially authorized for use. If a public image does not contain the application environments or software you need, you can use a public image to create an ECS and then deploy required software as needed. |
+-----------------------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
| Private image                     | A private image contains an OS or service data, preinstalled public applications, and a user's personal applications. Private images are only available to the users who created them.                                                                                                                                                                                                                                              |
|                                   |                                                                                                                                                                                                                                                                                                                                                                                                                                     |
|                                   | A private image can be a system disk image, data disk image, or full-ECS image.                                                                                                                                                                                                                                                                                                                                                     |
|                                   |                                                                                                                                                                                                                                                                                                                                                                                                                                     |
|                                   | -  A system disk image contains an OS and pre-installed software for various services. You can use a system disk image to create ECSs and migrate your services to the cloud.                                                                                                                                                                                                                                                       |
|                                   | -  A data disk image contains only service data. You can use a data disk image to create EVS disks and use them to migrate your service data to the cloud.                                                                                                                                                                                                                                                                          |
|                                   | -  A full-ECS image contains an OS, pre-installed software, and service data. A full-ECS image is created using differential backups and the creation takes less time than creating a system or data disk image of the same size.                                                                                                                                                                                                   |
+-----------------------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
| Shared image                      | A shared image is a private image another user has shared with you.                                                                                                                                                                                                                                                                                                                                                                 |
+-----------------------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+

IMS Functions
-------------

IMS provides:

-  Public images that contain common OSs
-  Creation of a private image from an ECS or external image file
-  Public image management, such as searching for images by OS type, name, or ID, and viewing the image ID, system disk size, and image features such as user data injection and disk hot swap
-  Private image management, such as modifying image attributes, sharing images, and replicating images
-  Creation of ECSs using an image

Access Methods
--------------

The public cloud provides a web-based service management platform (a management console). You can access the IMS service through HTTPS APIs or from the management console.

-  API

   If you need to integrate IMS into a third-party system for secondary development, use APIs to access the IMS service. For details, see *Image Management Service API Reference*.

-  Management console

   If no integration with a third-party system is needed, use the management console.
