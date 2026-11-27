:original_name: en-us_topic_0046588153.html

.. _en-us_topic_0046588153:

Encrypting an Image
===================

You can create encrypted images to securely store data.

.. note::

   -  To use image encryption, you must apply for KMS Administrator permissions. For details, see :ref:`Creating a User and Granting Permissions <en-us_topic_0171668650>`.
   -  An encrypted full-ECS image may contain multiple disks. The encryption status of each disk may be different. So, the encryption status of a full-ECS image is displayed as - in the image list.
   -  An encrypted full-ECS image inherits the encryption status of each disk of the ECS used to create the image. The inherited status cannot be changed.
   -  For details about how to check the encryption status of a disk in an encrypted full-ECS image, see :ref:`How Do I Check the Encryption Status of a Disk in an Encrypted Full-ECS Image? <en-us_topic_0049196765__section460431416289>`
   -  When you share an encrypted image with a user, ensure that the user has permissions for the key used to encrypt the image.

Constraints
-----------

-  KMS must be enabled.
-  An image encrypted using the default key cannot be shared with other users.
-  The system disk of an ECS created from an encrypted image is also encrypted, and its key is the same as the image key.
-  If an ECS has an encrypted system disk, private images created from the ECS are also encrypted.
-  The key used for encrypting an image cannot be changed.
-  If the key used for encrypting an image is disabled or deleted, the image is unavailable.
-  Encrypted full-ECS images cannot be replicated across regions.

.. _en-us_topic_0046588153__section2084462112332:

Introduction
------------

You can create an encrypted image in the following ways:

-  Create an encrypted image from an image file.

   When you register an image file as a private image, select **KMS encryption** and select a key. For details, see :ref:`Creating a Windows System Disk Image from an Image File <en-us_topic_0000002214579410>` and :ref:`Creating a Linux System Disk Image from an Image File <en-us_topic_0030713190>`.

-  Create an encrypted image from an encrypted ECS.

   When you use an ECS to create a private image, if the system disk of the ECS is encrypted, the private image created from this ECS will also be encrypted. The key used for encrypting the image is the same as that used for encrypting the system disk. For details, see :ref:`Creating a Windows System Disk Image from an ECS <en-us_topic_0030713149>` and :ref:`Creating a Linux System Disk Image from an ECS <en-us_topic_0030713180>`.

-  Replicate an unencrypted image to an encrypted image.

   If you want to store an unencrypted image in an encrypted way, you can replicate this image as a new one and encrypt the new image using a key. For details, see :ref:`Replicating Images <en-us_topic_0049177180>`.
