:original_name: en-us_topic_0030713217.html

.. _en-us_topic_0030713217:

Can I Use Images in Formats Other Than the Specified Ones?
==========================================================

No. Currently, only the VMDK, VHD, RAW, QCOW2, VHDX, QED, VDI, QCOW, ZVHD2, and ZVHD formats are supported.

Images of the -flat.vmdk format and image file packages containing snapshot volumes or delta volumes are not supported. You can use **qemu-img** to convert an image to one of the supported formats before uploading it to the cloud platform.

.. note::

   For how to install and use **qemu-img** in Windows, visit:

   https://cloudbase.it/qemu-img-windows/
