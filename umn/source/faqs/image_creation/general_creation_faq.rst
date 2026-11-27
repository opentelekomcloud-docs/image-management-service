:original_name: en-us_topic_0193146244.html

.. _en-us_topic_0193146244:

General Creation FAQ
====================

How Can I Use an ECS to Quickly Provision Identical ECSs?
---------------------------------------------------------

If you have an ECS with applications deployed, you can use the ECS to create a private image and then use the image to create identical ECSs. In this way, you do not need to deploy applications repeatedly.

-  :ref:`Creating a Windows System Disk Image from an ECS <en-us_topic_0030713149>`
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

What Is a Full-ECS Image?
-------------------------

A full-ECS image contains the OS, applications, and service data of an ECS. Generally, a full-ECS image is used to migrate all data of an ECS. For example:

-  Sharing an ECS with other users
-  Migrating data from an old ECS to a new one

Why Do I Have to Select a Vault When Creating a Full-ECS Image? Do I Need to Pay for the Vault?
-----------------------------------------------------------------------------------------------

When creating a full-ECS image from a CBR backup, you must select a vault. The vault is where your image and backup are stored. You need to pay for the vault.

When creating a full-ECS image from a CSBS backup, the space used to store the image and CSBS backup is not open to users but still needs to be billed.

So, no matter which backup type you select, you need to pay for the storage. Selecting a vault does not mean that you need to pay extra fees.

Where Can I Check the Data Disk Details of a Full-ECS Image?
------------------------------------------------------------

To check data disk details, you need to go to the CSBS or CBR console, depending on where the full-ECS image is created from. That is because only system disk information (**Disk Capacity**) is displayed in the image list and image details after a full-ECS image is created.

The following describes how to view the data disk details in CBR:

#. In the private image list, click the full-ECS image name.

   Image details are displayed.

#. Locate **Source** and click the backup ID following it.

   The CBR backup details page is displayed.

#. Click the **Disk Backup** tab. Details about the system disk and data disks are displayed.

What Are the Restrictions on Using a Full-ECS Image?
----------------------------------------------------

-  A full-ECS image cannot be exported. You are advised to create images for the system disk and data disks separately and then export the images.
-  Only the full-ECS image created from a CBR backup can be shared with other users.
-  A full-ECS image cannot be replicated within the same region.
