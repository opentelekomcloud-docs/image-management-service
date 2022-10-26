:original_name: en-us_topic_0122876047.html

.. _en-us_topic_0122876047:

Configuring Cloud-Init
======================

Scenarios
---------

You need to configure Cloud-Init after it is installed.

Prerequisites
-------------

-  Cloud-Init has been installed.
-  An EIP has been bound to the ECS.
-  You have logged in to the ECS.
-  The IP address obtaining mode of the ECS is DHCP.

Procedure
---------

The following operations are required:

#. Configure Cloud-Init.

   For details, see :ref:`Configure Cloud-Init <en-us_topic_0122876047__en-us_topic_0029124518_section5756595193936>`.

#. Check whether Cloud-Init is successfully configured.

   For details, see :ref:`Check the Cloud-Init Configuration <en-us_topic_0122876047__section56956574101031>`.

.. _en-us_topic_0122876047__en-us_topic_0029124518_section5756595193936:

Configure Cloud-Init
--------------------

#. Configure the user permissions for logging in to the ECS. If you use a common account (not user **root**) to log in to the ECS, disable the SSH permissions of user **root** and remote login using a password to improve the ECS security.

   -  You can remotely log in to the ECS using SSH and a key pair injected into your account. (It is recommended that you select the key pair login mode when creating an ECS.)
   -  You can also use a random password to log in to the ECS through noVNC.

   Run the following command to open the **sshd_config** file using the vi editor:

   **vi /etc/ssh/sshd_config**

#. Change the value of **PasswordAuthentication** in the **sshd_config** file to **no**.

   .. note::

      For SUSE and openSUSE, change the values of the following parameters in the **sshd_config** file to **no**:

      -  PasswordAuthentication
      -  ChallengeResponseAuthentication

#. Run the following command to open the **cloud.cfg** file using the vi editor:

   **vi /etc/cloud/cloud.cfg**

#. (Optional) In **/etc/cloud/cloud.cfg**, set **apply_network_config** to **false**.

   This step is only for Cloud-Init 18.3 or later.


   .. figure:: /_static/images/en-us_image_0000001082321842.png
      :alt: **Figure 1** Example configuration

      **Figure 1** Example configuration

#. Disable the SSH permissions of user **root** in **/etc/cloud/cloud.cfg**, add a common user (which is used for logging in to the ECS using VNC), and configure a password for the added user and assign sudo permissions to it.

   .. note::

      For Ubuntu and Debian, set the value of **manage_etc_hosts** in the **/etc/cloud/cloud.cfg** file to **localhost**. Otherwise, switching to user **root** from a user other than **root** may time out.

   Take Ubuntu as an example.

   -  Run the following command to create script **/etc/cloud/set_linux_random_password.sh**, which is executable and can be used to generate random passwords:

      **cat /etc/cloud/set_linux_random_password.sh**

      The file content is as follows:

      .. code-block::

         #!/bin/bash

         password=$(cat /dev/urandom | tr -dc 'A-Za-z0-9!@#$%&+=' | head -c 9)

         echo "linux:$password" | chpasswd
         sed -i -e '/^Login/d' /etc/issue
         sed -i -e '/^Initial/d' /etc/issue
         sed -i -c -e '/^$/d' /etc/issue
         echo -e "\nInitial login with linux:$password\n" >> /etc/issue

      .. note::

         You can run the **chmod +x /etc/cloud/set_linux_random_password.sh** command to add execute permissions of **set_linux_random_password.sh**.

   -  After you log in to the ECS, run the following commands to add a user-friendly prompt "Please change password for user linux after first login."

      **echo -e '\\e[1;31m#################################\\\\e[0m' > /etc/motd**

      **echo -e '\\e[1;31m# Important !!! #\\e[0m' >> /etc/motd**

      **echo -e '\\e[1;31m# Please change password for user linux after first login. #\\e[0m' >> /etc/motd**

      **echo -e '\\e[1;31m#################################\\e[0m' >> /etc/motd**

      **echo -e '' >> /etc/motd**

#. Add a common login user, set its password, assign sudo permissions to it, and use bootcmd to create a script used for generating a random password for each created ECS.

   .. caution::

      Ensure that the configuration file format (such as alignment and spaces) is consistent with the provided example.

   .. code-block::

      system_info:
          # This will affect which distro class gets used
          distro: rhel
          # Default user name + that default users groups (if added/used)
          default_user:
            name: linux  //Username for login
            lock_passwd: False  //Login using a password is enabled. Note that some OSs use value 0 to enable the password login.
            gecos: Cloud User
            groups: users  //Optional. Add users to other groups that have been configured in /etc/group.
            passwd: $6$I63DBVKK$Zh4lchiJR7NuZvtJHsYBQJIg5RoQCRLS1X2Hsgj2s5JwXI7KUO1we8WYcwbzeaS2VNpRmNo28vmxxCyU6LwoD0
            sudo: ["ALL=(ALL) NOPASSWD:ALL"]  // Assign the root rights to the user.
            shell: /bin/bash  //Execute shell in bash mode.
          # Other config here will be given to the distro class and/or path classes
          paths:
             cloud_dir: /var/lib/cloud/
             templates_dir: /etc/cloud/templates/
          ssh_svcname: sshd

      bootcmd:
      - [cloud-init-per, instance, password, bash,
      /etc/cloud/set_linux_random_password.sh]

   .. note::

      The value of **passwd** is encrypted using SHA512 (which is used as an example). For more details, see https://cloudinit.readthedocs.io/en/latest/topics/examples.html.

      For details about how to encrypt a password and generate ciphertext, see the following (encrypting password **cloud.1234** is used as an example):

      .. code-block::

         [root@** ~]# python -c "import crypt, getpass, pwd; print crypt.mksalt()"
         $6$I63DBVKK
         [root@** ~]# python -c "import crypt, getpass, pwd; print crypt.crypt('cloud.1234', '\$6\$I63DBVKK')"
         $6$I63DBVKK$Zh4lchiJR7NuZvtJHsYBQJIg5RoQCRLS1X2Hsgj2s5JwXI7KUO1we8WYcwbzeaS2VNpRmNo28vmxxCyU6LwoD0

