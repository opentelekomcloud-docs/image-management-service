:original_name: en-us_topic_0205267846.html

.. _en-us_topic_0205267846:

Full-ECS Image FAQs
===================

What Is a Full-ECS Image?
-------------------------

A full-ECS image contains the OS, applications, and service data of an ECS. Generally, a full-ECS image is used to migrate all data of an ECS. For example:

-  Sharing an ECS with other users
-  Migrating data from an old ECS to a new one

Why Do I Have to Select a Vault When Creating a Full-ECS Image? Do I Need to Pay for the Vault?
-----------------------------------------------------------------------------------------------

When creating a full-ECS image from a CBR backup, you must select a vault. The vault is where your image and backup are stored. You need to pay for the vault.

When creating a full-ECS image from a CSBS backup, the space used to store the image and CSBS backup is not open to users but still need to be billed.

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
