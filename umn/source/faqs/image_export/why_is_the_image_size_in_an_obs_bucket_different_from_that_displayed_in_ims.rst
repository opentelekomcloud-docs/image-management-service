:original_name: en-us_topic_0274352601.html

.. _en-us_topic_0274352601:

Why Is the Image Size in an OBS Bucket Different from That Displayed in IMS?
============================================================================

Symptom
-------

When a private image is exported to an OBS bucket, the image size in the bucket is different from that displayed in IMS.

For example, the size of a private image is 1.04 GB on the IMS console, but in an OBS bucket, the size is 2.91 GB.

Cause Analysis
--------------

The default format of a private image is ZVHD2, but it may be stored in a different format (VMDK, VHD, QCOW2, or ZVHD) in an OBS bucket after it is exported. The format conversion may lead to size changes.
