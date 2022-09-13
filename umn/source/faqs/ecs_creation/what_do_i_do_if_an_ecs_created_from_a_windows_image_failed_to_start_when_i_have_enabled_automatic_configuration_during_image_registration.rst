:original_name: en-us_topic_0113403127.html

.. _en-us_topic_0113403127:

What Do I Do If an ECS Created from a Windows Image Failed to Start When I Have Enabled Automatic Configuration During Image Registration?
==========================================================================================================================================

Symptom
-------

This issue is probably caused by the failure of offline VirtIO driver injection.

Solution
--------

When you inject the VirtIO driver for a Windows ECS offline, there are some restrictions:

-  If the boot mode in the image file is UEFI, the VirtIO driver cannot be injected offline.
-  It is recommended that you disable Group Policy Object (GPO). Some policies may cause the failure of VirtIO driver injection offline.
-  It is recommended that you stop antivirus software. Otherwise, the VirtIO driver may fail to be injected offline.

To update the VirtIO driver, you must install UVP VMTools. For how to install UVP VMTools, see :ref:`Optimizing a Windows Private Image <en-us_topic_0130878748>`.
