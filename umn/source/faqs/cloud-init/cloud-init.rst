:original_name: en-us_topic_0132216287.html

.. _en-us_topic_0132216287:

Cloud-Init
==========

You are advised to install Cloud-Init on the ECS that will be used to create a private image so that new ECSs created from the private image support custom configurations (for example, changing the ECS login password).

For details about how to install Cloud-Init, see :ref:`Installing Cloud-Init <en-us_topic_0030730603>`.

For details about how to configure Cloud-Init, see :ref:`Configuring Cloud-Init <en-us_topic_0122876047>`.

The following describes common problems you may encounter when installing Cloud-Init and their solutions.

Ubuntu 16.04/CentOS 7: Failed to Set Cloud-Init Automatic Start
---------------------------------------------------------------

-  Symptom:

   After Cloud-Init is installed, run the following command to set Cloud-Init automatic start:

   **systemctl enable cloud-init-local.service cloud-init.service cloud-config.service cloud-final.service**

   Information similar to the following is displayed:


   .. figure:: /_static/images/en-us_image_0137066322.png
      :alt: **Figure 1** Failed to enable Cloud-Init to start automatically

      **Figure 1** Failed to enable Cloud-Init to start automatically

-  Solution:

   #. Run the following command to roll back the configuration:

      **systemctl unmask cloud-init-local.service cloud-init.service cloud-config.service cloud-final.service**

   #. Run the following command to set automatic start again:

      **systemctl enable cloud-init-local.service cloud-init.service cloud-config.service cloud-final.service**

   #. Run the following command to check the Cloud-Init status:

      **systemctl status cloud-init-local.service cloud-init.service cloud-config.service cloud-final.service**

      As shown in the following figures, **failed** is displayed and all services are in the **inactive** state.


      .. figure:: /_static/images/en-us_image_0137085941.png
         :alt: **Figure 2** Checking Cloud-Init status

         **Figure 2** Checking Cloud-Init status


      .. figure:: /_static/images/en-us_image_0137085943.png
         :alt: **Figure 3** Checking Cloud-Init status

         **Figure 3** Checking Cloud-Init status

      This is because the address that the system uses to access Cloud-Init is redirected to **/usr/bin/**, but the actual installation path is **/usr/local/bin**.

   #. Run the following command to copy Cloud-Init to the **usr/bin** directory:

      **cp /usr/local/cloud-init /usr/bin/**

   #. Run the following command to restart Cloud-Init:

      **systemctl restart cloud-init-local.service cloud-init.service cloud-config.service cloud-final.service**


      .. figure:: /_static/images/en-us_image_0138105252.png
         :alt: **Figure 4** Restarting Cloud-Init

         **Figure 4** Restarting Cloud-Init

   #. Run the following command to check the Cloud-Init status:

      **systemctl status cloud-init-local.service cloud-init.service cloud-config.service cloud-final.service**

Ubuntu 14.04: chkconfig and systemctl Not Installed
---------------------------------------------------

-  Symptom:

   chkconfig is not installed.

-  Solution:

   Run the following commands to install chkconfig:

   **apt-get update**

   **apt-get install sysv-rc-conf**

   **cp /usr/sbin/sysv-rc-conf /usr/sbin/chkconfig**

   Run the following command to query the Cloud-Init version:

   **cloud-init -v**

   Information similar to the following is displayed:

   .. code-block::

      -bash:/usr/bin/cloud-init:not found this command

   Solution: Run the following command to copy Cloud-Init to the **usr/bin** directory:

   **cp /usr/local/bin/cloud-init /usr/bin**/

Debian 9.5: Failed to Query the Cloud-Init Version and Set Automatic Start
--------------------------------------------------------------------------

#. Run the following command to query the Cloud-Init version:

   **cloud-init -v**

   Information similar to the following is displayed:

   .. code-block::

      -bash:/usr/bin/cloud-init:not found this command

   Solution: Run the **cp /usr/local/bin/cloud-init /usr/bin/** command to copy Cloud-Init to the **usr/bin** directory.

#. Run the **cloud-init init --local** command.

   Information similar to the following is displayed:


   .. figure:: /_static/images/en-us_image_0137070023.png
      :alt: **Figure 5** Information returned when Cloud-Init automatic start successfully set

      **Figure 5** Information returned when Cloud-Init automatic start successfully set

   Cause analysis: The compilation fails because GCC is not installed.

   Solution:

   Run the following command to install GCC. Then, install Cloud-Init again.

   **yum -y install gcc**

#. After Cloud-Init is installed, run the following command to set Cloud-Init automatic start:

   **systemctl enable cloud-init-local.service cloud-init.service cloud-config.service cloud-final.service**

   Information similar to the following is displayed.


   .. figure:: /_static/images/en-us_image_0137070025.png
      :alt: **Figure 6** Prompt indicating the failure to set Cloud-Init automatic start

      **Figure 6** Prompt indicating the failure to set Cloud-Init automatic start

   Solution:

   a. Run the following command to roll back the configuration:

      **systemctl unmask cloud-init-local.service cloud-init.service cloud-config.service cloud-final.service**

   b. Run the following command to set automatic start again:

      **systemctl enable cloud-init-local.service cloud-init.service cloud-config.service cloud-final.service**

   c. Run the following command to restart Cloud-Init:

      **systemctl restart cloud-init-local.service cloud-init.service cloud-config.service cloud-final.service**

      Run the **systemctl status** command to check the Cloud-Init status. Information similar to the following is displayed:


      .. figure:: /_static/images/en-us_image_0137069967.png
         :alt: **Figure 7** Verifying the service status

         **Figure 7** Verifying the service status

CentOS 7/Fedora 28: Required C Compiler Not Installed
-----------------------------------------------------

-  Symptom

   After Cloud-Init is successfully installed, run the following command:

   **cloud-init init --local**

   The following information is displayed:

   .. code-block::

      /usr/lib/python2.5/site-packages/Cheetah/Compiler.py:1532: UserWarning:
      You don't have the C version of NameMapper installed! I'm disabling Cheetah's useStackFrames option as it is painfully slow with the Python version of NameMapper. You should get a copy of Cheetah with the compiled C version of NameMapper.
        "\nYou don't have the C version of NameMapper installed!

-  Cause analysis

   This alarm is generated because C version of NameMapper needs to be compiled when Cloud-Init is installed. However, GCC is not installed in the system, and the compilation cannot be performed. As a result, NameMapper is missing.

-  Solution

   Run the following command to install GCC:

   **yum -y install gcc**

   Reinstall Cloud-Init.

CentOS 7/Fedora: Failed to Use the New Password to Log In to an ECS Created from an Image
-----------------------------------------------------------------------------------------

-  Symptom

   After Cloud-Init is successfully installed on an ECS, an image is created from the ECS. You cannot use a new password to log in to the ECSs created from this image. When you log in to the ECSs using the old password, you find that NICs of these ECSs are not started.


   .. figure:: /_static/images/en-us_image_0137083450.png
      :alt: **Figure 8** NIC not started

      **Figure 8** NIC not started

-  Solution:

   Log in to the ECS used to create the image, open the DHCP configuration file **/etc/sysconfig/network-scripts/ifcfg-eth**\ *X*, and comment out **HWADDR**.
