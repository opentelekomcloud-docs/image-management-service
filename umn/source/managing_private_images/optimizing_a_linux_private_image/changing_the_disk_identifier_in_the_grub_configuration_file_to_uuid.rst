:original_name: en-us_topic_0086020895.html

.. _en-us_topic_0086020895:

Changing the Disk Identifier in the GRUB Configuration File to UUID
===================================================================

Scenarios
---------

When optimizing a Linux private image, you need to change the disk identifier to UUID in the GRUB configuration file of the ECS.

Modify the **menu.lst** or **grub.cfg** configuration file (**/boot/grub/menu.lst**, **/boot/grub/grub.cfg**, **/boot/grub2/grub.cfg**, **/boot/grub/grub.conf**, or **/boot/efi/EFI/euleros/grub.cfg**), and configure the boot partition using the UUID.

.. note::

   The root partition identified in the configuration file varies depending on the OS. It may be **root=/dev/xvda** or **root=/dev/disk**.

Procedure
---------

-  Ubuntu 14.04: Run **blkid** to obtain the UUID of the root partition. Modify the **/boot/grub/grub.cfg** file and use the UUID of the root partition to configure the boot item. If the root partition already uses UUID, no modification is required. The procedure is as follows:

   #. Log in to the ECS as user **root**.

   #. Run the following command to query all types of mounted file systems and device UUIDs:

      **blkid**

      The following information is displayed:

      .. code-block::

         /dev/xvda1: UUID="ec51d860-34bf-4374-ad46-a0c3e337fd34" TYPE="ext3"
         /dev/xvda5: UUID="7a44a9ce-9281-4740-b95f-c8de33ae5c11" TYPE="swap"

   3. Run the following command to query the **grub.cfg** file:

      **cat /boot/grub/grub.cfg**

      The following information is displayed:

      .. code-block::

         ......menuentry 'Ubuntu Linux, with Linux 3.13.0-24-generic' --class ubuntu --class gnu-linux --class gnu --class os --unrestricted $menuentry_id_option 'gnulinux-3.13.0-24-generic-advanced-ec51d860-34bf-4374-ad46-a0c3e337fd34' {
         recordfail
         load_video
         gfxmode $linux_gfx_mode
         insmod gzio
         insmod part_msdos
         insmod ext2
         if [ x$feature_platform_search_hint = xy ]; then
         search --no-floppy --fs-uuid --set=root ec51d860-34bf-4374-ad46-a0c3e337fd34
         else
         search --no-floppy --fs-uuid --set=root ec51d860-34bf-4374-ad46-a0c3e337fd34
         fi
         echo 'Loading Linux 3.13.0-24-generic ...'
         linux /boot/vmlinuz-3.13.0-24-generic root=/dev/xvda1 ro
         echo 'Loading initial ramdisk ...'
         initrd /boot/initrd.img-3.13.0-24-generic
         }

   4. Check whether the root partition in the **/boot/grub/grub.cfg** configuration file contains **root=/dev/xvda1** or **root=UUID=ec51d860-34bf-4374-ad46-a0c3e337fd34**.

      -  If **root=UUID=ec51d860-34bf-4374-ad46-a0c3e337fd34** is contained, the root partition is in the UUID format and requires no change.
      -  If **root=/dev/xvda1** is contained, the root partition is in the device name format. Go to :ref:`5 <en-us_topic_0086020895__en-us_topic_0037352187_li5200232314010>`.

   5. .. _en-us_topic_0086020895__en-us_topic_0037352187_li5200232314010:

      Identify the UUID of the root partition device based on **root=/dev/xvda1** (device name of the root partition) and the partition information obtained by running the **blkid** command.

   6. Run the following command to open the **grub.cfg** file:

      **vi /boot/grub/grub.cfg**

   7. Press **i** to enter editing mode and change the root partition to the UUID format, for example, from **root=/dev/xvda1** to **root=UUID=ec51d860-34bf-4374-ad46-a0c3e337fd34**.

   8. Press **Esc**, enter **:wq**, and press **Enter**. The system saves the configuration and exits the vi editor.

   9. Run the following command to verify the change:

      **cat /boot/grub/grub.cfg**

      The change is successful if information similar to the following is displayed:

      .. code-block::

         ......menuentry 'Ubuntu Linux, with Linux 3.13.0-24-generic' --class ubuntu --class gnu-linux --class gnu --class os --unrestricted $menuentry_id_option 'gnulinux-3.13.0-24-generic-advanced-ec51d860-34bf-4374-ad46-a0c3e337fd34' {
         recordfail
         load_video
         gfxmode $linux_gfx_mode
         insmod gzio
         insmod part_msdos
         insmod ext2
         if [ x$feature_platform_search_hint = xy ]; then
         search --no-floppy --fs-uuid --set=root ec51d860-34bf-4374-ad46-a0c3e337fd34
         else
         search --no-floppy --fs-uuid --set=root ec51d860-34bf-4374-ad46-a0c3e337fd34
         fi
         echo 'Loading Linux 3.13.0-24-generic ...'
         linux /boot/vmlinuz-3.13.0-24-generic root=UUID=ec51d860-34bf-4374-ad46-a0c3e337fd34 ro
         echo 'Loading initial ramdisk ...'
         initrd /boot/initrd.img-3.13.0-24-generic
         }

