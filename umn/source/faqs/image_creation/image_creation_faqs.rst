:original_name: en-us_topic_0193146244.html

.. _en-us_topic_0193146244:

Image Creation FAQs
===================

How Many Private Images Can I Create Under an Account?
------------------------------------------------------

Currently, you can create a maximum of 100 private images under an account in a region.

Do I Have to Stop the ECS Before Using It to Create a Private Image?
--------------------------------------------------------------------

No. You can create an image from a running ECS. However, if data is written to the ECS during image creation, that new data will not be included in the created image.

Where Can I View the Image Creation Progress? How Long Does It Take to Create an Image?
---------------------------------------------------------------------------------------

Log in to the management console. Choose **Compute** > **Image Management Service** and click the **Private Images** tab. Monitor the image creation progress in the **Status** column.

The image creation involves the installation of KVM drivers, OS kernel loading, and GRUB boot configuration, which may take a long time. In addition, the network speed, image file type, and disk size have an impact on how long image creation takes.
