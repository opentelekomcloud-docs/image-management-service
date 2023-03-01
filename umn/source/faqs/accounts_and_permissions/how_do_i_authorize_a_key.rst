:original_name: en-us_topic_0133773781.html

.. _en-us_topic_0133773781:

How Do I Authorize a Key?
=========================

Scenarios
---------

To share an encrypted image, you need to authorize the key used for encrypting the image. This section describes how to authorize a key.

.. note::

   The key can only be a custom key. The default key cannot be authorized.

Prerequisites
-------------

You have confirmed the key to be authorized. (You can view **KMS Key Name** on the image details page).

Procedure
---------

#. Log in to the management console and choose **Security** > **Key Management Service**.
#. On the **Custom Keys** tab, click the alias of the target key to go to the key details page.
#. On the **Grants** tab, click **Create Grant**, and set the following parameters.

   -  **User or Tenant**: Select **Tenant** and enter the tenant ID. You can obtain the tenant ID from **Account ID** on the **My Credentials** page.
   -  **Granted Operations**: **Decrypt Data Key** and **Describe Key** are mandatory. Others are optional.

#. Click **OK**.