-  CentOS 6.5: Run **blkid** to obtain the UUID of the root partition. Modify the **/boot/grub/grub.conf** file and use the UUID of the root partition to configure the boot item. If the root partition already uses UUID, no modification is required. The procedure is as follows:

   #. Log in to the ECS as user **root**.

   #. Run the following command to query all types of mounted file systems and device UUIDs:

      **blkid**

      The following information is displayed:

      .. code-block::

         /dev/xvda1: UUID="749d6c0c-990a-4661-bed1-46769388365a" TYPE="swap"
         /dev/xvda2: UUID="f382872b-eda6-43df-9516-5a687fecdce6" TYPE="ext4"

   3. Run the following command to query the **grub.conf** file:

      **cat /boot/grub/grub.conf**

      The following information is displayed:

      .. code-block::

         default=0
         timeout=5
         splashimage=(hd0,1)/boot/grub/splash.xpm.gz
         hiddenmenu
         title CentOS (2.6.32-573.8.1.el6.x86_64)
         root (hd0,1)
         kernel /boot/vmlinuz-2.6.32-573.8.1.el6.x86_64 ro root=/dev/xvda2 rd_NO_LUKS rd_NO_LVM LANG=en_US.UTF-8 rd_NO_MD SYSFONT=latarcyrheb-sun16 crashkernel=autoKEYBOARDTYPE=pc KEYTABLE=us rd_NO_DM rhgb quiet
         initrd /boot/initramfs-2.6.32-573.8.1.el6.x86_64.img

   4. Check whether the root partition in the **/boot/grub/grub.conf** configuration file contains **root=/dev/xvda2** or **root=UUID=f382872b-eda6-43df-9516-5a687fecdce6**.

      -  If **root=UUID=f382872b-eda6-43df-9516-5a687fecdce6** is contained, the root partition is in the UUID format and requires no change.
      -  If **root=/dev/xvda2** is contained, the root partition is in the device name format. Go to :ref:`5 <en-us_topic_0086020895__en-us_topic_0037352187_li954614614457>`.

   5. .. _en-us_topic_0086020895__en-us_topic_0037352187_li954614614457:

      Identify the UUID of the root partition device based on **root=/dev/xvda2** (device name of the root partition) and the partition information obtained by running the **blkid** command.

   6. Run the following command to open the **grub.conf** file:

      **vi /boot/grub/grub.conf**

   7. Press **i** to enter editing mode and change the root partition to the UUID format, for example, from **root=/dev/xvda2** to **root=UUID=f382872b-eda6-43df-9516-5a687fecdce6**.

   8. Press **Esc**, enter **:wq**, and press **Enter**. The system saves the configuration and exits the vi editor.

   9. Run the following command to verify the change:

      **cat /boot/grub/grub.conf**

      The change is successful if information similar to the following is displayed:

      .. code-block::

         default=0
         timeout=5
         splashimage=(hd0,1)/boot/grub/splash.xpm.gz
         hiddenmenu
         title CentOS (2.6.32-573.8.1.el6.x86_64)
         root (hd0,1)
         kernel /boot/vmlinuz-2.6.32-573.8.1.el6.x86_64 ro root=UUID=f382872b-eda6-43df-9516-5a687fecdce6 rd_NO_LUKS rd_NO_LVM LANG=en_US.UTF-8 rd_NO_MD SYSFONT=latarcyrheb-sun16 crashkernel=autoKEYBOARDTYPE=pc KEYTABLE=us rd_NO_DM rhgb quiet
         initrd /boot/initramfs-2.6.32-573.8.1.el6.x86_64.img

