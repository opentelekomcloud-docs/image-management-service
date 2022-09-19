:original_name: en-us_topic_0046588155.html

.. _en-us_topic_0046588155:

Creating Encrypted Images
=========================

You can create an encrypted image using an external image file or an encrypted ECS.

-  Create an encrypted image using an external image file.

   When you register the external image file as a private image, select **KMS encryption** and select a key. For details, see :ref:`Creating a Windows System Disk Image from an External Image File <en-us_topic_0030713181>` and :ref:`Creating a Linux System Disk Image from an External Image File <en-us_topic_0030713190>`.

-  Create an encrypted image using an encrypted ECS.

   When you use an ECS to create a private image, if the system disk of the ECS is encrypted, the private image created using the ECS is also encrypted. The key used for encrypting the image must be the same as that used for encrypting the system disk. For details, see :ref:`Creating a System Disk Image from a Windows ECS <en-us_topic_0030713149>` and :ref:`Creating a System Disk Image from a Linux ECS <en-us_topic_0030713180>`.
