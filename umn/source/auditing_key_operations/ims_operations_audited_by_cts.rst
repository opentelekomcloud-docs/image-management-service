:original_name: en-us_topic_0107462581.html

.. _en-us_topic_0107462581:

IMS Operations Audited by CTS
=============================

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

   +---------------------------------------------------------+---------------+--------------+
   | Operation                                               | Resource Type | Trace Name   |
   +=========================================================+===============+==============+
   | Creating an image                                       | ims           | createImage  |
   +---------------------------------------------------------+---------------+--------------+
   | Modifying an image                                      | ims           | updateImage  |
   +---------------------------------------------------------+---------------+--------------+
   | Deleting images                                         | ims           | deleteImage  |
   +---------------------------------------------------------+---------------+--------------+
   | Replicating an image                                    | ims           | copyImage    |
   +---------------------------------------------------------+---------------+--------------+
   | Exporting an image                                      | ims           | exportImage  |
   +---------------------------------------------------------+---------------+--------------+
   | Adding image recipients                                 | ims           | addMember    |
   +---------------------------------------------------------+---------------+--------------+
   | Updating the image sharing status of an image recipient | ims           | updateMember |
   +---------------------------------------------------------+---------------+--------------+
   | Deleting image recipients                               | ims           | deleteMember |
   +---------------------------------------------------------+---------------+--------------+

.. table:: **Table 2** Relationship between IMS operations and native OpenStack APIs

   +---------------------------------------------------------+--------------+--------------+---------------+---------------------+
   | Operation                                               | Trace Name   | Service Type | Resource Type | OpenStack Component |
   +=========================================================+==============+==============+===============+=====================+
   | Creating an Image                                       | createImage  | IMS          | image         | glance              |
   +---------------------------------------------------------+--------------+--------------+---------------+---------------------+
   | Modifying/Uploading an image                            | updateImage  | IMS          | image         | glance              |
   +---------------------------------------------------------+--------------+--------------+---------------+---------------------+
   | Deleting an image                                       | deleteImage  | IMS          | image         | glance              |
   +---------------------------------------------------------+--------------+--------------+---------------+---------------------+
   | Tagging an image                                        | addTag       | IMS          | image         | glance              |
   +---------------------------------------------------------+--------------+--------------+---------------+---------------------+
   | Deleting an image tag                                   | deleteTag    | IMS          | image         | glance              |
   +---------------------------------------------------------+--------------+--------------+---------------+---------------------+
   | Adding image recipients                                 | addMember    | IMS          | image         | glance              |
   +---------------------------------------------------------+--------------+--------------+---------------+---------------------+
   | Updating the image sharing status of an image recipient | updateMember | IMS          | image         | glance              |
   +---------------------------------------------------------+--------------+--------------+---------------+---------------------+
   | Deleting image recipients                               | deleteMember | IMS          | image         | glance              |
   +---------------------------------------------------------+--------------+--------------+---------------+---------------------+
