:original_name: en-us_topic_0049177180.html

.. _en-us_topic_0049177180:

Replicating Images
==================

Scenarios
---------

You can convert encrypted and unencrypted images into each other or enable some advanced features (such as fast ECS creation from an image) using the image replication function. You may need to replicate an image in the following scenarios:

-  Replicate an encrypted image to an unencrypted one.

-  Replicate an encrypted image to an encrypted one.

   Keys for encrypting the images cannot be changed. If you want to change the key of an encrypted image, you can replicate this image to a new one and encrypt the new image using an encryption key.

-  Replicate an unencrypted image to an encrypted one.

   If you want to store an unencrypted image in an encrypted way, you can replicate this image as a new one and encrypt the new image using a key.

-  Optimize a system disk image so that it can be used to quickly create ECSs.

   Fast Create greatly reduces the time required for creating ECSs from a system disk image. Currently, this feature is supported by all newly created system disk images by default. Existing system disk images may not support this function. You can optimize the images using the image replication function. For example, if image A does not support fast ECS creation, you can replicate it to generate image copy_A that supports fast ECS creation.

Constraints
-----------

-  Full-ECS images cannot be replicated.
-  Private images created using ISO files do not support in-region replication.

Prerequisites
-------------

The images to be replicated are in the **Normal** state.

Procedure
---------

#. Access the IMS console.

   a. Log in to the management console.

   b. Under **Computing**, click **Image Management Service**.

      The IMS console is displayed.

#. Locate the row that contains the image to be replicated, click **More** in the **Operation** column, and select **Replicate**.

#. In the displayed **Replicate Image** dialog box, set the following parameters:

   -  **Name**: Enter a name that is easy to identify.
   -  **Description**: This parameter is optional. Enter description of the replication.
   -  **Encryption**: If you want to encrypt the image or change a key, select **KMS encryption** and select the key you want to use from the drop-down list.

#. Click **OK**.

   On the **Private Images** page, view the replication progress. If the status of the new image becomes **Normal**, the image replication is successful.
