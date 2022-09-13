:original_name: en-us_topic_0076880304.html

.. _en-us_topic_0076880304:

How Do I Configure a Linux Private Image to Make It Automatically Expand Its Root Partition?
============================================================================================

Constraints
-----------

-  An image whose root partition file system is xfs cannot automatically expand its partitions.
-  An image that has the LVM partition cannot automatically expand its partitions.
-  Images whose file system is ext3 or ext4 are recommended.

   .. note::

      After OS partitions of old versions are expanded, the OS must be restarted to update the file system.

Installation of growpart on Different OSs
-----------------------------------------

To enable private images to automatically expand the root partition, install growpart.

.. table:: **Table 1** growpart installation packages for different OSs

   ============= =====================================================
   OS            Tool Package
   ============= =====================================================
   Debian/Ubuntu cloud-init, cloud-utils, and cloud-initramfs-growroot
   Fedora/CentOS cloud-init, cloud-utils, and cloud-utils-growpart
   SUSE/openSUSE cloud-init and growpart
   ============= =====================================================

.. note::

   For Debian 9, use method 1 to install growpart. If the installation fails, use method 2 to install growpart.

   **Method 1**:

   Run the following command to install growpart:

   **apt-get install -y -f cloud-init cloud-utils cloud-initramfs-growroot**

   **Method 2**:

   If method 1 fails, it may be because the installation source of Debian 9.0.0 is faulty. You need to download dependent packages **cloud-utils** and **cloud-initramfs-growroot** and install them.

   #. Run the following command to download the dependent packages:

      **wget** *Package download path*

      You can obtain the dependent packages from the following paths:

      http://ftp.br.debian.org/debian/pool/main/c/cloud-utils/cloud-utils_0.29-1_all.deb

      http://ftp.br.debian.org/debian/pool/main/c/cloud-initramfs-tools/cloud-initramfs-growroot_0.18.debian5_all.deb

   #. Run the following command to rectify the dependent packages:

      **apt --fix-broken install**

   #. Run the following command to install the dependent packages:

      **dpkg -i** *cloud-utils* *package path* *cloud-initramfs-growroot* *package path*

      An example command is **dpkg -i /root/cloud-utils_0.29-1_all.deb /root/cloud-initramfs-growroot_0.18.debian5_all.deb**.

   For other Debian versions, run the following command to install dependent packages:

   **apt-get update;apt-get install cloud-utils cloud-initramfs-growroot**

Procedure
---------

Take the following as two examples of image disk partitioning:

If the root partition is the last partition, see :ref:`Root partition at the last <en-us_topic_0076880304__li38782413161354>`.

If the root partition is not the last partition, see :ref:`Root partition not at the last <en-us_topic_0076880304__li17770807112053>`.

.. note::

   If the **parted** command fails, ensure that the **parted** tool has been installed in the OS. Perform the following operations to install the tool:

   -  For CentOS, run the following command:

      **yum install parted**

   -  For Debian, run the following command:

      **apt-get install parted**

