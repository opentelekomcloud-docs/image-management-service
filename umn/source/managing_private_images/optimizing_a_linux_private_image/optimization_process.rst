:original_name: en-us_topic_0047501133.html

.. _en-us_topic_0047501133:

Optimization Process
====================

A Linux ECS can run properly only when native KVM (VirtIO) drivers have been installed on it and the disk ID in its GRUB configuration file and fstab file has been changed to UUID.

Preparations
------------

#. Use the Linux image to be optimized to create an ECS, and start and log in to the ECS.

#. Check whether the private image needs to be optimized.

   For details, see :ref:`Checking Whether a Private Image Needs to be Optimized <en-us_topic_0037352185>`.

.. _en-us_topic_0047501133__section862461118288:

Process
-------

#. Change the disk ID in the GRUB configuration file to UUID.

   For details, see :ref:`Changing the Disk Identifier in the GRUB Configuration File to UUID <en-us_topic_0086020895>`.

#. Change the disk ID in the fstab file to UUID.

   For details, see :ref:`Changing the Disk Identifier in the fstab File to UUID <en-us_topic_0086024961>`.

#. Install native KVM drivers.

   For details, see :ref:`Installing Native KVM Drivers <en-us_topic_0000001120952155>`.

#. Delete log files and historical records, and stop the ECS.

   For details, see :ref:`Clearing System Logs <en-us_topic_0125076462>`.

#. Create a Linux private image from the ECS.
