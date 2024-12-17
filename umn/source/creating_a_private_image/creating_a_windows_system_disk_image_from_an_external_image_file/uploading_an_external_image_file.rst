:original_name: en-us_topic_0030713183.html

.. _en-us_topic_0030713183:

Uploading an External Image File
================================

You are advised to use OBS Browser to upload external image files to OBS buckets. For details, see *Object Storage Service User Guide*.

.. note::

   -  The bucket file and the image to be registered must belong to the same region.
   -  Only unencrypted external image files or those encrypted using SSE-KMS can be uploaded to an OBS bucket.
   -  The storage class of the OBS bucket must be Standard.
   -  If you want to create a data disk image along with the system disk image, you also need to upload an image file containing data disks to the OBS bucket. You can create one system disk image and no more than three data disk images.
