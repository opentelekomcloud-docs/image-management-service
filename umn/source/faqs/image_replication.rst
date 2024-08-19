:original_name: en-us_topic_0183293891.html

.. _en-us_topic_0183293891:

Image Replication
=================

When Do I Need to Replicate an Image?
-------------------------------------

-  In-region replication

   This is used for conversion between encrypted and unencrypted images or for enabling advanced features (such as fast ECS creation). For details, see :ref:`Replicating Images <en-us_topic_0049177180>`.

How Long Does It Take to Replicate an Image?
--------------------------------------------

The time required for replicating an image depends on the network transmission speed and the number of tasks in the queue.

How Will I Be Billed for Replicating Images?
--------------------------------------------

-  In-region replication

   The replicas of system disk and data disk images are stored in OBS buckets for free.

   .. note::

      Full-ECS images cannot be replicated within the same region.

How Do I Replicate an Image Across Regions and Accounts?
--------------------------------------------------------

Replicate the image to the target region and share it with the target account. Then, the image will be displayed in the shared image list of the target account.
