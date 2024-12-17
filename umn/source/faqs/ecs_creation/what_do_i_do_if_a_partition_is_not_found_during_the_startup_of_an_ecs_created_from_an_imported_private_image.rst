:original_name: en-us_topic_0034220644.html

.. _en-us_topic_0034220644:

What Do I Do If a Partition Is Not Found During the Startup of an ECS Created from an Imported Private Image?
=============================================================================================================

Cause
-----

Disk partition IDs are changed after the cross-platform image import. As a result, no partition can be found at startup. In this case, you need to change disk partition IDs in the image to UUID.

Solution
--------

openSUSE 13.2 is used as an example.

#. .. _en-us_topic_0034220644__li4101085015191:

   Check disk partition IDs.

   **ls -l /dev/disk/by-id/**

   An output similar to the following should be seen:

   .. code-block::

      total 0
      lrwxrwxrwx 1 root root 10 Jul 22 01:35 ata-QEMU_HARDDISK_QM00001 -> ../../xvda
      lrwxrwxrwx 1 root root 11 Jul 22 01:35 ata-QEMU_HARDDISK_QM00001-part1 -> ../../xvda1
      lrwxrwxrwx 1 root root 12 Jul 22 01:35 ata-QEMU_HARDDISK_QM00001-part10 -> ../../xvda10
      lrwxrwxrwx 1 root root 11 Jul 22 01:35 ata-QEMU_HARDDISK_QM00001-part2 -> ../../xvda2
      lrwxrwxrwx 1 root root 11 Jul 22 01:35 ata-QEMU_HARDDISK_QM00001-part5 -> ../../xvda5
      lrwxrwxrwx 1 root root 11 Jul 22 01:35 ata-QEMU_HARDDISK_QM00001-part6 -> ../../xvda6
      lrwxrwxrwx 1 root root 11 Jul 22 01:35 ata-QEMU_HARDDISK_QM00001-part7 -> ../../xvda7
      lrwxrwxrwx 1 root root 11 Jul 22 01:35 ata-QEMU_HARDDISK_QM00001-part8 -> ../../xvda8
      lrwxrwxrwx 1 root root 11 Jul 22 01:35 ata-QEMU_HARDDISK_QM00001-part9 -> ../../xvda9
      lrwxrwxrwx 1 root root 10 Jul 22 01:35 ata-QEMU_HARDDISK_QM00005 -> ../../xvde
      lrwxrwxrwx 1 root root 10 Jul 22 01:35 scsi-SATA_QEMU_HARDDISK_QM00001 -> ../../xvda
      lrwxrwxrwx 1 root root 11 Jul 22 01:35 scsi-SATA_QEMU_HARDDISK_QM00001-part1 -> ../../xvda1
      lrwxrwxrwx 1 root root 12 Jul 22 01:35 scsi-SATA_QEMU_HARDDISK_QM00001-part10 -> ../../xvda10
      lrwxrwxrwx 1 root root 11 Jul 22 01:35 scsi-SATA_QEMU_HARDDISK_QM00001-part2 -> ../../xvda2
      lrwxrwxrwx 1 root root 11 Jul 22 01:35 scsi-SATA_QEMU_HARDDISK_QM00001-part5 -> ../../xvda5
      lrwxrwxrwx 1 root root 11 Jul 22 01:35 scsi-SATA_QEMU_HARDDISK_QM00001-part6 -> ../../xvda6
      lrwxrwxrwx 1 root root 11 Jul 22 01:35 scsi-SATA_QEMU_HARDDISK_QM00001-part7 -> ../../xvda7
      lrwxrwxrwx 1 root root 11 Jul 22 01:35 scsi-SATA_QEMU_HARDDISK_QM00001-part8 -> ../../xvda8
      lrwxrwxrwx 1 root root 11 Jul 22 01:35 scsi-SATA_QEMU_HARDDISK_QM00001-part9 -> ../../xvda9
      lrwxrwxrwx 1 root root 10 Jul 22 01:35 scsi-SATA_QEMU_HARDDISK_QM00005 -> ../../xvde

   **ata-QEMU_HARDDISK\_**\ *xxx* and **scsi-SATA_QEMU_HARDDISK\_**\ *xxx* indicate that the ECS disks are simulated using Quick EMUlator (QEMU). The content on the left of **->** are disk partition IDs, and that on the right of **->** are partition names.

#. .. _en-us_topic_0034220644__li37981366152220:

   Check disk partition UUIDs.

   **ls -l /dev/disk/by-uuid/**

   An output similar to the following should be seen:

   .. code-block::

      total 0
      lrwxrwxrwx 1 root root 11 Jul 22 01:35 45ecd7a0-29da-4402-a017-4564a62308b8 -> ../../xvda5
      lrwxrwxrwx 1 root root 11 Jul 22 01:35 55386c6a-9e32-41d4-af7a-e79596221f51 -> ../../xvda9
      lrwxrwxrwx 1 root root 11 Jul 22 01:35 55f36660-9bac-478c-a701-7ecc5347f789 -> ../../xvda8
      lrwxrwxrwx 1 root root 11 Jul 22 01:35 780f36bc-0ada-4c98-9a8d-44570d65333d -> ../../xvda1
      lrwxrwxrwx 1 root root 11 Jul 22 01:35 b3b7c47f-6a91-45ef-80d6-275b1cc16e19 -> ../../xvda6
      lrwxrwxrwx 1 root root 11 Jul 22 01:35 ea63b55d-3b6e-4dcd-8986-956b72bac3e9 -> ../../xvda7
      lrwxrwxrwx 1 root root 12 Jul 22 01:35 eb3cc645-925e-4bc5-bedf-c2a6f3b65809 -> ../../xvda10

   The content on the left of **->** are disk partition UUIDs, and that on the right of **->** are partition names. Based on the outputs in :ref:`1 <en-us_topic_0034220644__li4101085015191>` and this step, you can obtain the mappings between the partition names, IDs, and UUIDs.

#. Open the **/etc/fstab** file to check partition names.

   **vi /etc/fstab**

   An example command output is as follows:

   .. code-block::

      /dev/disk/by-id/scsi-SATA_QEMU_HARDDISK_QM00001-part5 / ext3 defaults,errors=panic 1 1
      /dev/disk/by-id/scsi-SATA_QEMU_HARDDISK_QM00001-part1 /boot ext3 defaults,errors=panic 1 2
      /dev/disk/by-id/scsi-SATA_QEMU_HARDDISK_QM00001-part6 /home ext3 nosuid,errors=panic 1 2
      /dev/disk/by-id/scsi-SATA_QEMU_HARDDISK_QM00001-part10 /opt ext3 defaults,errors=panic 1 2
      /dev/disk/by-id/scsi-SATA_QEMU_HARDDISK_QM00001-part7 /tmp ext3 nodev,nosuid,errors=panic 1 2
      /dev/disk/by-id/scsi-SATA_QEMU_HARDDISK_QM00001-part9 /usr ext3 defaults,errors=panic 1 2
      /dev/disk/by-id/scsi-SATA_QEMU_HARDDISK_QM00001-part8 /var ext3 nodev,nosuid,errors=panic 1 2
      sysfs /sys sysfs noauto 0 0
      proc /proc proc defaults 0 0
      usbfs /proc/bus/usb usbfs noauto 0 0
      devpts /dev/pts devpts mode=0620,gid=5 0 0
      /dev/cdrom /media/ udf,iso9660 noexec,noauto,nouser,nodev,nosuid 1 2
      tmpfs /dev/shm tmpfs noexec,nodev,nosuid 0 0

   The values in the first column are the disk partition IDs.

