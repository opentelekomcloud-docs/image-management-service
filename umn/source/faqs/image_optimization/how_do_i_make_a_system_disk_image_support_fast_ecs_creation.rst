:original_name: en-us_topic_0187108863.html

.. _en-us_topic_0187108863:

How Do I Make a System Disk Image Support Fast ECS Creation?
============================================================

Scenarios
---------

Fast Create greatly reduces the time required for creating ECSs from a system disk image. Currently, this feature is supported by all newly created system disk images by default. Some existing system disk images may not support this feature, you can make them support it through image replication.

For example, if image A does not support fast ECS creation, you can replicate it to generate image copy_A that supports fast ECS creation.

Constraints
-----------

Full-ECS images cannot be configured using this method.

Check Whether an Image Supports Fast ECS Creation
-------------------------------------------------

#. Access the IMS console.

   a. Log in to the management console.

   b. Under **Computing**, click **Image Management Service**.

      The IMS console is displayed.

#. Click the **Private Images** tab to display the image list.
#. Click the name of the target image.
#. On the displayed image details page, check the value of **Fast ECS Creation**.

Configure an Image to Make It Support Fast ECS Creation
-------------------------------------------------------

#. Locate the target system disk image, click **More** in the **Operation** column, and select **Replicate** from the drop-down list.

   The **Replicate Image** dialog box is displayed.

#. Set parameters based on :ref:`Replicating Images <en-us_topic_0049177180>`.

#. After the image is successfully replicated, the generated image can be used to quickly create ECSs.
