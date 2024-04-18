:original_name: en-us_topic_0030713201.html

.. _en-us_topic_0030713201:

Deleting Images
===============

Scenarios
---------

You can delete private images that will no longer be used.

-  Deleted private images cannot be retrieved. Perform this operation only when absolutely necessary.
-  After a private image is deleted, it cannot be used to create ECSs or EVS disks.
-  After a private image is deleted, ECSs created from the image can still be used and are still billed. However, the OS cannot be reinstalled for the ECSs and ECSs with the same configuration cannot be created.
-  Deleting the source image of a replicated image has no effect on the replicated image. Similarly, deleting a replicated image has no effect on its source.

Procedure
---------

#. Access the IMS console.

   a. Log in to the management console.

   b. Under **Computing**, click **Image Management Service**.

      The IMS console is displayed.

#. Click the **Private Images** tab to display the image list.

#. Locate the row that contains the image, choose **More** > **Delete** in the **Operation** column.

   .. note::

      To delete multiple images:

      a. Select the images you want to delete in the image list.
      b. Click **Delete** above the image list.

#. (Optional) Select **Delete CSBS backups or cloud server backups of the full-ECS images**.

   This parameter is available only when you have selected full-ECS images from the image list.

   If you select this option, the system will delete CSBS or CBR backups of the full-ECS images.

   .. note::

      If CSBS or CBR backups failed to be deleted, the cause may be that these backups are being created and cannot be deleted. In this case, manually delete them as prompted.

#. Click **Yes**.