#. Enable the agent to access the IaaS OpenStack data source.

   Add the following information to the last line of **/etc/cloud/cloud.cfg**:

   .. code-block::

      datasource_list: [ OpenStack ]
      datasource:
        OpenStack:
          metadata_urls: ['http://169.254.169.254']
          max_wait: 120
          timeout: 5

   .. note::

      -  You can decide whether to set **max_wait** and **timeout**. The values of **max_wait** and **timeout** in the preceding example are only for reference.

      -  If the OS version is earlier than Debian 8 or CentOS 5, you cannot enable the agent to access the IaaS OpenStack data source.

      -  The default zeroconf route must be disabled for CentOS and EulerOS ECSs for accurate access to the IaaS OpenStack data source.

         **echo "NOZEROCONF=yes" >> /etc/sysconfig/network**

#. Prevent Cloud-Init from taking over the network in **/etc/cloud/cloud.cfg**.

   If the Cloud-Init version is 0.7.9 or later, add the following content to **/etc/cloud/cloud.cfg**:

   .. code-block::

      network:
        config: disabled

   .. note::

      The added content must be in the YAML format.


   .. figure:: /_static/images/en-us_image_0122875972.png
      :alt: **Figure 2** Preventing Cloud-Init from taking over the network

      **Figure 2** Preventing Cloud-Init from taking over the network

#. Modify the **cloud_init_modules** configuration file.

   Move **ssh** from the bottom to the top to speed up the SSH login.


   .. figure:: /_static/images/en-us_image_0122875976.png
      :alt: **Figure 3** Speeding up the SSH login to the ECS

      **Figure 3** Speeding up the SSH login to the ECS

#. Modify the configuration so that the hostname of the ECS created from the image does not contain the **.novalocal** suffix and can contain a dot (.).

   a. Run the following command to modify the **\__init__.py** file:

      **vi /usr/lib/python2.7/site-packages/cloudinit/sources/__init__.py**

      Press **i** to enter editing mode. Search for **toks**. The following information is displayed:

      .. code-block::

         if toks:
             toks = str(toks).split('.')
         else:
             toks = ["ip-%s" % lhost.replace(".", "-")]
         else:
             toks = lhost.split(".novalocal")

         if len(toks) > 1:
             hostname = toks[0]
             #domain = '.'.join(toks[1:])
         else:
             hostname = toks[0]

         if fqdn and domain != defdomain:
             return "%s.%s" % (hostname, domain)
         else:
             return hostname

      After the modification is complete, press **Esc** to exit the editing mode and enter **:wq!** to save the configuration and exit.


      .. figure:: /_static/images/en-us_image_0125515202.png
         :alt: **Figure 4** Modifying the **\__init__.py** file

         **Figure 4** Modifying the **\__init__.py** file

   b. Run the following command to switch to the **cloudinit/sources** folder:

      **cd /usr/lib/python2.7/site-packages/cloudinit/sources/**

   c. Run the following commands to delete the **\__init__.pyc** file and the optimized **\__init__.pyo** file:

      **rm -rf \__init__.pyc**

      **rm -rf \__init__.pyo**

   d. Run the following commands to clear the logs:

      **rm -rf /var/lib/cloud/\***

      **rm -rf /var/log/cloud-init\***

#. Run the following command to edit the **/etc/cloud/cloud.cfg.d/05_logging.cfg** file to use cloudLogHandler to process logs:

   **vim /etc/cloud/cloud.cfg.d/05_logging.cfg**


   .. figure:: /_static/images/en-us_image_0141888758.png
      :alt: **Figure 5** Setting the parameter value to **cloudLogHandler**

      **Figure 5** Setting the parameter value to **cloudLogHandler**

.. _en-us_topic_0122876047__section56956574101031:

Check the Cloud-Init Configuration
----------------------------------

Run the following command to check whether Cloud-Init has been properly configured:

**cloud-init init --local**

If Cloud-Init has been properly installed, the version information is displayed and no error occurs. For example, messages indicating lack of files will not be displayed.

.. note::

   (Optional) Run the following command to set the password validity period to the maximum:

   **chage -M 99999 $user_name**

   *user_name* is a system user, such as user **root**.

   You are advised to set the password validity period to **99999**.
