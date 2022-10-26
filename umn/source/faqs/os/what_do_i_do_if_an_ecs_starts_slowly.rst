:original_name: en-us_topic_0117142739.html

.. _en-us_topic_0117142739:

What Do I Do If an ECS Starts Slowly?
=====================================

Symptom
-------

If an ECS starts slowly, you can change the default timeout duration to speed up the startup.

Solution
--------

#. Log in to the ECS.

#. Run the following command to switch to user **root**:

   **sudo su**

#. Run the following command to query the version of the GRUB file:

   **rpm -qa \| grep grub**


   .. figure:: /_static/images/en-us_image_0251959651.png
      :alt: **Figure 1** Querying the GRUB file version

      **Figure 1** Querying the GRUB file version

#. Set **timeout** in the GRUB file to **0**.

   -  If the GRUB file version is earlier than 2:

      Open **/boot/grub/grub.cfg** or **/boot/grub/menu.lst** and set **timeout** to **0**.

   -  If the GRUB file version is 2:

      Open **/boot/grub2/grub.cfg** and set the value of **timeout** to **0**.


      .. figure:: /_static/images/en-us_image_0207619609.jpg
         :alt: **Figure 2** Modifying the timeout duration

         **Figure 2** Modifying the timeout duration