-  CentOS 7.0: Run **blkid** to obtain the UUID of the root partition. Modify the **/boot/grub2/grub.cfg** file and use the UUID of the root partition to configure the boot item. If the root partition already uses UUID, no modification is required.

   #. Log in to the ECS as user **root**.

   #. Run the following command to query all types of mounted file systems and device UUIDs:

      **blkid**

      The following information is displayed:

      .. code-block::

         /dev/xvda2: UUID="4eb40294-4c6f-4384-bbb6-b8795bbb1130" TYPE="xfs"
         /dev/xvda1: UUID="2de37c6b-2648-43b4-a4f5-40162154e135" TYPE="swap"

   3. Run the following command to query the **grub.cfg** file:

      **cat /boot/grub2/grub.cfg**

      The following information is displayed:

      .. code-block::

         ......
         menuentry 'CentOS Linux (3.10.0-229.el7.x86_64) 7 (Core)' --class fedora --class gnu-linux --class gnu --class os --unrestricted $menuentry_id_option 'gnulinux-3.10.0-229.el7.x86_64-advanced-4eb40294-4c6f-4384-bbb6-b8795bbb1130' {
         load_video
         set gfxpayload=keep
         insmod gzio
         insmod part_msdos
         insmod xfs
         set root='hd0,msdos2'
         if [ x$feature_platform_search_hint = xy ]; then
         search --no-floppy --fs-uuid --set=root --hint='hd0,msdos2'4eb40294-4c6f-4384-bbb6-b8795bbb1130
         else
         search --no-floppy --fs-uuid --set=root 4eb40294-4c6f-4384-bbb6-b8795bbb1130
         fi
         linux16 /boot/vmlinuz-3.10.0-229.el7.x86_64 root=/dev/xvda2 ro crashkernel=auto rhgb quiet LANG=en_US.UTF-8
         initrd16 /boot/initramfs-3.10.0-229.el7.x86_64.img
         }

   4. Check whether the root partition in the **/boot/grub2/grub.cfg** configuration file contains **root=/dev/xvda2** or **root=UUID=4eb40294-4c6f-4384-bbb6-b8795bbb1130**.

      -  If **root=UUID=4eb40294-4c6f-4384-bbb6-b8795bbb1130** is contained, the root partition is in the UUID format and requires no change.
      -  If **root=/dev/xvda2** is contained, the root partition is in the device name format. Go to :ref:`5 <en-us_topic_0086020895__en-us_topic_0037352187_li2365474142222>`.

   5. .. _en-us_topic_0086020895__en-us_topic_0037352187_li2365474142222:

      Identify the UUID of the root partition device based on **root=/dev/xvda2** (device name of the root partition) and the partition information obtained by running the **blkid** command.

   6. Run the following command to open the **grub.cfg** file:

      **vi /boot/grub2/grub.cfg**

   7. Press **i** to enter editing mode and change the root partition to the UUID format, for example, from **root=/dev/xvda2** to **root=UUID=4eb40294-4c6f-4384-bbb6-b8795bbb1130**.

   8. Press **Esc**, enter **:wq**, and press **Enter**. The system saves the configuration and exits the vi editor.

   9. Run the following command to verify the change:

      **cat /boot/grub2/grub.cfg**

      The change is successful if information similar to the following is displayed:

      .. code-block::

         ......
         menuentry 'CentOS Linux (3.10.0-229.el7.x86_64) 7 (Core)' --class fedora --class gnu-linux --class gnu --class os --unrestricted $menuentry_id_option 'gnulinux-3.10.0-229.el7.x86_64-advanced-4eb40294-4c6f-4384-bbb6-b8795bbb1130' {
         load_video
         set gfxpayload=keep
         insmod gzio
         insmod part_msdos
         insmod xfs
         set root='hd0,msdos2'
         if [ x$feature_platform_search_hint = xy ]; then
         search --no-floppy --fs-uuid --set=root --hint='hd0,msdos2'4eb40294-4c6f-4384-bbb6-b8795bbb1130
         else
         search --no-floppy --fs-uuid --set=root 4eb40294-4c6f-4384-bbb6-b8795bbb1130
         fi
         linux16 /boot/vmlinuz-3.10.0-229.el7.x86_64 root=UUID=4eb40294-4c6f-4384-bbb6-b8795bbb1130 ro crashkernel=auto rhgb quiet LANG=en_US.UTF-8
         initrd16 /boot/initramfs-3.10.0-229.el7.x86_64.img
         }
