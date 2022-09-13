:original_name: en-us_topic_0030713201.html

.. _en-us_topic_0030713201:

Deleting Images
===============

Scenarios
---------

You can delete private images that will no longer be used.

Procedure
---------

#. Access the IMS console.

   a. Log in to the management console.

   b. Under **Compute**, click **Image Management Service**.

      The IMS console is displayed.

#. Click the **Private Images** tab to display the image list.

#. Locate the row that contains the image, choose **More** > **Delete** in the **Operation** column.

   .. note::

      To delete multiple images:

      a. Select the images you want to delete in the image list.
      b. Click **Delete** above the image list.

#. (Optional) Select **Delete CSBS backups of the full-ECS images**.

   This parameter is available only when you have selected full-ECS images from the image list.

   If you select this option, the system will delete CSBS backups of the full-ECS images.

   .. note::

      If CSBS backups failed to be deleted, the cause may be that these backups are being created and cannot be deleted. In this case, manually delete them as prompted.

#. Click **Yes**.
