:original_name: en-us_topic_0040740508.html

.. _en-us_topic_0040740508:

How Do I Configure an ECS, a BMS, or an Image File Before I Use It to Create an Image?
======================================================================================

ECS or Image File Configurations
--------------------------------

.. table:: **Table 1** ECS configurations

   +-----------------------+-------------------------------------------------------+---------------------------------------------------------------------------------+
   | OS                    | Configuration                                         | Reference                                                                       |
   +=======================+=======================================================+=================================================================================+
   | Windows               | -  Configure DHCP.                                    | :ref:`Creating a System Disk Image from a Windows ECS <en-us_topic_0030713149>` |
   |                       | -  Enable remote desktop connection.                  |                                                                                 |
   |                       | -  (Optional) Install special Windows drivers.        |                                                                                 |
   |                       | -  (Optional) Install Cloudbase-Init.                 |                                                                                 |
   |                       | -  Install Guest OS drivers (VirtIO drivers).         |                                                                                 |
   |                       | -  Run Sysprep.                                       |                                                                                 |
   +-----------------------+-------------------------------------------------------+---------------------------------------------------------------------------------+
   | Linux                 | -  Configure DHCP.                                    | :ref:`Creating a System Disk Image from a Linux ECS <en-us_topic_0030713180>`   |
   |                       | -  (Optional) Install special Linux drivers.          |                                                                                 |
   |                       | -  (Optional) Install Cloud-Init.                     |                                                                                 |
   |                       | -  Delete files from the network rule directory.      |                                                                                 |
   |                       | -  Change disk identifiers in the GRUB file to UUID.  |                                                                                 |
   |                       | -  Change disk identifiers in the fstab file to UUID. |                                                                                 |
   |                       | -  Install native KVM drivers.                        |                                                                                 |
   |                       | -  Detach data disks from the ECS.                    |                                                                                 |
   |                       | -  Configure console logging.                         |                                                                                 |
   +-----------------------+-------------------------------------------------------+---------------------------------------------------------------------------------+

.. table:: **Table 2** Image file configurations

   +-----------------------+-----------------------------------------------------------------------------------------------+---------------------------------------------------------+
   | OS                    | Configuration                                                                                 | Reference                                               |
   +=======================+===============================================================================================+=========================================================+
   | Windows               | -  Configure DHCP.                                                                            | :ref:`Preparing an Image File <en-us_topic_0030713189>` |
   |                       | -  Enable remote desktop connection.                                                          |                                                         |
   |                       | -  Install Guest OS drivers (VirtIO drivers).                                                 |                                                         |
   |                       | -  (Optional) Install Cloudbase-Init.                                                         |                                                         |
   |                       | -  (Optional) Enable NIC multi-queue.                                                         |                                                         |
   +-----------------------+-----------------------------------------------------------------------------------------------+---------------------------------------------------------+
   | Linux                 | -  Delete files from the network rule directory.                                              | :ref:`Preparing an Image File <en-us_topic_0030713198>` |
   |                       | -  Configure DHCP.                                                                            |                                                         |
   |                       | -  Install native KVM drivers.                                                                |                                                         |
   |                       | -  Change disk identifiers in the GRUB file to UUID.                                          |                                                         |
   |                       | -  Change disk identifiers in the fstab file to UUID.                                         |                                                         |
   |                       | -  Delete the automatic mount configuration of non-system disks from the **/etc/fstab** file. |                                                         |
   |                       | -  (Optional) Install Cloud-Init.                                                             |                                                         |
   |                       | -  (Optional) Enable NIC multi-queue.                                                         |                                                         |
   +-----------------------+-----------------------------------------------------------------------------------------------+---------------------------------------------------------+

.. note::

   -  When registering an external image file as a private image, you are advised to perform the preceding operations on the VM where the external image file is located.
   -  When registering a Windows external image file as a private image, if the Guest OS drivers are installed, the cloud platform will check the image file after you select **Enable automatic configuration**. If the GuestOS drivers are not installed, the cloud platform will try to install them.

BMS or Image File Configurations
--------------------------------

.. table:: **Table 3** BMS configurations

   +-----------------------+------------------------------------------------------------+-------------------------------------------------------------------------+
   | OS                    | Configuration                                              | Reference                                                               |
   +=======================+============================================================+=========================================================================+
   | Windows               | -  Install the **bms-network-config** package.             | "Creating a Private Image from a BMS" in *Bare Metal Server User Guide* |
   |                       | -  Install Cloudbase-Init.                                 |                                                                         |
   |                       | -  Delete residual files from the OS.                      |                                                                         |
   +-----------------------+------------------------------------------------------------+-------------------------------------------------------------------------+
   | Linux                 | -  Install software in the **bms-network-config** package. | "Creating a Private Image from a BMS" in *Bare Metal Server User Guide* |
   |                       | -  Install Cloud-Init.                                     |                                                                         |
   |                       | -  Delete residual files from the OS.                      |                                                                         |
   +-----------------------+------------------------------------------------------------+-------------------------------------------------------------------------+

.. table:: **Table 4** Image file configurations

   +-----------------------+------------------------------------------------------------+------------------------------------------+
   | OS                    | Configuration                                              | Reference                                |
   +=======================+============================================================+==========================================+
   | Windows               | -  Install drivers for x86 V5 BMSs.                        | *Bare Metal Server Image Creation Guide* |
   |                       | -  Install Cloudbase-Init.                                 |                                          |
   |                       | -  Install software in the **bms-network-config** package. |                                          |
   |                       | -  (Optional) Install the SDI iNIC driver.                 |                                          |
   |                       | -  Set the Windows time zone.                              |                                          |
   |                       | -  Set the virtual memory.                                 |                                          |
   |                       | -  (Optional) Configure automatic Windows update.          |                                          |
   |                       | -  Configure SID.                                          |                                          |
   +-----------------------+------------------------------------------------------------+------------------------------------------+
   | Linux                 | -  Install and configure Cloud-Init.                       | *Bare Metal Server Image Creation Guide* |
   |                       | -  Modify the hardware device driver that boots the OS.    |                                          |
   |                       | -  Install software in the **bms-network-config** package. |                                          |
   |                       | -  (Optional) Install the SDI iNIC driver.                 |                                          |
   |                       | -  (Optional) Install the Hi1822 NIC driver.               |                                          |
   |                       | -  (Optional) Install the IB driver.                       |                                          |
   |                       | -  (Optional) Install drivers for x86 V5 BMSs.             |                                          |
   |                       | -  (Optional) Install the UltraPath software.              |                                          |
   |                       | -  Perform security configuration.                         |                                          |
   |                       | -  Configure remote login to the BMS.                      |                                          |
   |                       | -  Configure automatic root partition expansion.           |                                          |
   +-----------------------+------------------------------------------------------------+------------------------------------------+