-  .. _en-us_topic_0076880304__li38782413161354:

   Root partition at the last (**/dev/xvda1: swap** and **/dev/xvda2: root**)

   For example, if the system disk size of CentOS 6.5 64bit is 40 GB, perform the following operations to configure a Linux private image so that it can automatically expand its root partition:

   #. Run the following command to query the partitions of **/dev/xvda**:

      **parted -l /dev/xvda**

      As shown in the command output, the root partition is the second partition and is 38.7 GB.

      .. code-block::

         Model: Xen Virtual Block Device (xvd)
         Disk /dev/xvda: 42.7GB
         Sector size (logical/physical): 512B/512B
         Partition Table: msdos

         Number Start End Size Type File system Flags
         1 1049kB 4296MB 4295MB primary linux-swap(v1)
         2 4296MB 42.9GB 38.7GB primary ext4 boot

   #. Install growpart to ensure that the image can automatically expand its root partition.

      Run the following command to install growpart:

      **yum install cloud-\***

      .. note::

         growpart may be contained in the **cloud-utils-growpart/cloud-utils/cloud-initramfs-tools/cloud-init** package. You can run the preceding command directly and then run the **growpart** command to check whether growpart has been installed successfully.

   #. Run the following command to obtain the file system type and UUID:

      **blkid**

      The command output is as follows:

      .. code-block::

         /dev/xvda1: UUID="25ec3bdb-ba24-4561-bcdc-802edf42b85f" TYPE="swap"
         /dev/xvda2: UUID="1a1ce4de-e56a-4e1f-864d-31b7d9dfb547" TYPE="ext4"

   #. Stop the ECS and use it to create a private image.

      .. code-block:: console

         [root@sluo-ecs-e6dc-resizefs ~]# poweroff
         Connection closed by foreign host.
         Disconnected from remote host at 11:08:54.
         Type `help´ to learn how to use Xshell prompt.

   #. Use the created image to create an ECS with a 50 GB system disk. Log in to the ECS and run the following command to query the expanded partitions:

      **parted -l /dev/xvda**

      As shown in the command output, the root partition has been expanded automatically.

      .. code-block::

         Model: Xen Virtual Block Device (xvd)
         Disk /dev/xvda: 53.7GB
         Sector size (logical/physical): 512B/512B
         Partition Table: msdos

         NumberStartEndSizeTypeFile systemFlags
         1 1049kB 4296MB 4295MB primary linux-swap(v1)
         2 4296MB 53.7GB 49.4GB primary ext4 boot

   #. Run the following command to check whether disks are attached to the ECS successfully:

      **df -Th**

      The command output is as follows:

      .. code-block::

         Filesystem     Type      Size    Used   Avail Use%  Mounted on
         /dev/xvda2     ext4      49.4G    2.6G  46.8G  4%   /dev/shm
         tmpfs          tmpfs     4295M    0     4295M  0%   /

-  .. _en-us_topic_0076880304__li17770807112053:

   Root partition not at the last (for example, **/dev/xvda1: root** and **/dev/xvda2: swap**)

   For example, if the system disk size of CentOS 7.3 64bit is 40 GB, perform the following operations to configure a Linux private image so that it can automatically expand its root partition:

   #. Run the following command to query the partitions of **/dev/xvda**:

      **parted -l /dev/xvda**

      As shown in the command output, the root partition is the first partition and is 40.9 GB. The swap partition is the second partition.

      .. code-block::

         Model: Xen Virtual Block Device (xvd)
         Disk /dev/xvda: 42.9GB
         Sector size (logical/physical): 512B/512B
         Partition Table: msdos
         Disk Flags:

         Number  Start   End     Size    Type     File system     Flags
         1      1049kB  41.0GB  40.9GB  primary  ext4            boot
         2      41.0GB  42.9GB  2000MB  primary  linux-swap(v1)

   #. Run the following command to check the configuration of the **/etc/fstab** file:

      **tail -n 3 /etc/fstab**

      As shown in the command output, UUIDs of the two partitions are displayed.

      .. code-block::

         #
         UUID=7c4fce5d-f8f7-4ed6-8463-f2bd22d0ddea /                       ext4    defaults        1 1
         UUID=5de3cf2c-30c6-4fb2-9e63-830439d4e674 swap                    swap    defaults        0 0

   #. Run the following command to open the **/etc/fstab** file and press **i** to enter editing mode:

      **vi /etc/fstab**

   #. Delete the swap partition configuration, press **Esc** to exit editing mode, and run the following command to save the configuration:

      **wq!**

   #. Run the following command to check whether the configuration has been modified:

      **tail -n 3 /etc/fstab**

      As shown in the command output, only the UUID of the root partition is displayed.

      .. code-block::

         UUID=7c4fce5d-f8f7-4ed6-8463-f2bd22d0ddea /                       ext4    defaults        1 1

   #. Run the following command to stop the swap device:

      **swapoff -a**

   #. Run the following command to query the partitions of **/dev/xvda**:

      **parted /dev/xvda**

      The command output is as follows:

      .. code-block:: console

         [root@test-0912 bin]# parted /dev/xvda
         GNU Parted 3.1
         Using /dev/xvda
         Welcome to GNU Parted! Type 'help' to view a list of commands.
         (parted)

   #. Run the following command to query the disk partitions:

      **p**

      The command output is as follows:

      .. code-block::

         (parted) p
         Model: Xen Virtual Block Device (xvd)
         Disk /dev/xvda: 42.9GB
         Sector size (logical/physical): 512B/512B
         Partition Table: msdos
         Disk Flags:

         Number  Start   End     Size    Type     File system     Flags
          1      1049kB  4296MB  4295MB  primary  linux-swap(v1)
          2      4296MB  42.9GB  38.7GB  primary  xfs             boot
         (parted)

   #. Run the following command to delete the second partition:

      **rm 2**

      The command output is as follows:

      .. code-block::

         (parted) rm 2
         (parted)

   #. Run the following command to query the disk partitions:

      **p**

      The command output is as follows:

      .. code-block::

         (parted) p
         Model: Xen Virtual Block Device (xvd)
         Disk /dev/xvda: 42.9GB
         Sector size (logical/physical): 512B/512B
         Partition Table: msdos
         Disk Flags:

         Number  Start   End     Size    Type     File system  Flags
         1      1049kB  41.0GB  40.9GB  primary  ext4         boot

   #. Enter **quit**.

   #. Run the following command to query the partitions of **/dev/xvda**:

      **parted -l /dev/xvda**

      As shown in the command output, the swap partition is deleted.

      .. code-block::

         Model: Xen Virtual Block Device (xvd)
         Disk /dev/xvda: 42.9GB
         Sector size (logical/physical): 512B/512B
         Partition Table: msdos
         Disk Flags:

         Number  Start   End     Size    Type     File system  Flags
         1      1049kB  41.0GB  40.9GB  primary  ext4         boot

   #. Install growpart to ensure that the image can automatically expand its root partition.

      Run the following command to install growpart:

      **yum install cloud-\***

      .. note::

         growpart may be contained in the **cloud-utils-growpart/cloud-utils/cloud-initramfs-tools/cloud-init** package. You can run the preceding command directly and then run the **growpart** command to check whether growpart has been installed successfully.

   #. Run the following command to expand the swap partition of the **/dev/xvda** disk to the first partition to which the root partition belongs:

      **growpart /dev/xvda 1**

      The command output is as follows:

      .. code-block::

         CHANGED: partition=1 start=2048 old: size=79978496 end=79980544 new: size=83873317,end=83875365

   #. Run the following command to query the partitions of **/dev/xvda**:

      **parted -l /dev/xvda**

      The command output is as follows:

      .. code-block::

         Model: Xen Virtual Block Device (xvd)
         Disk /dev/xvda: 42.9GB
         Sector size (logical/physical): 512B/512B
         Partition Table: msdos
         Disk Flags:

         Number  Start   End     Size    Type     File system  Flags
         1      1049kB  42.9GB  42.9GB  primary  ext4         boot

   #. Run the following command to obtain the file system type and UUID:

      **blkid**

      The command output is as follows:

      .. code-block::

         /dev/xvda1: UUID="7c4fce5d-f8f7-4ed6-8463-f2bd22d0ddea" TYPE="ext4"

   #. Stop the ECS and use it to create a private image.

      .. code-block:: console

         [root@sluo-ecs-e6dc-resizefs ~]# poweroff
         Connection closed by foreign host.
         Disconnected from remote host at 11:08:54.
         Type `help´ to learn how to use Xshell prompt.

   #. Use the created image to create an ECS with a 100 GB system disk. Log in to the ECS and run the following command to query the partitions of **/dev/xvda**:

      **parted -l /dev/xvda**

      As shown in the command output, the root partition has been expanded to 107 GB.

      .. code-block::

         Model: Xen Virtual Block Device (xvd)
         Disk /dev/xvda: 107GB
         Sector size (logical/physical): 512B/512B
         Partition Table: msdos
         Disk Flags:

         Number  Start   End    Size   Type     File system  Flags
          1      1049kB  107GB  107GB  primary  ext4         boot

      .. note::

         The value of **Size** is the size of the expanded root partition.
