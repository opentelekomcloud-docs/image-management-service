:original_name: en-us_topic_0013901609.html

.. _en-us_topic_0013901609:

What Is Image Management Service?
=================================

Overview
--------

An image is a cloud server or disk template that contains an operating system (OS), service data, or necessary software.

Image Management Service (IMS) allows you to manage the entire lifecycle of your images. You can create ECSs or BMSs from public, private, or shared images. You can also create a private image from a cloud server or an external image file to make it easier to migrate workloads to the cloud or on the cloud.

Image Types
-----------

IMS provides public, private, and shared images. Public images are provided by the cloud platform, private images are created by users, and shared images are private images that other users shared with you.

+-----------------------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
| Image Type                        | Description                                                                                                                                                                                                                                                                                                                                                                                                                             |
+===================================+=========================================================================================================================================================================================================================================================================================================================================================================================================================================+
| Public                            | A public image is a standard, widely used image. It contains an OS and preinstalled public applications and is available to all users. Public images are very stable and their OS and any included software have been officially authorized for use. If a public image does not contain the environments or software you need, you can use a public image to create an ECS and then deploy the required environments or software on it. |
+-----------------------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
| Private                           | A private image contains an OS or service data, preinstalled public applications, and a user's personal applications. Private images are only available to the users who created them.                                                                                                                                                                                                                                                  |
|                                   |                                                                                                                                                                                                                                                                                                                                                                                                                                         |
|                                   | A private image can be a system disk image, data disk image, or full-ECS image.                                                                                                                                                                                                                                                                                                                                                         |
|                                   |                                                                                                                                                                                                                                                                                                                                                                                                                                         |
|                                   | -  A system disk image contains an OS and preinstalled software for various services. You can use a system disk image to create ECSs and migrate your services to the cloud.                                                                                                                                                                                                                                                            |
|                                   | -  A data disk image contains only service data. You can use a data disk image to create EVS disks and use them to migrate your service data to the cloud.                                                                                                                                                                                                                                                                              |
|                                   | -  A full-ECS image contains an OS, preinstalled software, and service data. A full-ECS image is created using differential backups and the creation takes less time than creating a system or data disk image that has the same disk capacity.                                                                                                                                                                                         |
+-----------------------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
| Shared                            | A shared image is a private image another user has shared with you.                                                                                                                                                                                                                                                                                                                                                                     |
|                                   |                                                                                                                                                                                                                                                                                                                                                                                                                                         |
|                                   | For more information, see "Sharing Images" in *Image Management Service User Guide*.                                                                                                                                                                                                                                                                                                                                                    |
+-----------------------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+

IMS Functions
-------------

IMS provides:

-  Public images that contain common OSs
-  Creation of a private image from an ECS or external image file
-  Public image management, such as searching for images by OS type, name, or ID, and viewing the image ID, system disk capacity, and image features such as user data injection and disk hot swap
-  Private image management, such as modifying image attributes, sharing images, and replicating images
-  Creation of ECSs using an image

Access Methods
--------------

The public cloud provides a web-based service management platform (a management console). You can access the IMS service through HTTPS APIs or from the management console.

-  API

   If you need to integrate IMS into a third-party system for secondary development, use APIs to access the IMS service. For details, see *Image Management Service API Reference*.

-  Management console

   If no integration with a third-party system is needed, use the management console. Log in to the management console and choose **Computing** > **Image Management Service** on the homepage.
