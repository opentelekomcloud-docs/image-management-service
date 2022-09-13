:original_name: en-us_topic_0047501133.html

.. _en-us_topic_0047501133:

Optimization Process
====================

A Linux ECS can be switched from Xen to KVM if xen-pv and VirtIO drivers run on the ECS. Before changing a Xen-based ECS to a KVM-based ECS, ensure that the required drivers have been installed and the UUID has been configured for the Linux private image. In addition, optimizing the private image can improve network performance of the ECS.

#. Use the Linux image to be optimized to create an ECS, and start and log in to the ECS.

#. .. _en-us_topic_0047501133__en-us_topic_0036684058_li52904758173244:

   Uninstall the PV Driver installed on the ECS.

   For details, see :ref:`Uninstalling the PV Driver from a Linux ECS <en-us_topic_0037352186>`.

#. Change the disk ID in the GRUB configuration file to UUID.

   For details, see :ref:`Changing the Disk Identifier in the GRUB Configuration File to UUID <en-us_topic_0086020895>`.

#. Change the disk ID in the fstab file to UUID.

   For details, see :ref:`Changing the Disk Identifier in the fstab File to UUID <en-us_topic_0086024961>`.

#. Install native KVM drivers.

   For details, see :ref:`Installing Native KVM Drivers <en-us_topic_0000001120952155>`.

#. .. _en-us_topic_0047501133__en-us_topic_0036684058_li36218236173244:

   Delete log files and historical records, and stop the ECS.

   For details, see :ref:`Clearing System Logs <en-us_topic_0125076462>`.

#. Create a Linux private image using the ECS.
