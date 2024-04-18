:original_name: en-us_topic_0032042420.html

.. _en-us_topic_0032042420:

Accepting or Rejecting Shared Images
====================================

Scenarios
---------

After another tenant shares images with you, you will receive a message. You can choose to accept or reject all or some of the shared images.

.. note::

   -  If you are not in the same region as the tenant sharing the images with you, you will not receive the message.

Prerequisites
-------------

-  Another tenant has shared images with you.
-  If the shared image is a full-ECS image, you need to create a server backup vault to store the full-ECS image and the backups of the full-ECS image before accepting the shared image. When creating a server backup vault, set **Protection Type** to **Backup**.

Procedure
---------

#. Access the IMS console.

   a. Log in to the management console.

   b. Under **Computing**, click **Image Management Service**.

      The IMS console is displayed.

#. In the upper left corner, switch to the region where the target project resides and then select the project.

#. Click the **Images Shared with Me** tab.

   A message is displayed above the image list asking you whether to accept the shared images.

   -  To accept all the shared images, click **Accept All** in the upper right corner.
   -  To accept some images, select the images and click **Accept**.
   -  To reject some images, select the images and click **Reject**.

   .. note::

      If no message is displayed, check whether you have selected a correct region.

#. (Optional) In the **Accept Full-ECS Image** dialog box, select a server backup vault with the **Backup** protection type and click **OK**.

   This dialog box is displayed when the shared image is a full-ECS image.

   When accepting a full-ECS image, you must specify a vault for storing the CBR backups associated with the full-ECS image. The vault capacity must be no less than the total capacities of the system disk and data disk backups.

   .. note::

      For more information about server backup vaults, see *Cloud Backup and Recovery User Guide*.

Results
-------

-  **Pending**: If you do not immediately accept or reject a shared image, the image is in the **Pending** state.

   A pending shared image is not displayed in the shared image list.

-  **Accepted**: After an image is accepted, it is displayed in the shared image list. You can use the image to create ECSs.

-  **Rejected**: After an image is rejected, it is not displayed in the shared image list. You can click **Rejected Images** to view the images you have rejected and you can still choose to accept them.

Follow-up Procedure
-------------------

After accepting a system disk image or full-ECS image shared by another tenant, you can:

-  Use the image to create one or more ECSs (select **Shared Image** during ECS creation).
-  Use the image to change the OS of existing ECSs. For details, see "Changing the OS" in *Elastic Cloud Server User Guide*.

After accepting a data disk image shared by another tenant, you can use the image to create EVS disks (locate the row that contains the image and click **Create Data Disk** in the **Operation** column).

After accepting the encrypted image shared by another tenant, you can use the image to apply for ECSs or EVS disks or replace the key of the image with your own key by replicating the shared image. The replacement prevents the shared image from being unavailable when the tenant who shares the image cancels the key authorization.
