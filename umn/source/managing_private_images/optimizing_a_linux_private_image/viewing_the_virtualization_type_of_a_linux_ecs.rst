:original_name: en-us_topic_0037352185.html

.. _en-us_topic_0037352185:

Viewing the Virtualization Type of a Linux ECS
==============================================

You can run the following command to query the virtualization type of an ECS:

**lscpu**

If the value of **Hypervisor vendor** is **Xen**, the ECS uses Xen.

If the value of **Hypervisor vendor** is **KVM**, the ECS uses KVM.


.. figure:: /_static/images/en-us_image_0125146639.png
   :alt: **Figure 1** Viewing the virtualization type of a Linux ECS

   **Figure 1** Viewing the virtualization type of a Linux ECS
