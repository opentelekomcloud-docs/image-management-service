:original_name: en-us_topic_0032042423.html

.. _en-us_topic_0032042423:

Adding Tenants Who Can Use Shared Images
========================================

Scenarios
---------

In addition to the tenants you have shared images with, you can add more tenants who can use the shared images.

Prerequisites
-------------

-  You have shared private images.
-  You have obtained the project IDs of the tenants to be added.

Procedure
---------

#. Access the IMS console.

   a. Log in to the management console.

   b. Under **Compute**, click **Image Management Service**.

      The IMS console is displayed.

#. Click the **Private Images** tab.

#. Click the image name to view image details.

#. Click **Add Tenant**.

#. In the **Add Tenant** dialog box, enter the project ID of the tenant to be added and click **OK**.

   To add multiple tenants, enter their project IDs and separate them with commas. Click **OK**.

   .. note::

      -  You can share images only within the region where they reside.
      -  A project ID uniquely identifies a tenant in a specific region. If you enter a project ID that belongs to a different region from the images, a message will display indicating that the tenant cannot be found.
