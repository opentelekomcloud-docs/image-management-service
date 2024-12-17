:original_name: en-us_topic_0171668651.html

.. _en-us_topic_0171668651:

Creating a Custom Policy
========================

Scenarios
---------

Custom policies can be created as a supplement to the system permissions of IMS. For the actions supported for custom policies, see "Permissions Policies and Supported Actions" in *Image Management Service API Reference*.

You can create custom policies in either of the following two ways:

-  Visual editor: Select cloud services, actions, resources, and request conditions without the need to know policy syntax.
-  JSON: Edit JSON policies from scratch or based on an existing policy.

For details, see "Creating a Custom Policy" in *Identity and Access Management User Guide*. This section provides examples of common IMS custom policies.

Example Policies
----------------

-  Example 1: Allowing users to create images

   .. code-block::

      {
          "Version": "1.1",
          "Statement": [
              {
                  "Effect": "Allow",
                  "Action": [
                      "ims:serverImages:create"
                  ]
              },
              {
                  "Effect": "Allow",
                  "Action": [
                      "KMS:*:*"
                  ]
              },
              {
                  "Effect": "Allow",
                  "Action": [
                      "ecs:cloudServers:get",
                      "ecs:servers:get",
                      "ecs:serverVolumes:use",
                      "ecs:cloudServers:list",
                      "ecs:serverVolumeAttachments:list",
                      "ecs:servers:list"

                  ]
              },
              {
                  "Effect": "Allow",
                  "Action": [
                      "bms:servers:list",
                      "bms:servers:get",
                      "bms:serverFlavors:get"
                  ]
              },
             {
                  "Effect": "Allow",
                  "Action": [
                      "evs:volumes:*"
                  ]
              }
          ]
      }
      {
          "Version": "1.1",
          "Statement": [
              {
                  "Effect": "Allow",
                  "Action": [
                      "OBS:*:*"
                  ]
              }
          ]
      }

   .. note::

      The action required for creating an image is **ims:serverImages:create**. Others are dependent actions for creating an image.

-  Example 2: Denying image deletion

   A deny policy must be used in conjunction with other policies to take effect. If the policies assigned to a user contain both Allow and Deny actions, the Deny actions take precedence over the Allow actions.

   The following method can be used if you need to assign the **IMS FullAccess** policy to a user but also forbid the user from deleting images. Create a custom policy for denying image deletion, and assign both the policies to the group the user belongs to. Then, the user can perform all operations on IMS except deleting images. The following is an example deny policy:

   .. code-block::

      {
          "Version": "1.1",
          "Statement": [
              {
                  "Effect": "Deny",
                  "Action": [
                      "ims:images:delete"
                  ]
              }
          ]
      }
