:original_name: en-us_topic_0030713219.html

.. _en-us_topic_0030713219:

What Do I Do If the Disks of an ECS Created from a CentOS Image Cannot Be Found?
================================================================================

Symptom
-------

Generally, this is because the xen-blkfront.ko module is not loaded during the startup. You need to modify OS kernel startup parameters. :ref:`Figure 1 <en-us_topic_0030713219__en-us_topic_0029124532_fb625ead0fbca4936a8a0b147e6719b71>` shows the startup screen after the login to the ECS.

.. _en-us_topic_0030713219__en-us_topic_0029124532_fb625ead0fbca4936a8a0b147e6719b71:

.. figure:: /_static/images/en-us_image_0207619456.png
   :alt: **Figure 1** Startup screen


   **Figure 1** Startup screen

Solution
--------

Perform the following operations to modify OS kernel boot parameters:

.. note::

   These operations must be performed after the OS starts. You are advised to modify kernel boot parameters in the ECS used for creating the image.

#. Run the following command to log in to the OS:

   **lsinitrd /boot/initramfs-\`**\ *uname* **-r\ \`.img \|grep -i xen**

   -  If the command output contains **xen-blkfront.ko**, contact the customer service.
   -  If no command output is displayed, go to :ref:`2 <en-us_topic_0030713219__li155801950404>`.

#. .. _en-us_topic_0030713219__li155801950404:

   Back up the GRUB configuration file.

   -  If the ECS runs CentOS 6, run the following command:

      **cp /boot/grub/grub.conf /boot/grub/grub.conf.bak**

   -  If the ECS runs CentOS 7, run the following command:

      **cp /boot/grub2/grub.cfg /boot/grub2/grub.cfg.bak**

#. Use the **vi** editor to open the GRUB configuration file. Run the following command (using CentOS 7 as an example):

   **vi /boot/grub2/grub.cfg**

#. Add **xen_emul_unplug=all** to the default boot kernel.

   .. note::

      Search for the line that contains **root=UUID=** and add **xen_emul_unplug=all** to the end of the line.

   .. code-block::

      menuentry 'CentOS Linux (3.10.0-229.el7.x86_64) 7 (Core) with debugging' --class centos --class gnu-linux --class gnu --class os --unrestricted $menuentry_id_option 'gnulinux-3.10.0-229.el7.x86_64-advanced-bf3cc825-7638-48d8-8222-cd2f412dd0de' {
              load_video
              set gfxpayload=keep
              insmod gzio
              insmod part_msdos
              insmod ext2
              set root='hd0,msdos1'
              if [ x$feature_platform_search_hint = xy ]; then
                search --no-floppy --fs-uuid --set=root --hint='hd0,msdos1'  bf3cc825-7638-48d8-8222-cd2f412dd0de
              else
                search --no-floppy --fs-uuid --set=root bf3cc825-7638-48d8-8222-cd2f412dd0de
              fi
              linux16 /boot/vmlinuz-3.10.0-229.el7.x86_64 root=UUID=bf3cc825-7638-48d8-8222-cd2f412dd0de xen_emul_unplug=all ro crashkernel=auto rhgb quiet  systemd.log_level=debug systemd.log_target=kmsg
              initrd16 /boot/initramfs-3.10.0-229.el7.x86_64.img
      }

#. Press **Esc**, enter **:wq**, and press **Enter** to exit the vi editor.

#. Create an image using the ECS, upload and register the image on the cloud platform.
