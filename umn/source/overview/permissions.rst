:original_name: en-us_topic_0171668647.html

.. _en-us_topic_0171668647:

Permissions
===========

If you need to assign different permissions to personnel in your enterprise to access your images, Identity and Access Management (IAM) is a good choice for fine-grained permissions management. IAM provides identity authentication, permissions management, and access control, helping you secure access to your resources.

With IAM, you can create IAM users and assign permissions to control their access to specific resources. For example, if you want some software developers in your enterprise to use images but do not want them to delete the images or perform any other high-risk operations, you can create IAM users and grant permission to use the images but not permission to delete them.

If your account does not require individual IAM users for permissions management, you can skip this section.

IAM is a free service. You pay only for the resources in your account. For more information about IAM, see `IAM Service Overview <https://docs.otc.t-systems.com/identity-access-management/umn/service_overview/what_is_iam.html#iam-01-0026>`__.

.. _en-us_topic_0171668647__section2091762218354:

IMS Permissions
---------------

New IAM users do not have any permissions assigned by default. You need to first add them to one or more groups and attach policies or roles to these groups. The users then inherit permissions from the groups and can perform specified operations on cloud services based on the permissions they have been assigned.

IMS is a project-level service deployed for specific regions. When you set **Scope** to **Region-specific projects** and select the specified projects in the specified regions, the users only have permissions for images in the selected projects. If you set **Scope** to **All resources**, the users have permissions for images in all region-specific projects. When accessing IMS, the users need to switch to the authorized region.

You can grant permissions by using roles and policies.

-  Roles: A coarse-grained authorization strategy provided by IAM to assign permissions based on users' job responsibilities. Only a limited number of service-level roles are available for authorization. Cloud services depend on each other. When you grant permissions using roles, you also need to attach any existing role dependencies. Roles are not ideal for fine-grained authorization and least privilege access.

   .. table:: **Table 1** System-defined IMS roles

      +----------------------+-------------------------------------------------------------------------------+--------------------------------------------------------------------------+
      | Role                 | Description                                                                   | Dependencies                                                             |
      +======================+===============================================================================+==========================================================================+
      | IMS Administrator    | Administrator permissions for IMS                                             | This role depends on the **Tenant Administrator** role.                  |
      +----------------------+-------------------------------------------------------------------------------+--------------------------------------------------------------------------+
      | Server Administrator | Permissions for creating, deleting, querying, modifying, and uploading images | This role depends on the **IMS Administrator** role in the same project. |
      +----------------------+-------------------------------------------------------------------------------+--------------------------------------------------------------------------+

-  Policies (recommended): A fine-grained authorization strategy that defines permissions required to perform operations on specific cloud resources under certain conditions. This type of authorization is more flexible and is ideal for least privilege access. For example, you can grant users only the permission to manage images of a certain type.

   A majority of fine-grained policies contain permissions for specific APIs, and permissions are defined using API actions. For the API actions supported by IMS, see "Permissions and Supported Actions" in *Elastic Cloud Server API Reference*.

   .. table:: **Table 2** System-defined policies for IMS

      +--------------------+-------------------------------------------------------------------------------------+--------------+
      | Policy             | Description                                                                         | Dependencies |
      +====================+=====================================================================================+==============+
      | IMS FullAccess     | All permissions for IMS                                                             | None         |
      +--------------------+-------------------------------------------------------------------------------------+--------------+
      | IMS ReadOnlyAccess | Read-only permissions for IMS. Users with these permissions can only view IMS data. | None         |
      +--------------------+-------------------------------------------------------------------------------------+--------------+

:ref:`Table 3 <en-us_topic_0171668647__table1131314508337>` lists the common operations supported by system-defined permissions for IMS.

.. _en-us_topic_0171668647__table1131314508337:

.. table:: **Table 3** Common operations supported by system-defined permissions

   +----------------------------+----------------+--------------------+-------------------------------------------------------+
   | Operation                  | IMS FullAccess | IMS ReadOnlyAccess | IMS Administrator (Depending on Tenant Administrator) |
   +============================+================+====================+=======================================================+
   | Creating images            | Y              | x                  | Y                                                     |
   +----------------------------+----------------+--------------------+-------------------------------------------------------+
   | Deleting images            | Y              | x                  | Y                                                     |
   +----------------------------+----------------+--------------------+-------------------------------------------------------+
   | Querying images            | Y              | Y                  | Y                                                     |
   +----------------------------+----------------+--------------------+-------------------------------------------------------+
   | Updating image information | Y              | x                  | Y                                                     |
   +----------------------------+----------------+--------------------+-------------------------------------------------------+

Helpful Links
-------------

-  `What Is IAM? <https://docs.otc.t-systems.com/identity-access-management/umn/service_overview/what_is_iam.html#iam-01-0026>`__
