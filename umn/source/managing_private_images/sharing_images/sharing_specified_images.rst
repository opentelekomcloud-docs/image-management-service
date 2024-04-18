:original_name: en-us_topic_0032042419.html

.. _en-us_topic_0032042419:

Sharing Specified Images
========================

Scenarios
---------

After obtaining the project ID from a tenant, you can share specified private images with the tenant. You can share a single image or multiple images as needed.

Prerequisites
-------------

-  If the image to be shared is an encrypted image, authorize the key (it must be a custom key) used for encrypting the image. For details, see :ref:`How Do I Authorize a Key? <en-us_topic_0133773781>`

-  You have obtained the project ID from the target tenant.
-  Before sharing an image, ensure that any sensitive data has been deleted from the image.

Procedure
---------

-  Share multiple images.

   #. Access the IMS console.

      a. Log in to the management console.

      b. Under **Computing**, click **Image Management Service**.

         The IMS console is displayed.

   #. Click the **Private Images** tab.

   #. Select the private images to share and click **Share** above the image list.

   #. In the **Share Image** dialog box, enter the project ID of the target tenant.

      To share images with more than one tenant, separate their project IDs with commas (,).

      .. note::

         -  You can enter a maximum of 100 project IDs at a time.
         -  You can share images only within the region where they reside.
         -  If the target tenant is a multi-project user, you can share images to any project of the tenant.

   #. Click **OK**.

-  Share a single image.

   #. Access the IMS console.

      a. Log in to the management console.

      b. Under **Computing**, click **Image Management Service**.

         The IMS console is displayed.

   #. Click the **Private Images** tab.

   #. Locate the row that contains the private image you are to share, click **More** in the **Operation** column, and select **Share** from the drop-down list.

   #. In the **Share Image** dialog box, enter the project ID of the target tenant.

      To share an image with more than one tenant, separate their project IDs with commas (,).

      .. note::

         -  You can enter a maximum of 100 project IDs at a time.
         -  You can share images only within the region where they reside.
         -  If the target tenant is a multi-project user, you can share images to any project of the tenant.


      .. figure:: /_static/images/en-us_image_0000001538100365.png
         :alt: **Figure 1** Sharing an image

         **Figure 1** Sharing an image

   #. Click **OK**.

Related Operations
------------------

-  After you share images with a tenant, the tenant can accept the shared images on the **Images Shared with Me** page on the IMS console. For detailed operations, see :ref:`Accepting or Rejecting Shared Images <en-us_topic_0032042420>`.
-  If the shared image is an encrypted image and is accepted by a tenant, the tenant can use this image to apply for ECSs or replace the key of this image with its own by replicating the shared image. If the tenant has accepted the shared image but have not performed any other operations, do not cancel the authorization of the key. Otherwise, the shared image will be unavailable to the tenant.
