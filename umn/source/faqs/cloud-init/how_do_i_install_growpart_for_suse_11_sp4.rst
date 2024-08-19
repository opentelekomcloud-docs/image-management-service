:original_name: en-us_topic_0078454810.html

.. _en-us_topic_0078454810:

How Do I Install growpart for SUSE 11 SP4?
==========================================

Scenarios
---------

For SUSE and openSUSE, growpart is an independent tool and is not included in a **cloud-\*** package. You need to install it separately.

Procedure
---------

#. Check whether Cloud-Init and growpart are installed.

   **rpm -qa \| grep cloud-init**

   If cloud-init is installed, the command output should be similar to the following:

   .. code-block::

      cloud-init-0.7.8-39.2

   **rpm -qa \| grep growpart**

   If growpart is installed, the command output should be similar to the following:

   .. code-block::

      growpart-0.29-8.1

#. If they are installed, uninstall them.

   **zypper remove cloud-init growpart**

#. Delete residual files.

   **rm -fr /etc/cloud/\***

   **rm -fr /var/lib/cloud/\***

#. Install growpart.

   **zypper install http://download.opensuse.org/repositories/home:/garloff:/OTC:/cloudinit/SLE_11_SP4/noarch/growpart-0.27-1.1.noarch.rpm**

#. Install python-oauth.

   **zypper install http://download.opensuse.org/repositories/home:/garloff:/OTC:/cloudinit/SLE_11_SP4/x86_64/python-oauth-1.0.1-35.1.x86_64.rpm**

#. Install Cloud-Init.

   **zypper install http://download.opensuse.org/repositories/home:/garloff:/OTC:/cloudinit/SLE_11_SP4/x86_64/cloud-init-0.7.6-27.23.1.x86_64.rpm**

#. Check whether growpart, python-oauth, and Cloud-Init are installed successfully.

   **rpm -qa \| grep growpart**

   If growpart is installed, the command output should be similar to the following:

   .. code-block::

      growpart-0.27-1.1

   **rpm -qa \| grep python-oauth**

   If python-oauth is installed, the command output should be similar to the following:

   .. code-block::

      python-oauthlib-0.6.0-1.5
      python-oauth-1.0.1-35.1

   **rpm -qa \| grep cloud-init**

   If Cloud-Init is installed, the command output should be similar to the following:

   .. code-block::

      cloud-init-0.7.6-27.19.1

#. Check the configurations.

   **chkconfig cloud-init-local on;chkconfig cloud-init on;chkconfig cloud-config on;chkconfig cloud-final on**
