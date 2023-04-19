:original_name: en-us_topic_0171668647.html

.. _en-us_topic_0171668647:

Permissions
===========

If you need to grant different permissions to employees in your enterprise to access your IMS resources, IAM is a good choice for fine-grained permissions management. IAM provides identity authentication, permissions management, and access control, helping you secure access to your resources.

With IAM, you can use your account to create IAM users for your employees, and grant permissions to the users to control their access to specific resource types. For example, some software developers in your enterprise need to use IMS resources but must not delete them or perform any high-risk operations. To achieve this result, you can create IAM users for the software developers and grant them only the permissions required for using IMS resources.

If your account does not require individual IAM users for permissions management, skip this section.

IAM can be used free of charge. You pay only for the resources in your account. For more information about IAM, see `IAM Service Overview <https://docs.otc.t-systems.com/identity-access-management/umn/service_overview/what_is_iam.html#iam-01-0026>`__.

.. _en-us_topic_0171668647__section2091762218354:

IMS Permissions
---------------

By default, new IAM users do not have any permissions assigned. You need to add a user to one or more groups, and assign policies or roles to these groups. The user then inherits permissions from the groups it is a member of. This process is called authorization. After authorization, the user can perform specified operations on cloud services based on the permissions.

IMS is a project-level service deployed and accessed in specific physical regions. When you grant IMS permissions to a user group, set **Scope** to **Region-specific projects** and then select projects for the permissions to take effect. If you select **All projects**, the permissions will take effect for the user group in all region-specific projects. Before you access IMS, switch to a region where you have been authorized to use IMS.

You can grant user permissions by using roles and policies.

-  Roles: A type of coarse-grained authorization mechanism that defines permissions related to user responsibilities. This mechanism provides only a limited number of service-level roles for authorization. When using roles to grant permissions, you need to also assign other roles on which the permissions depend to take effect. However, roles are not an ideal choice for fine-grained authorization and secure access control.

   .. table:: **Table 1** System-defined IMS roles

      +----------------------+-------------------------------------------------------------------------------+--------------------------------------------------------------------------+
      | Role                 | Description                                                                   | Dependency                                                               |
      +======================+===============================================================================+==========================================================================+
      | IMS Administrator    | Administrator permissions for IMS                                             | This role depends on the **Tenant Administrator** role.                  |
      +----------------------+-------------------------------------------------------------------------------+--------------------------------------------------------------------------+
      | Server Administrator | Permissions for creating, deleting, querying, modifying, and uploading images | This role depends on the **IMS Administrator** role in the same project. |
      +----------------------+-------------------------------------------------------------------------------+--------------------------------------------------------------------------+

-  Policies (recommended): A type of fine-grained authorization mechanism that defines permissions required to perform operations on specific cloud resources under certain conditions. This mechanism allows for more flexible policy-based authorization, meeting requirements for secure access control. For example, you can grant IMS users only the permissions for managing a certain type of image resources.

   Most policies define permissions based on APIs. For the API actions supported by IMS, see "Permission Policies and Supported Actions" in *Elastic Cloud Server API Reference*.

   .. table:: **Table 2** System-defined IMS policies

      +--------------------+----------------------------------------------------------------------------------------+------------+
      | Policy             | Description                                                                            | Dependency |
      +====================+========================================================================================+============+
      | IMS FullAccess     | All permissions of IMS                                                                 | None       |
      +--------------------+----------------------------------------------------------------------------------------+------------+
      | IMS ReadOnlyAccess | Read-only permissions for IMS. Users granted these permissions can only view IMS data. | None       |
      +--------------------+----------------------------------------------------------------------------------------+------------+

:ref:`Table 3 <en-us_topic_0171668647__table1131314508337>` lists common operations and their required system-defined IMS permissions.

.. _en-us_topic_0171668647__table1131314508337:

.. table:: **Table 3** Common operations and required system-defined permissions

   +----------------------------+----------------+--------------------+-------------------------------------------------------+
   | Action                     | IMS FullAccess | IMS ReadOnlyAccess | IMS Administrator (Depending on Tenant Administrator) |
   +============================+================+====================+=======================================================+
   | Creating an image          | Y              | x                  | Y                                                     |
   +----------------------------+----------------+--------------------+-------------------------------------------------------+
   | Deleting an image          | Y              | x                  | Y                                                     |
   +----------------------------+----------------+--------------------+-------------------------------------------------------+
   | Querying an image          | Y              | Y                  | Y                                                     |
   +----------------------------+----------------+--------------------+-------------------------------------------------------+
   | Updating image information | Y              | x                  | Y                                                     |
   +----------------------------+----------------+--------------------+-------------------------------------------------------+

Helpful Links
-------------

-  `What Is IAM? <https://docs.otc.t-systems.com/identity-access-management/umn/service_overview/what_is_iam.html#iam-01-0026>`__
