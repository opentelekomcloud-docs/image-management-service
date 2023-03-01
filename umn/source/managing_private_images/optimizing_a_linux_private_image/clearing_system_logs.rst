:original_name: en-us_topic_0125076462.html

.. _en-us_topic_0125076462:

Clearing System Logs
====================

Delete log files and historical records, and stop the ECS.

#. Run the following commands to delete redundant key files:

   **echo** **>** */$path/$to/$root*\ **/.ssh/authorized_keys**

   An example command is **echo > /root/.ssh/authorized_keys**.

   **echo** **>** */$path/$to/$none-root*\ **/.ssh/authorized_keys**

   An example command is **echo > /home/linux/.ssh/authorized_keys**.

2. Run the following command to clear log files in the **/var/log** directory:

   **rm** **-rf** **/var/log/\***

   .. note::

      Before deleting log files, back up log directories and log files required by application startup. For example, if the default Nginx log directory **/var/log/nginx** is deleted, Nginx may fail to be started.

3. Run the following commands to delete historical records:

   **echo** **>** **/root/.bash_history**

   **history** **-c**
