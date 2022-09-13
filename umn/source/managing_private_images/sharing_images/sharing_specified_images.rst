:original_name: en-us_topic_0032042419.html

.. _en-us_topic_0032042419:

Sharing Specified Images
========================

Scenarios
---------

After obtaining the project ID from a tenant, you can share specified private images with the tenant. You can share a single image or multiple images as needed.

Prerequisites
-------------

-  You have obtained the project ID from the target tenant.
-  Before sharing an image, ensure that any sensitive data has been deleted from the image.

Procedure
---------

-  Share multiple images.

   #. Access the IMS console.

      a. Log in to the management console.

      b. Under **Compute**, click **Image Management Service**.

         The IMS console is displayed.

   #. Click the **Private Images** tab.

   #. Select the private images to share and click **Share** above the image list.

   #. In the **Share Image** dialog box, enter the project ID of the target tenant.

      To share images with more than one tenant, separate their project IDs with commas (,).

      .. note::

         You can enter a maximum of 100 project IDs at a time.

   #. Click **OK**.

-  Share a single image.

   #. Access the IMS console.

      a. Log in to the management console.

      b. Under **Compute**, click **Image Management Service**.

         The IMS console is displayed.

   #. Click the **Private Images** tab.

   #. Locate the row that contains the private image you are to share, click **More** in the **Operation** column, and select **Share** from the drop-down list.

   #. In the **Share Image** dialog box, enter the project ID of the target tenant.

      To share an image with more than one tenant, separate their project IDs with commas (,).

      .. note::

         You can enter a maximum of 100 project IDs at a time.

   #. Click **OK**.

Related Operations
------------------

After you share images with a tenant, the tenant can accept the shared images on the **Images Shared with Me** page on the IMS console. For detailed operations, see :ref:`Accepting or Rejecting Shared Images <en-us_topic_0032042420>`.
