:original_name: en-us_topic_0171668650.html

.. _en-us_topic_0171668650:

Creating a User and Granting Permissions
========================================

Scenarios
---------

This section describes how to use `Identity and Access Management <https://docs.otc.t-systems.com/identity-access-management/umn/service_overview/what_is_iam.html>`__ (IAM) to implement fine-grained permissions control over your images. With IAM, you can:

-  Create IAM users for employees based on the organizational structure of your enterprise. Each IAM user has their own identity credentials for accessing images.
-  Grant only the permissions required for users to perform a specific task.
-  Entrust an account or cloud service to perform professional and efficient O&M on your images.

If your account does not need individual IAM users for permissions management, you can skip this section.

This section uses the **IMS ReadOnlyAccess** permission as an example to describe how to grant permissions to a user. :ref:`Figure 1 <en-us_topic_0171668650__fig5293113815405>` shows the process.

Prerequisites
-------------

Learn about the permissions (see :ref:`IMS Permissions <en-us_topic_0171668647__section2091762218354>`) supported by IMS. For the system permissions of other services, see `Permissions <https://docs.otc.t-systems.com/identity-access-management/permissions/permissions.html>`__.

Process Flow
------------

.. _en-us_topic_0171668650__fig5293113815405:

.. figure:: /_static/images/en-us_image_0221322139.png
   :alt: **Figure 1** Process for granting IMS permissions

   **Figure 1** Process for granting IMS permissions

#. .. _en-us_topic_0171668650__li2021991142518:

   `Create a user group and grant permissions to it <https://docs.otc.t-systems.com/identity-access-management/umn/getting_started/creating_a_user_group_and_assigning_permissions.html>`__.

   Create a user group on the IAM console, and grant the read-only permission to the group by assigning the **IMS ReadOnlyAccess** permission.

#. `Create an IAM user and add it to the user group <https://docs.otc.t-systems.com/identity-access-management/umn/getting_started/creating_a_user_and_adding_the_user_to_a_user_group.html>`__.

   Create a user on the IAM console and add the user to the group created in :ref:`1 <en-us_topic_0171668650__li2021991142518>`.

#. Log in and verify permissions.

   Log in to the management console using the IAM user, switch to a region where the permissions take effect, and verify the permissions (assume that the user has only the **IMS ReadOnlyAccess** permission).

   -  In the **Service List**, choose **Image Management Service**. On the IMS console, perform operations except querying images, such as creating, modifying, and deleting an image.

      For example, click **Create Private Image** in the upper right corner. If you are prompted insufficient permissions, the **IMS ReadOnlyAccess** permission has taken effect.

   -  Choose any other service in the **Service List**, such as **Virtual Private Cloud**. If a message appears indicating insufficient permissions to access the service, the **IMS ReadOnlyAccess** permission has taken effect.
