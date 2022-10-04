:original_name: en-us_topic_0107462581.html

.. _en-us_topic_0107462581:

IMS Operations Recorded by CTS
==============================

Scenarios
---------

Cloud Trace Service (CTS) is a log audit service provided by the public cloud and intended for cloud security. It allows you to collect, store, and query cloud resource operation records and use these records for security analysis, compliance auditing, resource tracking, and fault locating.

You can use CTS to record IMS operations for later querying, auditing, and backtracking.

Prerequisites
-------------

You need to enable CTS before using it. If it is not enabled, IMS operations cannot be recorded. After being enabled, CTS automatically creates a tracker to record all your operations. The tracker stores only the operations of the last seven days. To store the operations for a longer time, store trace files in OBS buckets.


IMS Operations Recorded by CTS
------------------------------

.. table:: **Table 1** IMS operations that can be recorded by CTS

   +--------------------------------------------------------------------------+---------------+---------------+
   | Operation                                                                | Resource Type | Trace Name    |
   +==========================================================================+===============+===============+
   | Creating an Image                                                        | ims           | createImage   |
   +--------------------------------------------------------------------------+---------------+---------------+
   | Modifying an image                                                       | ims           | updateImage   |
   +--------------------------------------------------------------------------+---------------+---------------+
   | Deleting images in a batch                                               | ims           | deleteImage   |
   +--------------------------------------------------------------------------+---------------+---------------+
   | Replicating an image                                                     | ims           | copyImage     |
   +--------------------------------------------------------------------------+---------------+---------------+
   | Exporting an image                                                       | ims           | exportImage   |
   +--------------------------------------------------------------------------+---------------+---------------+
   | Adding a tenant that can use a shared image                              | ims           | addMember     |
   +--------------------------------------------------------------------------+---------------+---------------+
   | Modifying tenants that can use a shared image                            | ims           | updateMember  |
   +--------------------------------------------------------------------------+---------------+---------------+
   | Deleting tenants from the group where the members can use a shared image | ims           | deleteMemeber |
   +--------------------------------------------------------------------------+---------------+---------------+

.. table:: **Table 2** Relationship between IMS operations and native OpenStack APIs

   +---------------------------------------------------------------------------+--------------+--------------+---------------+---------------------+
   | Operation                                                                 | Trace Name   | Service Type | Resource Type | OpenStack Component |
   +===========================================================================+==============+==============+===============+=====================+
   | Creating an Image                                                         | createImage  | IMS          | image         | glance              |
   +---------------------------------------------------------------------------+--------------+--------------+---------------+---------------------+
   | Modifying/Uploading an image                                              | updateImage  | IMS          | image         | glance              |
   +---------------------------------------------------------------------------+--------------+--------------+---------------+---------------------+
   | Deleting an image                                                         | deleteImage  | IMS          | image         | glance              |
   +---------------------------------------------------------------------------+--------------+--------------+---------------+---------------------+
   | Tagging an image                                                          | addTag       | IMS          | image         | glance              |
   +---------------------------------------------------------------------------+--------------+--------------+---------------+---------------------+
   | Deleting an image tag                                                     | deleteTag    | IMS          | image         | glance              |
   +---------------------------------------------------------------------------+--------------+--------------+---------------+---------------------+
   | Adding a tenant that can use a shared image                               | addMember    | IMS          | image         | glance              |
   +---------------------------------------------------------------------------+--------------+--------------+---------------+---------------------+
   | Modifying information about a tenant that can use a shared image          | updateMember | IMS          | image         | glance              |
   +---------------------------------------------------------------------------+--------------+--------------+---------------+---------------------+
   | Deleting a tenant from the group where the members can use a shared image | deleteMember | IMS          | image         | glance              |
   +---------------------------------------------------------------------------+--------------+--------------+---------------+---------------------+
