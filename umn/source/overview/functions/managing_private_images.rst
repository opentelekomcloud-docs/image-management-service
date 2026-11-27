:original_name: en-us_topic_0000002471162042.html

.. _en-us_topic_0000002471162042:

Managing Private Images
=======================

Private Image Lifecycle
-----------------------

After you create a private image, you can use it to create cloud servers or EVS disks. You can also share the image with other accounts. :ref:`Figure 1 <en-us_topic_0000002471162042__fig752524722119>` shows the lifecycle of a private image.

.. _en-us_topic_0000002471162042__fig752524722119:

.. figure:: /_static/images/en-us_image_0000002504043681.png
   :alt: **Figure 1** Private image lifecycle

   **Figure 1** Private image lifecycle

Creating an ECS from a Private Image
------------------------------------

After a system disk image or full-ECS image is created, in the image list, you can locate the image and click **Apply for Server** to create new ECSs.

Related operations:

:ref:`Creating an ECS from an Image <en-us_topic_0030713200>`

Modifying an Image
------------------

You can modify the following attributes of a private image: name, description, minimum memory, maximum memory, and advanced features such as NIC multi-queue and SR-IOV driver.

Related operations:

:ref:`Modifying an Image <en-us_topic_0030713199>`

Sharing Images
--------------

You can share an image with other accounts. These accounts can use the shared image to quickly create cloud servers or EVS disks identical to your own.

Assume that user A wants to share an image with user B. The process is as follows:

To share the same image with D, A can add D as the tenant who can use the image.

When B has deployed services on the instances created from the shared image and does not need the image any longer, B can reject the shared image.

A can stop the sharing of an image with others.

Related operations:

-  :ref:`Sharing Images <en-us_topic_0032042416>`
-  :ref:`Image Sharing <en-us_topic_0171668653>`

Exporting an Image
------------------

You can export private images to your OBS bucket and download them to your local PC for backup.

You can export images of cloud servers from the cloud platform and then use the exported images to create cloud servers for use in on-premises clusters or private clouds. The following figure shows the process of exporting an image.

|image1|

The following images cannot be exported:

-  Public images
-  Full-ECS images
-  ISO images
-  Private images created from a Windows or SUSE public image

Related operations:

-  :ref:`Exporting an Image <en-us_topic_0034011241>`
-  :ref:`Image Export <en-us_topic_0030713222>`

Encrypting an Image
-------------------

You can create encrypted images to improve data security. KMS envelope encryption is used. Encrypted images can be created from external image files or encrypted cloud servers.

Related operations:

-  :ref:`Encrypting an Image <en-us_topic_0046588153>`

Replicating Images
------------------

You can replicate an image to make encrypted or unencrypted copies or enable some advanced features (such as fast server creation).

|image2|

|image3|

Related operations:

:ref:`Replicating Images <en-us_topic_0049177180>`

Tagging Images
--------------

You can tag your private images for easier management and search.

You can add tags during image creation or after the image is created on its details page. A maximum of 10 tags can be added to a private image.

|image4|

Related operations:

:ref:`Managing Tags <en-us_topic_0068002265>`

Exporting an Image List
-----------------------

You can export the public and private image lists in a given region as an XLSX file for local maintenance and query.

Related operations:

:ref:`Exporting an Image List <en-us_topic_0090099339>`

Deleting Images
---------------

You can delete images that will no longer be used. Deleting an image does not affect the cloud servers or EVS disks created from that image.

Related operations:

:ref:`Deleting Images <en-us_topic_0030713201>`

.. |image1| image:: /_static/images/en-us_image_0255101497.png
.. |image2| image:: /_static/images/en-us_image_0000002477038234.png
.. |image3| image:: /_static/images/en-us_image_0000002509118267.png
.. |image4| image:: /_static/images/en-us_image_0000002508953949.png
