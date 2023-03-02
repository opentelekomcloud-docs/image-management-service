:original_name: en-us_topic_0000001120952155.html

.. _en-us_topic_0000001120952155:

Installing Native KVM Drivers
=============================

Scenarios
---------

When optimizing a Linux private image, you need to install native KVM drivers on the ECS. If the drivers have been installed, skip this section.

.. caution::

   If you do not install KVM drivers, NICs of the ECS may not be detected and the ECS cannot communicate with other resources.

Prerequisites
-------------

-  The ECS needs to be optimized. For details, see :ref:`Checking Whether a Private Image Needs to be Optimized <en-us_topic_0037352185>`.
-  If the ECS uses native Linux KVM drivers, its kernel must be later than 2.6.24.
-  Disable your antivirus and intrusion detection software. You can enable the software after KVM drivers are installed.

Procedure
---------

Modify the configuration file based on the OS version.

.. table:: **Table 1** Modifying configuration files for different OSs

   +-----------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+--------------------------------------------------------------------------------------------------------------------------+
   | OS                    | Configuration                                                                                                                                                                                                              | Reference                                                                                                                |
   +=======================+============================================================================================================================================================================================================================+==========================================================================================================================+
   | CentOS/EulerOS        | Take CentOS 7.0 as an example.                                                                                                                                                                                             | :ref:`CentOS, EulerOS <en-us_topic_0000001120952155__section57411552112542>`                                             |
   |                       |                                                                                                                                                                                                                            |                                                                                                                          |
   |                       | #. In the **/etc/dracut.conf** file, add VirtIO drivers to **add_drivers**, including virtio_blk, virtio_scsi, virtio_net, virtio_pci, virtio_ring, and virtio. Separate driver names with spaces.                         |                                                                                                                          |
   |                       | #. Save and exit the **/etc/dracut.conf** file and run the **dracut -f** command to generate **initrd** again.                                                                                                             |                                                                                                                          |
   +-----------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+--------------------------------------------------------------------------------------------------------------------------+
   | Ubuntu/Debian         | #. In the **/etc/initramfs-tools/modules** file, add VirtIO drivers, including virtio_blk, virtio_scsi, virtio_net, virtio_pci, virtio_ring, and virtio. Separate driver names with spaces.                                | :ref:`Ubuntu and Debian <en-us_topic_0000001120952155__section1865536911274>`                                            |
   |                       | #. Save and exit the **/etc/initramfs-tools/modules** file and run the **update-initramfs -u** command to generate **initrd** again.                                                                                       |                                                                                                                          |
   +-----------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+--------------------------------------------------------------------------------------------------------------------------+
   | SUSE and openSUSE     | If the OS version is earlier than SUSE 12 SP1 or openSUSE 13:                                                                                                                                                              | :ref:`SUSE and openSUSE (Earlier than SUSE 12 SP1 or openSUSE 13) <en-us_topic_0000001120952155__section63790002112835>` |
   |                       |                                                                                                                                                                                                                            |                                                                                                                          |
   |                       | #. In the **/etc/sysconfig/kernel** file, add VirtIO drivers to **INITRD_MODULES=""**. VirtIO drivers include virtio_blk, virtio_scsi, virtio_net, virtio_pci, virtio_ring, and virtio. Separate driver names with spaces. |                                                                                                                          |
   |                       | #. Run the **mkinitrd** command to generate **initrd** again.                                                                                                                                                              |                                                                                                                          |
   +-----------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+--------------------------------------------------------------------------------------------------------------------------+
   |                       | If the OS version is SUSE 12 SP1:                                                                                                                                                                                          | :ref:`SUSE and openSUSE (SUSE 12 SP1) <en-us_topic_0000001120952155__section23748121182>`                                |
   |                       |                                                                                                                                                                                                                            |                                                                                                                          |
   |                       | #. In the **/etc/dracut.conf** file, add VirtIO drivers to **add_drivers**. VirtIO drivers include virtio_blk, virtio_scsi, virtio_net, virtio_pci, virtio_ring, and virtio. Separate driver names with spaces.            |                                                                                                                          |
   |                       | #. Run the **dracut -f** command to generate **initrd** again.                                                                                                                                                             |                                                                                                                          |
   +-----------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+--------------------------------------------------------------------------------------------------------------------------+
   |                       | If the OS version is later than SUSE 12 SP1 or openSUSE 13:                                                                                                                                                                | :ref:`SUSE and openSUSE (Later than SUSE 12 SP1 or openSUSE 13) <en-us_topic_0000001120952155__section17251152081820>`   |
   |                       |                                                                                                                                                                                                                            |                                                                                                                          |
   |                       | #. In the **/etc/dracut.conf** file, add VirtIO drivers to **add_drivers**, including virtio_blk, virtio_scsi, virtio_net, virtio_pci, virtio_ring, and virtio. Separate driver names with spaces.                         |                                                                                                                          |
   |                       | #. Save and exit the **/etc/dracut.conf** file and run the **dracut -f** command to generate **initrd** again.                                                                                                             |                                                                                                                          |
   +-----------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+--------------------------------------------------------------------------------------------------------------------------+

