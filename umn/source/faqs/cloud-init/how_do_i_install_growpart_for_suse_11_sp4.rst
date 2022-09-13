:original_name: en-us_topic_0078454810.html

.. _en-us_topic_0078454810:

How Do I Install growpart for SUSE 11 SP4?
==========================================

Scenarios
---------

growpart for SUSE and openSUSE is an independent toolkit that does not start with **cloud-\***. Perform operations in this section to install growpart.

Procedure
---------

#. Run the following commands to check whether Cloud-Init and growpart have been installed:

   **rpm -qa \| grep cloud-init**

   The command output is as follows:

   .. code-block::

      cloud-init-0.7.8-39.2

   **rpm -qa \| grep growpart**

   The command output is as follows:

   .. code-block::

      growpart-0.29-8.1

#. Run the following command to uninstall Cloud-Init and growpart:

   **zypper remove cloud-init growpart**

#. Run the following commands to delete residual files:

   **rm -fr /etc/cloud/\***

   **rm -fr /var/lib/cloud/\***

#. Run the following command to install growpart:

   **zypper install http://download.opensuse.org/repositories/home:/garloff:/OTC:/cloudinit/SLE_11_SP4/noarch/growpart-0.27-1.1.noarch.rpm**

#. Run the following command to install python-oauth:

   **zypper install http://download.opensuse.org/repositories/home:/garloff:/OTC:/cloudinit/SLE_11_SP4/x86_64/python-oauth-1.0.1-35.1.x86_64.rpm**

#. Run the following command to install Cloud-Init:

   **zypper install http://download.opensuse.org/repositories/home:/garloff:/OTC:/cloudinit/SLE_11_SP4/x86_64/cloud-init-0.7.6-27.23.1.x86_64.rpm**

#. Run the following commands to check whether growpart, python-oauth, and Cloud-Init have been installed successfully:

   **rpm -qa \| grep growpart**

   The command output is as follows:

   .. code-block::

      growpart-0.27-1.1

   **rpm -qa \| grep python-oauth**

   The command output is as follows:

   .. code-block::

      python-oauthlib-0.6.0-1.5
      python-oauth-1.0.1-35.1

   **rpm -qa \| grep cloud-init**

   The command output is as follows:

   .. code-block::

      cloud-init-0.7.6-27.19.1

#. Run the following command to check the configuration:

   **chkconfig cloud-init-local on;chkconfig cloud-init on;chkconfig cloud-config on;chkconfig cloud-final on**
