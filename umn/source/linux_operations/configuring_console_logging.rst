:original_name: en-us_topic_0057450886.html

.. _en-us_topic_0057450886:

Configuring Console Logging
===========================

Scenarios
---------

If you want to use the ECS console logging function, you need to configure related parameters on the ECS.

Currently, ECSs running the following OSs are supported: CentOS 6 series, Red Hat 6 series, CentOS 7 series, Red Hat 7 series, Ubuntu 14 series, SUSE 11 series, SUSE 12 series, Debian, Ubuntu 16 series, Fedora, FreeBSD, and CoreOS.

.. note::

   To use the Console Log function on the ECS console, perform this operation. Otherwise, skip this section.

Prerequisites
-------------

You have logged in to the ECS.

Procedure
---------

The configuration method varies depending on the OS.

.. note::

   To prevent impact on the start of the recovery mode, you are advised to modify only the item used for the default start.

-  For CentOS and Red Hat 6, perform the following steps:

   #. Run the following command to open the configuration file:

      **vi /boot/grub/menu.lst**

   #. Locate the row that contains **linux**, **linux16**, or **kernel** (depending on the system), add **console=ttyS0** to its end, and delete parameter **rhgb quiet**. If **console=ttyS0** already exists, you do not need to add it. Save the change and exit.

-  For CentOS 7, Red Hat 7, and Ubuntu 14, perform the following steps:

   #. Run the following command to open the configuration file:

      **vi /boot/grub2/grub.cfg**

   #. Locate the row that contains **linux**, **linux16**, or **kernel** (depending on the system), add **console=ttyS0** to its end, and delete parameter **rhgb quiet**. If **console=ttyS0** already exists, you do not need to add it. Save the change and exit.

-  For SUSE Linux 11, perform the following steps:

   #. Run the following command to open the configuration file:

      **vi /boot/grub/menu.1st**

   #. Locate the row that contains **linux**, **linux16**, or **kernel** (depending on the system) and add **console=ttyS0** to its end. If **console=ttyS0** already exists, you do not need to add it. Save the change and exit.

-  For SUSE Linux 12, openSUSE 13, and openSUSE 42, perform the following steps:

   #. Run the following command to open the configuration file:

      **vi /boot/grub2/grub.cfg**

   #. Locate the row that contains **linux**, **linux16**, or **kernel** (depending on the system) and add **console=ttyS0** to its end. If **console=ttyS0** already exists, you do not need to add it. Save the change and exit.

-  For Debian and Ubuntu 16, perform the following steps:

   #. Run the following command to open the configuration file:

      **vi /boot/grub/grub.cfg**

   #. Locate the row that contains **linux**, **linux16**, or **kernel** (depending on the system) and add **console=ttyS0** to its end. If **console=ttyS0** already exists, you do not need to add it. Save the change and exit.

-  For Fedora, perform the following steps:

   #. Run the following command to open the configuration file:

      **vi /boot/grub2/grub.cfg**

   #. Locate the row that contains **linux**, **linux16**, or **kernel** (depending on the system) and add **console=ttyS0** to its end. If **console=ttyS0** already exists, you do not need to add it. Save the change and exit.

-  For FreeBSD, perform the following steps:

   #. Run the following command to open the configuration file:

      **vi /boot/loader.conf**

   #. Add **console="comconsole"**. If **console="comconsole"** already exists, you do not need to add it. Save the change and exit.

-  For CoreOS, perform the following steps:

   #. Run the following command to check whether **ttyS0** has been configured:

      **cat /proc/cmdline \| grep ttyS0**

      -  If yes, **ttyS0** has been configured.
      -  If no, **ttyS0** has not been configured. Go to :ref:`2 <en-us_topic_0057450886__li29451607172853>`.

   #. .. _en-us_topic_0057450886__li29451607172853:

      Run the following command to open the configuration file to be edited:

      **vi /usr/share/oem/grub.cfg**

      .. note::

         If the **/usr/share/oem/grub.cfg** configuration file does not exist, manually create the file.

   #. Add **set linux_append="console=ttyS0"**. If **set linux_append="console=ttyS0"** already exists, you do not need to add it. Save the change and exit.