.. _en-us_topic_0000001120952155__section57411552112542:

CentOS, EulerOS
---------------

#. Run the following command to open the **/etc/dracut.conf** file:

   **vi** **/etc/dracut.conf**

#. Press **i** to enter the editing mode and add VirtIO drivers to **add_drivers** (the format depends on the OS requirements).

   .. code-block:: console

      [root@CTU10000xxxxx ~]# vi /etc/dracut.conf
      # additional kernel modules to the default
      add_drivers+="virtio_blk virtio_scsi virtio_net virtio_pci virtio_ring virtio"
      ....

#. Press **Esc**, enter **:wq**, and press **Enter**. The system saves the change and exits the **/etc/dracut.conf** file.

#. Run the following command to regenerate initrd:

   **dracut** **-f** */boot/initramfs-2.6.32-573.8.1.el6.x86_64.img*

   If the virtual file system is not the default initramfs, run the **dracut -f** *Name of the initramfs or initrd file actually used* command. The actual initramfs or initrd file name can be obtained from the **grub.cfg** file, which can be **/boot/grub/grub.cfg**, **/boot/grub2/grub.cfg**, or **/boot/grub/grub.conf** depending on the OS.

#. If the virtual file system is initramfs, run the following command to check whether native KVM drivers have been loaded:

   **lsinitrd** **/boot/initramfs-`uname** **-r`.img** **\|** **grep** **virtio**

   If the virtual file system is initrd, run the following command to check whether native KVM drivers have been loaded:

   **lsinitrd** **/boot/initrd-`uname** **-r\`** **\|** **grep** **virtio**

   Assume that the virtual file system is initramfs. The following command output will be displayed:

   .. code-block:: console

      [root@CTU10000xxxxx home]# lsinitrd /boot/initramfs-`uname -r`.img | grep virtio
      -rwxr--r--   1 root     root        23448 Jul 16 17:53 lib/modules/2.6.32-573.8.1.el6.x86_64/kernel/drivers/block/virtio_blk.ko
      -rwxr--r--   1 root     root        50704 Jul 16 17:53 lib/modules/2.6.32-573.8.1.el6.x86_64/kernel/drivers/net/virtio_net.ko
      -rwxr--r--   1 root     root        28424 Jul 16 17:53 lib/modules/2.6.32-573.8.1.el6.x86_64/kernel/drivers/scsi/virtio_scsi.ko
      drwxr-xr-x   2 root     root            0 Jul 16 17:53 lib/modules/2.6.32-573.8.1.el6.x86_64/kernel/drivers/virtio
      -rwxr--r--   1 root     root        14544 Jul 16 17:53 lib/modules/2.6.32-573.8.1.el6.x86_64/kernel/drivers/virtio/virtio.ko
      -rwxr--r--   1 root     root        21040 Jul 16 17:53 lib/modules/2.6.32-573.8.1.el6.x86_64/kernel/drivers/virtio/virtio_pci.ko
      -rwxr--r--   1 root     root        18016 Jul 16 17:53 lib/modules/2.6.32-573.8.1.el6.x86_64/kernel/drivers/virtio/virtio_ring.ko

   .. note::

      If you add built-in drivers to the initrd or initramfs file, the ECS will not be affected. This makes it easy to modify the drivers. However, you cannot check the drivers by running the **lsinitrd** command. You can run the following command to check whether the drivers are built-in ones in the kernel:

      **cat** **/boot/config-`uname -r\`** **\|** **grep** **CONFIG_VIRTIO** **\|** **grep** **y**

.. _en-us_topic_0000001120952155__section1865536911274:

Ubuntu and Debian
-----------------

#. Run the following command to open the **modules** file:

   **vi** **/etc/initramfs-tools/modules**

#. Press **i** to enter the editing mode and add VirtIO drivers to the **/etc/initramfs-tools/modules** file (the format depends on the OS requirements).

   .. code-block:: console

      [root@CTU10000xxxxx ~]#vi /etc/initramfs-tools/modules
      ...
      # Examples:
      #
      # raid1
      # sd_mOd
      virtio_blk
      virtio_scsi
      virtio_net
      virtio_pci
      virtio_ring
      virtio

#. Press **Esc**, enter **:wq**, and press **Enter**. The system saves the change and exits the **/etc/initramfs-tools/modules** file.

#. Run the following command to regenerate initrd:

   **update-initramfs** **-u**

#. Run the following command to check whether native KVM drivers have been installed:

   **lsinitramfs** **/boot/initrd.img-`uname** **-r\`** **\|grep** **virtio**

   .. code-block::

      [root@ CTU10000xxxxx home]# lsinitramfs /boot/initrd.img-`uname -r` |grep virtio
      lib/modules/3.5.0-23-generic/kernel/drivers/scsi/virtio_scsi.ko

   .. note::

      If you add built-in drivers to the initrd or initramfs file, the ECS will not be affected. This makes it easy to modify the drivers. However, you cannot check the drivers by running the **lsinitrd** command. You can run the following command to check whether the drivers are built-in ones in the kernel:

      .. code-block::

         [root@ CTU10000xxxxx home]# cat /boot/config-`uname -r` | grep CONFIG_VIRTIO | grep y
         CONFIG_VIRTIO_BLK=y
         CONFIG_VIRTIO_NET=y
         CONFIG_VIRTIO=y
         CONFIG_VIRTIO_RING=y
         CONFIG_VIRTIO_PCI=y
         CONFIG_VIRTIO_MMIO_CMDLINE_DEVICES=y

.. _en-us_topic_0000001120952155__section63790002112835:

SUSE and openSUSE (Earlier than SUSE 12 SP1 or openSUSE 13)
-----------------------------------------------------------

Modify the **/etc/sysconfig/kernel** file.

#. Run the following command to modify the **/etc/sysconfig/kernel** file:

   **vi** **etc/sysconfig/kernel**

#. Add VirtIO drivers to **INITRD_MODULES=""** (the format of drivers depends on the OS).

   .. code-block::

      SIA10000xxxxx:~ # vi /etc/sysconfig/kernel
      # (like drivers for scsi-controllers, for lvm or reiserfs)
      #
      INITRD_MODULES="ata_piix ata_generic virtio_blk virtio_scsi virtio_net virtio_pci virtio_ring virtio"

#. Run the **mkinitrd** command to generate **initrd** again.

   .. note::

      If the virtual file system is not the default initramfs or initrd, run the **dracut -f** *Name of the initramfs or initrd file actually used* command. The actual initramfs or initrd file name can be obtained from the **menu.lst** or **grub.cfg** file (**/boot/grub/menu.lst**, **/boot/grub/grub.cfg**, or **/boot/grub2/grub.cfg**).

   The following is an example initrd file of SUSE 11 SP4:

   .. code-block::

      default 0
      timeout 10
      gfxmenu (hd0,0)/boot/message
      title sles11sp4_001_[_VMX_]
      root (hd0,0)
      kernel /boot/linux.vmx vga=0x314 splash=silent console=ttyS0,115200n8 console=tty0 net.ifnames=0 NON_PERSISTENT_DEVICE_NAMES=1 showopts
      initrd /boot/initrd.vmx
      title Failsafe_sles11sp4_001_[_VMX_]
      root (hd0,0)
      kernel /boot/linux.vmx vga=0x314 splash=silent ide=nodma apm=off noresume edd=off powersaved=off nohz=off highres=off processsor.max+cstate=1 nomodeset x11failsafe console=ttyS0,115200n8 console=tty0 net.ifnames=0 NON_PERSISTENT_DEVICE_NAMES=1 showopts
      initrd /boot/initrd.vmx

   **/boot/initrd.vmx** in the **initrd** line is the **initrd** file actually used. Run the **dracut -f /boot/initrd.vmx** command. If the **initrd** file does not contain the **/boot** directory, such as **/initramfs-**\ *xxx*, run the **dracut -f /boot/initramfs-**\ *xxx* command.

#. Run the following command to check whether the VirtIO module for KVM is loaded:

   **lsinitrd** **/boot/initrd-`uname** **-r\`** **\|** **grep** **virtio**

   .. code-block::

      SIA10000xxxxx:~ # lsinitrd /boot/initrd-`uname -r` | grep virtio
      -rwxr--r-- 1 root root 19248 Jun 22 2012 lib/modules/2.6.32-279.el6.x86_64/kernel/drivers/scsi/virtio_scsi.ko
      -rwxr--r-- 1 root root 23856 Jun 22 2012 lib/modules/2.6.32-279.el6.x86_64/kernel/drivers/block/virtio_blk.ko
      drwxr-xr-x 2 root root 0 Jul 12 14:53 lib/modules/2.6.32-279.el6.x86_64/kernel/drivers/virtio
      -rwxr--r-- 1 root root 15848 Jun 22 2012 lib/modules/2.6.32-279.el6.x86_64/kernel/drivers/virtio/virtio_ring.ko
      -rwxr--r-- 1 root root 20008 Jun 22 2012 lib/modules/2.6.32-279.el6.x86_64/kernel/drivers/virtio/virtio_pci.ko
      -rwxr--r-- 1 root root 12272 Jun 22 2012 lib/modules/2.6.32-279.el6.x86_64/kernel/drivers/virtio/virtio.ko
      -rwxr--r-- 1 root root 38208 Jun 22 2012 lib/modules/2.6.32-279.el6.x86_64/kernel/drivers/net/virtio_net.ko

#. Restart the ECS.

#. Run the following command to check whether KVM drivers exist in initrd:

   **lsinitrd** **/boot/initrd-`uname** **-r\`** **\|** **grep** **virtio**

   .. code-block::

      SIA10000xxxxx:~ # lsinitrd /boot/initrd-`uname -r` | grep virtio
      -rwxr--r-- 1 root root 19248 Jun 22 2012 lib/modules/2.6.32-279.el6.x86_64/kernel/drivers/scsi/virtio_scsi.ko
      -rwxr--r-- 1 root root 23856 Jun 22 2012 lib/modules/2.6.32-279.el6.x86_64/kernel/drivers/block/virtio_blk.ko
      drwxr-xr-x 2 root root 0 Jul 12 14:53 lib/modules/2.6.32-279.el6.x86_64/kernel/drivers/virtio
      -rwxr--r-- 1 root root 15848 Jun 22 2012 lib/modules/2.6.32-279.el6.x86_64/kernel/drivers/virtio/virtio_ring.ko
      -rwxr--r-- 1 root root 20008 Jun 22 2012 lib/modules/2.6.32-279.el6.x86_64/kernel/drivers/virtio/virtio_pci.ko
      -rwxr--r-- 1 root root 12272 Jun 22 2012 lib/modules/2.6.32-279.el6.x86_64/kernel/drivers/virtio/virtio.ko
      -rwxr--r-- 1 root root 38208 Jun 22 2012 lib/modules/2.6.32-279.el6.x86_64/kernel/drivers/net/virtio_net.ko

   .. note::

      If you add built-in drivers to the initrd or initramfs file, the ECS will not be affected. This makes it easy to modify the drivers. However, you cannot check the drivers by running the **lsinitrd** command. You can run the following command to check whether the drivers are built-in ones in the kernel:

      **cat** **/boot/config-`uname** **-r\`** **\|** **grep** **CONFIG_VIRTIO** **\|** **grep** **y**

.. _en-us_topic_0000001120952155__section23748121182:

SUSE and openSUSE (SUSE 12 SP1)
-------------------------------

Modify the **/etc/dracut.conf** file.

#. Run the following command to open the **/etc/dracut.conf** file:

   **vi** **/etc/dracut.conf**

#. Press **i** to enter the editing mode and add VirtIO drivers to **add-drivers** (the format depends on the OS requirements).

   .. code-block:: console

      [root@CTU10000xxxxx ~]# vi /etc/dracut.conf
      # additional kernel modules to the default
      add_drivers+="ata_piix ata_generic virtio_blk virtio_scsi virtio_net virtio_pci virtio_ring virtio"

#. Press **Esc**, enter **:wq**, and press **Enter**. The system saves the change and exits the **/etc/dracut.conf** file.

#. Run the following command to regenerate initrd:

   **dracut -f /boot/initramfs-**\ *File name*

   If the virtual file system is not the default initramfs, run the **dracut -f** *Name of the initramfs or initrd file actually used* command. The actual initramfs or initrd file name can be obtained from the **grub.cfg** file, which can be **/boot/grub/grub.cfg**, **/boot/grub2/grub.cfg**, or **/boot/grub/grub.conf** depending on the OS.

#. If the virtual file system is initramfs, run the following command to check whether native KVM drivers have been loaded:

   **lsinitrd** **/boot/initramfs-`uname** **-r`.img** **\|** **grep** **virtio**

   If the virtual file system is initrd, run the following command to check whether native KVM drivers have been loaded:

   **lsinitrd** **/boot/initrd-`uname** **-r\`** **\|** **grep** **virtio**

.. _en-us_topic_0000001120952155__section17251152081820:

SUSE and openSUSE (Later than SUSE 12 SP1 or openSUSE 13)
---------------------------------------------------------

Modify the **/etc/dracut.conf** file.

Take SUSE Linux Enterprise Server 12 SP2 (x86_64) as an example.

#. Run the following command to open the **/etc/dracut.conf** file:

   **vi** **/etc/dracut.conf**

#. Press **i** to enter the editing mode and add VirtIO drivers to **add_drivers** (the format depends on the OS requirements).

   .. code-block:: console

      [root@CTU10000xxxxx ~]# vi /etc/dracut.conf
      # additional kernel modules to the default
      add_drivers+="ata_piix ata_generic virtio_blk virtio_scsi virtio_net virtio_pci virtio_ring virtio"

#. Press **Esc**, enter **:wq**, and press **Enter**. The system saves the change and exits the **/etc/dracut.conf** file.

#. Run the following command to regenerate initrd:

   **dracut -f /boot/initramfs-**\ *File name*

   If the virtual file system is not the default initramfs, run the **dracut -f** *Name of the initramfs or initrd file actually used* command. The actual initramfs or initrd file name can be obtained from the **grub.cfg** file, which can be **/boot/grub/grub.cfg**, **/boot/grub2/grub.cfg**, or **/boot/grub/grub.conf** depending on the OS.

#. If the virtual file system is initramfs, run the following command to check whether native KVM drivers have been loaded:

   **lsinitrd** **/boot/initramfs-`uname** **-r`.img** **\|** **grep** **virtio**

   If the virtual file system is initrd, run the following command to check whether native KVM drivers have been loaded:

   **lsinitrd** **/boot/initrd-`uname** **-r\`** **\|** **grep** **virtio**

   Assume that the virtual file system is initrd. The following command output will be displayed:

   .. code-block::

      sluo-ecs-30dc:~ # lsinitrd /boot/initrd-`uname -r` | grep virtio
      -rw-r--r-- 1 root root 29335 Oct 26 2016 lib/modules/4.4.21-69-default/kernel/drivers/block/virtio_blk.ko
      -rw-r--r-- 1 root root 57007 Oct 26 2016 lib/modules/4.4.21-69-default/kernel/drivers/net/virtio_net.ko
      -rw-r--r-- 1 root root 32415 Oct 26 2016 lib/modules/4.4.21-69-default/kernel/drivers/scsi/virtio_scsi.ko
      drwxr-xr-x 2 root root 0 Sep 28 10:21 lib/modules/4.4.21-69-default/kernel/drivers/virtio
      -rw-r--r-- 1 root root 19623 Oct 26 2016 lib/modules/4.4.21-69-default/kernel/drivers/virtio/virtio.ko
      -rw-r--r-- 1 root root 38943 Oct 26 2016 lib/modules/4.4.21-69-default/kernel/drivers/virtio/virtio_pci.ko
      -rw-r--r-- 1 root root 24431 Oct 26 2016 lib/modules/4.4.21-69-default/kernel/drivers/virtio/virtio_ring.ko

   .. note::

      If you add built-in drivers to the initrd or initramfs file, the ECS will not be affected. This makes it easy to modify the drivers. However, you cannot check the drivers by running the **lsinitrd** command. You can run the following command to check whether the drivers are built-in ones in the kernel:

      **cat** **/boot/config-`uname** **-r\`** **\|** **grep** **CONFIG_VIRTIO** **\|** **grep** **y**
