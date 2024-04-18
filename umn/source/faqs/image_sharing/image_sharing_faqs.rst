:original_name: en-us_topic_0183293890.html

.. _en-us_topic_0183293890:

Image Sharing FAQs
==================

How Many Tenants Can I Share an Image with?
-------------------------------------------

A system disk image or data disk image can be shared with up to 256 tenants, but a full-ECS image can only be shared with up to 10 tenants.

How Many Images Can Be Shared with Me?
--------------------------------------

There is no limit.

Do Shared Images Affect My Private Image Quota?
-----------------------------------------------

No.

I Shared an Image to an Account But the Account Did Not Accept or Reject the Image. Will My Image Sharing Quota Be Consumed?
----------------------------------------------------------------------------------------------------------------------------

No.

Where Can I View the Images Shared with Me?
-------------------------------------------

Switch to the region where the shared image is located, choose **Service List** > **Computing** > **Image Management Service** > **Images Shared with Me**.

If you are a multi-project user, make clear which of your projects will receive the shared image. Switch to the region where the project resides and select the project. Then, choose **Service List** > **Computing** > **Image Management Service** > **Images Shared with Me**.

If the image is not accepted, a red dot is displayed on the **Images Shared with Me** tab page and a message is displayed, asking you whether to accept the shared image. After the image is accepted, it is displayed in the list on the **Images Shared with Me** tab page.

If I Want to Share a System Disk Image with Another Account, Should the Account Purchase an ECS in Advance?
-----------------------------------------------------------------------------------------------------------

No. The account can use the shared image to apply for ECSs.

Is There Any Restriction on the Region When I Create ECSs Using a Shared Image?
-------------------------------------------------------------------------------

Yes. You can only create ECSs in the same region as the shared image.

Can I Share Images Shared with Me with Other Tenants?
-----------------------------------------------------

You cannot directly share such images with other tenants. If you do need to do so, you can replicate a shared image to a private image and then share the private image.

Can I Use an Image I Have Shared with Others to Create an ECS?
--------------------------------------------------------------

Yes. After sharing an image with other tenants, you can still use the image to create an ECS and use the created ECS to create a private image.

What Are the Risks of Creating ECSs Using a Shared Image?
---------------------------------------------------------

The image owner can view, stop sharing, or delete the image at any time. After the shared image is deleted, you will be unable to use the shared image to reinstall the OSs of the ECSs created from the shared image or create ECSs with the same configurations.

The cloud platform does not ensure the integrity or security of images shared by other accounts. For security reasons, you are advised to choose only images shared by trusted accounts.

What Are the Risks of Sharing Images with Other Tenants?
--------------------------------------------------------

Data, files, and software may be disclosed. Before sharing an image, you must take care to delete any sensitive data or important files from the image. The image recipient can use the shared image to create ECSs and use the created ECSs to create private images. If the created private images are shared with other tenants, any data leakage that occurs can be quite widespread.

Can I Specify a Region or an AZ for Sharing an Image?
-----------------------------------------------------

No. When sharing an image, you can only specify a project ID. You cannot specify a region or an AZ. An image can only be shared within a given region, but once shared, it can be used in any AZ in that region.

Can I Restore My Data Disks from a Data Disk Image Shared by Another Account?
-----------------------------------------------------------------------------

No. You can only use the shared image to apply for a new data disk and cannot use it to restore your existing data disks. However, you can use the new data disk for restoration by referring to :ref:`Can I Import Data from a Data Disk Image to a Data Disk? <en-us_topic_0030713154>`

What Can I Do If I Want to Use a Rejected Image?
------------------------------------------------

If you have rejected an image shared by another tenant, but now want to use it, two methods are available:

-  Method 1

   Ask the image owner to add you to the tenants the image is shared with. For details, see :ref:`Adding Tenants Who Can Use Shared Images <en-us_topic_0032042423>`.

-  Method 2

   Accept the rejected image again. For details, see :ref:`Accepting Rejected Images <en-us_topic_0075730699>`.
