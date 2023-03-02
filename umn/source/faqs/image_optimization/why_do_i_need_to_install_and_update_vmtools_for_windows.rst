:original_name: en-us_topic_0165718046.html

.. _en-us_topic_0165718046:

Why Do I Need to Install and Update VMTools for Windows?
========================================================

Why Do I Need to Install VMTools?
---------------------------------

VMTools is a VirtIO driver (para-virtualization driver) that provides high-performance disks and NICs for ECSs.

-  A standard Windows OS does not have the VirtIO driver.
-  Public images have VMTools by default.
-  You need to install VMTools for private images. For details, see :ref:`Installing UVP VMTools <en-us_topic_0037352061>`.

Why Do I Need to Update VMTools?
--------------------------------

The cloud platform periodically synchronizes issue-fixed versions from the VirtIO community and releases updated versions every month. This ensures that known issues identified in the community or R&D tests can be avoided on the latest driver.

When Do I Need to Update VMTools?
---------------------------------

-  If a major error is fixed, you are advised to update VMTools immediately. (Major errors have not occurred by now.) If other issues are fixed, choose whether to update VMTools based on your needs.
-  The cloud platform updates the VMTools stored in an OBS bucket on a regular basis to ensure that you can download the latest version of VMTools for private images.
-  The cloud platform updates public images on a regular basis to ensure that these images have the latest version of VMTools.
-  The document is updated on a regular basis in accordance with VMTools in an OBS bucket to ensure that the download link of VMTools provided in the document is the latest.

What Do I Need to Do After VMTools Is Updated?
----------------------------------------------

-  Update Windows private images or drivers in running Windows ECSs.
-  If you have any technical issue or question, contact the customer service.
