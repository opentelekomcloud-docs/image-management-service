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

Can I Share Images Shared with Me with Other Tenants?
-----------------------------------------------------

You cannot directly share such images with other tenants. If you do need to do so, you can replicate a shared image to a private image and then share the private image.

Can I Use an Image I Have Shared with Others to Create an ECS?
--------------------------------------------------------------

Yes. After sharing an image with other tenants, you can still use the image to create an ECS and use the created ECS to create a private image.

When Can I Do If I Want to Use a Rejected Image?
------------------------------------------------

If you have rejected an image shared by another tenant, but now want to use it, two methods are available:

-  Method 1

   Ask the image owner to add you to the tenants the image is shared with. For details, see :ref:`Adding Tenants Who Can Use Shared Images <en-us_topic_0032042423>`.

-  Method 2

   Accept the rejected image again. For details, see :ref:`Accepting Rejected Images <en-us_topic_0075730699>`.
