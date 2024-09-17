:original_name: en-us_topic_0193146244.html

.. _en-us_topic_0193146244:

General Creation FAQs
=====================

How Can I Use an ECS to Quickly Provision Identical ECSs?
---------------------------------------------------------

If you have an ECS with applications deployed, you can use the ECS to create a private image and then use the image to create identical ECSs. In this way, you do not need to deploy applications repeatedly.

-  :ref:`Creating a System Disk Image from a Windows ECS <en-us_topic_0030713149>`
-  :ref:`Creating a System Disk Image from a Linux ECS <en-us_topic_0030713180>`
-  :ref:`Creating ECSs from an Image <en-us_topic_0030713200>`

How Many Private Images Can I Create Under an Account?
------------------------------------------------------

You can create up to 100 private images under an account in a region.

Do I Have to Stop the ECS Before Using It to Create a Private Image?
--------------------------------------------------------------------

No. You can create an image from a running ECS. But the data that was written into the ECS during the image creation will not be included in the image.

Where Can I Check the Image Creation Progress? How Long Does It Take to Create an Image?
----------------------------------------------------------------------------------------

Log in to the management console. Choose **Computing** > **Image Management Service** and click the **Private Images** tab. Check the image creation progress in the **Status** column.

Creating an image may take a period of time because it requires to install KVM drivers, load the OS kernel, and configure GRUB boot. In addition, the network speed, image file type, and disk size all have impacts on how long the entire process takes.

Can I Use a Private Image of an IAM User Under My Account to Create an ECS?
---------------------------------------------------------------------------

Yes.

Private images created by an IAM user are visible to the account that the IAM user belongs to as well as all other IAM users (if any) under this account.

-  You can use a system disk image or full-ECS image to create an ECS.
-  You can use a data disk image to create an EVS disk.

In addition, private images created by an account are visible to IAM users under this account.
