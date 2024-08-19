:original_name: en-us_topic_0146480990.html

.. _en-us_topic_0146480990:

Configuring the ECS and Creating a Linux System Disk Image
==========================================================

Scenarios
---------

After installing an OS for the temporary ECS, configure the ECS and install KVM drivers to ensure that ECSs created from this temporary ECS can work properly.

This section describes how to configure a Linux ECS, install drivers, and create a Linux system disk image.

Procedure
---------

#. .. _en-us_topic_0146480990__li249171184717:

   Configure the ECS.

   a. Configure the network.

      -  Run the **ifconfig** command to check whether the private IP address of the ECS is the same as that displayed on the console. If they are inconsistent, delete files from the network rule directory as instructed in :ref:`Deleting Files from the Network Rule Directory <en-us_topic_0069904570>`.
      -  Check whether NICs are set to DHCP. If the ECS is configured with a static IP address, change its IP address assignment mode to DHCP as instructed in :ref:`Setting the NIC to DHCP <en-us_topic_0030713176>`.
      -  Run the **service sshd status** command to check whether SSH is enabled. If it is disabled, run the **service sshd start** command to enable it. Ensure that your ECS firewall, for example, Linux iptables, allows access to SSH.

   b. Install drivers.

      To ensure that the network performance and basic functions of the ECSs created from the private image are normal, install KVM drivers on the ECS used to create the image.

      .. note::

         Disable your antivirus and intrusion detection software. You can enable them after the installation of KVM drivers.

      -  Install native KVM drivers. For details, see :ref:`Installing Native KVM Drivers <en-us_topic_0000001120952155>`.
      -  After the drivers are installed, you need to clear log files and historical records. For details, see :ref:`Clearing System Logs <en-us_topic_0125076462>`.

   c. Configure a file system.

      -  Change the disk identifier in the GRUB configuration file to UUID. For details, see :ref:`Changing the Disk Identifier in the GRUB Configuration File to UUID <en-us_topic_0086020895>`.
      -  Change the disk identifier in the fstab file to UUID. For details, see :ref:`Changing the Disk Identifier in the fstab File to UUID <en-us_topic_0086024961>`.
      -  Clear the automatic mount configuration of non-system disks in the **/etc/fstab** file. For details, see :ref:`Detaching Data Disks from an ECS <en-us_topic_0030713179>`.

   d. (Optional) Configure value-added functions.

      -  Install and configure Cloud-Init. For details, see :ref:`Installing Cloud-Init <en-us_topic_0030730603>` and :ref:`Configuring Cloud-Init <en-us_topic_0122876047>`.
      -  Enable NIC multi-queue. For details, see :ref:`How Do I Enable NIC Multi-Queue for an Image? <en-us_topic_0085214115>`

#. Create a Linux system disk image.

   For details, see :ref:`Creating a System Disk Image from a Linux ECS <en-us_topic_0030713180>`.

Follow-up Procedure
-------------------

After the system disk image is created, delete the temporary ECS in a timely manner to prevent it from occupying compute resources.
