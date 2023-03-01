:original_name: en-us_topic_0037352186.html

.. _en-us_topic_0037352186:

Uninstalling PV Drivers from a Linux ECS
========================================

Scenarios
---------

When optimizing a Linux private image with Xen virtualization, you need to change the UUID in the fstab and GRUB configuration files, and install native Xen and KVM drivers on the source ECS of the image.

To ensure that you can successfully install native Xen and KVM drivers, you must uninstall PV drivers from the ECS first.

Procedure
---------

#. Log in to the ECS as user **root** using VNC.

#. Run the following command to check whether PV drivers are installed in the OS:

   **ps -ef \| grep uvp-monitor**

   -  If the following information is displayed, PV drivers have been installed.
   -  Otherwise, PV drivers are not installed. No further actions will be required.

   .. code-block::

      root     4561        1    0   Jun29 ?           00:00:00   /usr/bin/uvp-monitor
      root     4567     4561    0   Jun29 ?           00:00:00   /usr/bin/uvp-monitor
      root     6185     6085    0   03:04  pts/2      00:00:00   grep uvp-monitor

#. In the VNC login window, open the CLI.

   For how to open the CLI, see the OS manual.

#. Run the following command to uninstall PV drivers:

   **/etc/.uvp-monitor/uninstall**

   -  PV drivers are uninstalled successfully if the following command output is displayed:

      .. code-block::

         The PV driver is uninstalled successfully. Reboot the system for the uninstallation to take effect.

   -  If the command output indicates that **.uvp-monitor** is not found, go to :ref:`5 <en-us_topic_0037352186__li45681026173616>`.

      .. code-block::

         -bash: /etc/.uvp-monitor/uninstall: No such file or directory

#. .. _en-us_topic_0037352186__li45681026173616:

   Perform the following operations to delete uvp-monitor that failed to take effect, preventing log overflow:

   a. Run the following command to check whether UVP user-mode programs are installed in the OS:

      **rpm -qa \| grep uvp**

      Information similar to the following is displayed:

      .. code-block::

         libxenstore_uvp3_0-3.00-36.1.x86_64
         uvp-monitor-2.2.0.315-3.1.x86_64
         kmod-uvpmod-2.2.0.315-3.1.x86_64

   b. Run the following commands to delete the installation packages:

      **rpm -e kmod-uvpmod**

      **rpm -e uvp-monitor**

      **rpm -e libxenstore_uvp**