#. Press **i** to enter editing mode. Change each disk partition ID to a UUID based on the outputs in :ref:`1 <en-us_topic_0034220644__li4101085015191>` and :ref:`2 <en-us_topic_0034220644__li37981366152220>`.

   The modified content is as follows.

   .. code-block::

      UUID=45ecd7a0-29da-4402-a017-4564a62308b8 / ext3 defaults,errors=panic 1 1
      UUID=780f36bc-0ada-4c98-9a8d-44570d65333d /boot ext3 defaults,errors=panic 1 2
      UUID=b3b7c47f-6a91-45ef-80d6-275b1cc16e19 /home ext3 nosuid,errors=panic 1 2
      UUID=eb3cc645-925e-4bc5-bedf-c2a6f3b65809 /opt ext3 defaults,errors=panic 1 2
      UUID=ea63b55d-3b6e-4dcd-8986-956b72bac3e9 /tmp ext3 nodev,nosuid,errors=panic 1 2
      UUID=55386c6a-9e32-41d4-af7a-e79596221f51 /usr ext3 defaults,errors=panic 1 2
      UUID=55f36660-9bac-478c-a701-7ecc5347f789 /var ext3 nodev,nosuid,errors=panic 1 2
      sysfs /sys sysfs noauto 0 0
      proc /proc proc defaults 0 0
      usbfs /proc/bus/usb usbfs noauto 0 0
      devpts /dev/pts devpts mode=0620,gid=5 0 0
      /dev/cdrom /media/ udf,iso9660 noexec,noauto,nouser,nodev,nosuid 1 2
      tmpfs /dev/shm tmpfs noexec,nodev,nosuid 0 0

   .. note::

      Ensure that the UUIDs are correct, or the ECS will be unable to start up normally.

