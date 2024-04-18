:original_name: en-us_topic_0193146244.html

.. _en-us_topic_0193146244:

Image Creation FAQs
===================

How Can I Use an ECS to Quickly Provision Identical ECSs?
---------------------------------------------------------

If you have an ECS with applications deployed, you can use the ECS to create a private image and then use the image to create identical ECSs. In this way, you do not need to deploy applications repeatedly.

-  :ref:`Creating a System Disk Image from a Windows ECS <en-us_topic_0030713149>`
-  :ref:`Creating a System Disk Image from a Linux ECS <en-us_topic_0030713180>`
-  :ref:`Creating ECSs from an Image <en-us_topic_0030713200>`

How Many Private Images Can I Create Under an Account?
------------------------------------------------------

Currently, you can create a maximum of 100 private images under an account in a region.

Do I Have to Stop the ECS Before Using It to Create a Private Image?
--------------------------------------------------------------------

No. You can create an image from a running ECS. However, if data is written to the ECS during image creation, that new data will not be included in the created image.

Where Can I View the Image Creation Progress? How Long Does It Take to Create an Image?
---------------------------------------------------------------------------------------

Log in to the management console. Choose **Computing** > **Image Management Service** and click the **Private Images** tab. Monitor the image creation progress in the **Status** column.

The image creation involves the installation of KVM drivers, OS kernel loading, and GRUB boot configuration, which may take a long time. In addition, the network speed, image file type, and disk size have an impact on how long image creation takes.

Can I Select a Private Image Created Under a Subaccount When Creating an ECS Under the Main Account?
----------------------------------------------------------------------------------------------------

Yes.

Private images created under a subaccount are visible to the main account and all the other subaccounts (if any) under the main account.

-  If the private image is a system disk image or full-ECS image, you can select **Private Image** for **Image** when creating an ECS. Then, select this image from the drop-down list.
-  If the private image is a data disk image, select **Create from image** for **Select Data Source** when creating an EVS disk. Then, select this image in the displayed dialog box.

In addition, private images created under the main account are visible to all of its subaccounts.
