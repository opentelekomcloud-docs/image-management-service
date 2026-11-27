:original_name: en-us_topic_0049177180.html

.. _en-us_topic_0049177180:

Replicating Images
==================

Scenarios
---------

You can convert encrypted and unencrypted images into each other or enable some advanced features (such as fast ECS creation from an image) using image replication. You may need to replicate an image to:

-  Replicate an encrypted image to an unencrypted one.

-  Replicate an encrypted image to an encrypted one.

   Keys for encrypting the images cannot be changed. If you want to change the key of an encrypted image, you can replicate this image to a new one and encrypt the new image using an encryption key.

-  Replicate an unencrypted image to an encrypted one.

   If you want to store an unencrypted image in an encrypted way, you can replicate this image as a new one and encrypt the new image using a key.

-  Optimize a system disk image so that it can be used for fast ECS creation.

   Fast Create greatly reduces the time required for creating ECSs from a system disk image. Currently, this feature is supported by all newly created system disk images by default. Existing system disk images may not support it. You can enable them to support this feature through image replication. For example, if image A does not support fast ECS creation, you can replicate it to generate image copy_A that supports fast ECS creation.

Constraints
-----------

-  Full-ECS images cannot be replicated.
-  Private images created using ISO files do not support in-region replication.

Prerequisites
-------------

The images to be replicated are in the **Normal** state.

Procedure
---------

#. Log in to the management console.

   a. Under **Computing**, click **Image Management Service**. The IMS console is displayed.

#. Locate the row that contains the image to be replicated, click **More** in the **Operation** column, and select **Replicate**.

#. In the displayed **Replicate Image** dialog box, set the following parameters:

   .. table:: **Table 1** Parameters

      +-----------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+-----------------------+
      | Parameter             | Description                                                                                                                                                                                                                                                                                   | Example Value         |
      +=======================+===============================================================================================================================================================================================================================================================================================+=======================+
      | Name                  | Enter a name that is easy to identify.                                                                                                                                                                                                                                                        | copy_image_001        |
      +-----------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+-----------------------+
      | Enterprise Project    | This parameter is for enterprise users. To use this function, contact customer service to enable it.                                                                                                                                                                                          | default               |
      |                       |                                                                                                                                                                                                                                                                                               |                       |
      |                       | An enterprise project groups cloud resources, so you can manage resources and users by project. The default project is **default**.                                                                                                                                                           |                       |
      |                       |                                                                                                                                                                                                                                                                                               |                       |
      |                       | Select an enterprise project from the drop-down list.                                                                                                                                                                                                                                         |                       |
      +-----------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+-----------------------+
      | Description           | This parameter is optional. Enter a description for the image.                                                                                                                                                                                                                                | ``-``                 |
      +-----------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+-----------------------+
      | Encryption            | This parameter is optional. If you want to encrypt the image, select **KMS encryption** and select the key name to be used from the key list. After you select **KMS encryption**, the system will create a default key **ims/default** for you. You can also select a key from the key list. | ``-``                 |
      |                       |                                                                                                                                                                                                                                                                                               |                       |
      |                       | For details about how to encrypt an image, see :ref:`Introduction <en-us_topic_0046588153__section2084462112332>`.                                                                                                                                                                            |                       |
      +-----------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+-----------------------+

#. Click **OK**.

   On the **Private Images** page, view the replication progress. If the status of the new image becomes **Normal**, the image replication is successful.
