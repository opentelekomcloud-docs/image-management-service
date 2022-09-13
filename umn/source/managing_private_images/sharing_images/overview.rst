:original_name: en-us_topic_0032042417.html

.. _en-us_topic_0032042417:

Overview
========

You can share your private images with other tenants. The tenants who accept the shared images can use the images to create ECSs of the same specifications.

Constraints
-----------

-  You can share images only within the region where they reside.
-  Each image can be shared with a maximum of 128 tenants.
-  Encrypted images cannot be shared.
-  Only full-ECS images created from CBR backups can be shared. Other full-ECS images cannot be shared.

Procedure
---------

If you want to share a private image with another tenant, the procedure is as follows:

#. You obtain the project ID from the tenant.

#. You share an image with the tenant.

#. The tenant accepts the shared image.

   After accepting the image, the tenant can use it to create ECSs.

Related FAQs
------------

If you have any questions, see :ref:`Image Sharing FAQs <en-us_topic_0183293890>`.
