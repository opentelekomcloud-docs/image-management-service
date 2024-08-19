:original_name: en-us_topic_0113403127.html

.. _en-us_topic_0113403127:

What Do I Do If I Enabled Automatic Configuration During Image Registration for an ECS Created from a Windows Image and Now It Won't Start?
===========================================================================================================================================

Cause
-----

This may be caused by an issue with offline VirtIO driver injection.

Solution
--------

When you inject VirtIO drivers into the image for a Windows ECS, note that:

-  If the boot mode in the image file is UEFI, the VirtIO drivers cannot be injected offline.
-  Disable Group Policy Object (GPO) because some policies may cause offline VirtIO driver injection to fail.
-  Stop any installed antivirus software. They may cause offline VirtIO driver injection to fail.

To install VirtIO drivers, see :ref:`Optimizing a Windows Private Image <en-us_topic_0130878748>`.
