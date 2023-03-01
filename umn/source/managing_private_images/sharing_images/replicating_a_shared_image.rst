:original_name: en-us_topic_0172473649.html

.. _en-us_topic_0172473649:

Replicating a Shared Image
==========================

Scenarios
---------

Replicate a private image that was shared with you. The image is displayed in the private image list. You can export, share, and replicate this image, or use it to create ECSs.

If the shared image to be replicated is an encrypted image, you can replace the key of the image with your own key when replicating the image. This prevents the shared image from being unavailable when the tenant who shares the image cancels the key authorization.

Constraints
-----------

-  Only accepted shared images can be replicated.

   To replicate a rejected shared image, you must accept the image first. For details, see :ref:`Accepting Rejected Images <en-us_topic_0075730699>`.

-  Currently, only system and data disk images can be replicated. Full-ECS images are not supported.

-  Currently, images can only be replicated within a region.

-  An image to be replicated cannot be larger than 128 GB.

Procedure
---------

#. Access the IMS console.

   a. Log in to the management console.

   b. Under **Compute**, click **Image Management Service**.

      The IMS console is displayed.

#. On the displayed IMS console, click the **Images Shared with Me** tab.

   Shared images that are accepted are displayed.

#. Locate a shared image, click **More** in the **Operation** column, and select **Replicate** from the drop-down list.


   .. figure:: /_static/images/en-us_image_0172485503.png
      :alt: **Figure 1** Replicating an image

      **Figure 1** Replicating an image

#. In the **Replicate Image** dialog box, specify **Name**, **Enterprise Project**, and **Description**.

#. Click **OK**.

   You can click the **Private Images** tab and view the creation progress of the image in the private image list. When the image status changes to **Normal**, the image creation is complete.
