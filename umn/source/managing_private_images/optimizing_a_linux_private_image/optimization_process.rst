:original_name: en-us_topic_0047501133.html

.. _en-us_topic_0047501133:

Optimization Process
====================

The virtualization of ECSs is gradually changing from Xen to KVM. Therefore, private images need to support both Xen and KVM. To ensure that ECSs created from a private image can run properly, you are advised to optimize it no matter it is using Xen or KVM.

A Linux ECS can run properly only when xen-pv and VirtIO drivers have been installed on it and the disk ID in its GRUB configuration file and fstab file has been changed to UUID.

Preparations
------------

#. Use the Linux image to be optimized to an ECS, and start and log in to the ECS.

#. View the virtualization type of the ECS....

   For details, see :ref:`Viewing the Virtualization Type of a Linux ECS <en-us_topic_0037352185>`.

   The virtualization type may cause slice differences in an optimization process.

Process
-------

#. Uninstall PV drivers from the ECS.

   For details, see :ref:`Uninstalling PV Drivers from a Linux ECS <en-us_topic_0037352186>`.

   .. note::

      If the ECS is using KVM virtualization, skip this step.

#. .. _en-us_topic_0047501133__li20604522122715:

   Change the disk ID in the GRUB configuration file to UUID.

   For details, see :ref:`Changing the Disk Identifier in the GRUB Configuration File to UUID <en-us_topic_0086020895>`.

#. Change the disk ID in the fstab file to UUID.

   For details, see :ref:`Changing the Disk Identifier in the fstab File to UUID <en-us_topic_0086024961>`.

#. Install native virtualization drivers.

   -  For Xen, install native Xen and KVM drivers. For details, see :ref:`Install the Native Xen and KVM Drivers <en-us_topic_0000001347866330>`
   -  For KVM, install native KVM drivers. For details, see :ref:`Installing Native KVM Drivers <en-us_topic_0000001120952155>`.

#. .. _en-us_topic_0047501133__li18604132210271:

   Delete log files and historical records, and stop the ECS.

   For details, see :ref:`Clearing System Logs <en-us_topic_0125076462>`.

#. Create a Linux private image using the ECS.