#. Press **Esc**, enter **:wq**, and press **Enter**. The system saves the configuration and exits the editor.

#. .. _en-us_topic_0034220644__li2638602155053:

   Check the partition names in the system boot configuration file.

   The system boot configuration file varies depending on the OS. Confirm the boot configuration file of the current OS.

   -  GRUB file

      -  /boot/grub/grub.conf
      -  /boot/grub/menu.lst
      -  /boot/grub/grub.cfg
      -  /boot/grub2/grub.cfg

   -  Syslinux configuration file

      -  /extlinux.conf
      -  /boot/syslinux/extlinux.conf
      -  /boot/extlinux/extlinux.conf
      -  /boot/syslinux/syslinux.cfg
      -  /syslinux/syslinux.cfg
      -  /syslinux.cfg

   The boot file in this example is **/boot/grub/menu.lst**. Run the following command to check it:

   **vi /boot/grub/menu.lst**

   .. code-block::

      default 0
      timeout 3
      title xxx Server OS - xxxxxx
      kernel /boot/vmlinuz-3.0.101-0.47.52-default root=/dev/disk/by-id/scsi-SATA_QEMU_HARDDISK_QM00001-part5 resume= memmap=0x2000000$0x3E000000 nmi_watchdog=2 crashkernel=512M-:256M console=ttyS0,115200 console=tty0 xen_emul_unplug=all
      initrd /boot/initrd-3.0.101-0.47.52-default

#. Press **i** to enter editing mode and change the partition names in the system boot configuration file.

   Change each disk partition name in the **/boot/grub/menu.lst** file in :ref:`6 <en-us_topic_0034220644__li2638602155053>` to **UUID=**\ *UUID of the disk partition* based on the query results in :ref:`1 <en-us_topic_0034220644__li4101085015191>` and :ref:`2 <en-us_topic_0034220644__li37981366152220>`.

   .. code-block::

      default 0
      timeout 3
      title xxx Server OS - xxxxxx
      kernel /boot/vmlinuz-3.0.101-0.47.52-default root=UUID=45ecd7a0-29da-4402-a017-4564a62308b8 resume= memmap=0x2000000$0x3E000000 nmi_watchdog=2 crashkernel=512M-:256M console=ttyS0,115200 console=tty0 xen_emul_unplug=all
      initrd /boot/initrd-3.0.101-0.47.52-default

#. Press **Esc**, enter **:wq**, and press **Enter**. The system saves the configuration and exits the vi editor.
