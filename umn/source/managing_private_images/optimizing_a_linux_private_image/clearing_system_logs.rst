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

3. Run the following commands to delete historical records:

   **echo** **>** **/root/.bash_history**

   **history** **-c**
