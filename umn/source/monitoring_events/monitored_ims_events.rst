:original_name: en-us_topic_0000002328459649.html

.. _en-us_topic_0000002328459649:

Monitored IMS Events
====================

Introduction
------------

Event monitoring provides data collection, query, and alarm reporting for events. You can create alarm rules for events. When specific events occur, Cloud Eye generates alarms for you.

Namespace
---------

SYS.IMS

Monitored Events
----------------

.. table:: **Table 1** IMS events

   +--------------+-----------+-------------------+-------------+----------------+-------------------------------+---------------------+----------------------------------------------------------------------------------------+
   | Event Source | Namespace | Event Name        | Event ID    | Event Severity | Description                   | Handling Suggestion | Impact                                                                                 |
   +==============+===========+===================+=============+================+===============================+=====================+========================================================================================+
   | IMS          | SYS.IMS   | Creating an image | createImage | Minor          | Creating a private image      | None                | This image can be used to create cloud servers.                                        |
   +--------------+-----------+-------------------+-------------+----------------+-------------------------------+---------------------+----------------------------------------------------------------------------------------+
   |              |           | Updating an image | updateImage | Minor          | Updating metadata of an image | None                | Cloud servers may fail to be created from this image if key image metadata is changed. |
   +--------------+-----------+-------------------+-------------+----------------+-------------------------------+---------------------+----------------------------------------------------------------------------------------+
   |              |           | Deleting an image | deleteImage | Minor          | Deleting a private image      | None                | This image can no longer be used to create cloud servers.                              |
   +--------------+-----------+-------------------+-------------+----------------+-------------------------------+---------------------+----------------------------------------------------------------------------------------+
