:original_name: en-us_topic_0146474781.html

.. _en-us_topic_0146474781:

Integrating VirtIO Drivers into an ISO File
===========================================

Scenarios
---------

Windows uses IDE disks and VirtIO NICs. Before registering an image on the cloud platform, integrate VirtIO drivers into the Windows ISO file. Typically, an ISO file contains all the files that would be included on an optical disc. Some software can be installed only from a CD-ROM drive. So, a virtual CD-ROM drive is required.

This section uses AnyBurn and UltraISO as examples to describe how to integrate VirtIO drivers into an ISO file.

.. note::

   -  AnyBurn is lightweight CD/DVD/Blu-ray burning software with a free version.
   -  UltraISO is an ISO CD/DVD image file handling tool. A free trial version is limited to ISO files of 300 MB or less. You are advised to buy a standard version.

Prerequisites
-------------

You have obtained an ISO file.

.. note::

   The ISO file name can contain only letters, digits, hyphens (-), and underscores (_). If the name does not meet the requirements, change it.

AnyBurn
-------

#. Download `AnyBurn <http://www.anyburn.com/index.htm>`__ and install it on your local PC.

#. .. _en-us_topic_0146474781__li3822041155015:

   Download VirtIO drivers.

   https://fedorapeople.org/groups/virt/virtio-win/direct-downloads/stable-virtio/virtio-win.iso

   Other versions:

   https://fedorapeople.org/groups/virt/virtio-win/direct-downloads/archive-virtio/

#. Use AnyBurn to open the ISO file.

   a. Open AnyBurn and select **Edit Image File**.

      |image1|

   b. Select the ISO file and click **Next**.

      |image2|

#. Edit the ISO file to integrate VirtIO drivers into it.

   a. Decompress the **virtio-win.iso** file downloaded in :ref:`2 <en-us_topic_0146474781__li3822041155015>`.

   b. Click **Add**. Select all the decompressed files to add them to the parent node of the ISO file, and click **Next**.

   c. Select a path to save the new ISO file and specify a name for the new file. Select **ISO** as the file type. Click **Create Now**.

      After the new ISO file is generated, view VirtIO drivers in it.

      |image3|

UltraISO
--------

#. Download UltraISO and install it on your local PC.

   Download address: https://www.ultraiso.com/

#. Download VirtIO drivers.

   https://fedorapeople.org/groups/virt/virtio-win/direct-downloads/stable-virtio/virtio-win.iso

   Other versions:

   https://fedorapeople.org/groups/virt/virtio-win/direct-downloads/archive-virtio/

#. Use UltraISO to open the ISO file.

   .. caution::

      Do not extract the ISO file or open it with any tool other than UltraISO, or the boot data will be lost.

#. Drag and drop the downloaded VirtIO driver files to the parent node of the ISO file.

#. Use UltraISO to export the ISO file with VirtIO drivers to an .iso file on your local PC.

.. |image1| image:: /_static/images/en-us_image_0000001493029617.png
.. |image2| image:: /_static/images/en-us_image_0000001443321198.png
.. |image3| image:: /_static/images/en-us_image_0000001493065701.png
