:original_name: en-us_topic_0032042423.html

.. _en-us_topic_0032042423:

Adding Image Recipients
=======================

Scenarios
---------

In addition to the tenants you have shared images with, you can add more image recipients.

Prerequisites
-------------

-  You have shared private images.
-  You have obtained the project IDs of the tenants to be added.

Procedure
---------

#. Log in to the management console.

   a. Under **Computing**, click **Image Management Service**. The IMS console is displayed.

#. Click the **Private Images** tab.

#. Click the target image name to view image details.

#. Click **Add Tenant**.

#. In the **Add Tenant** dialog box, enter the project ID of the tenant, and click **OK**.

   To add multiple tenants, enter their project IDs and separate them with commas (,). Click **OK**.

   .. note::

      -  You can share images only within the region where they reside.
      -  A project ID uniquely identifies a recipient in a specific region. The recipient's project ID must be in the same region as the image. If you enter a project ID that belongs to a different region from the image, a message will be displayed, indicating that the recipient cannot be found in the current region.
