:original_name: en-us_topic_0000002294300328.html

.. _en-us_topic_0000002294300328:

Configuring Event Alarm Notifications
=====================================

You can use Cloud Eye to monitor IMS. After IMS event notifications are configured, a notification will be sent when an image is created, updated, or deleted.

.. note::

   Notifications are sent by the Simple Message Notification (SMN) service, which will incur charges.


Configuring Event Alarm Notifications
-------------------------------------

#. Log in to the management console.

#. Click |image1| in the upper left corner of the page. In the navigation pane on the left, choose **Management & Deployment** > **Cloud Eye**.

#. Use either of the methods:

   Method 1: In the navigation pane, choose **Event Monitoring**.

   Method 2: In the navigation pane, choose **Alarm Management** > **Alarm Rules**.

#. In the upper right corner, click **Create Alarm Rule**.

#. Set alarm parameters by referring to :ref:`Table 1 <en-us_topic_0000002294300328__table11241524115310>`.

   .. _en-us_topic_0000002294300328__table11241524115310:

   .. table:: **Table 1** Parameter description

      +-----------------------------------+-----------------------------------------------------------------------------------------------------------------------------------------------+
      | Parameter                         | Description                                                                                                                                   |
      +===================================+===============================================================================================================================================+
      | Name                              | Name of the rule. The system generates a random name and you can modify it.                                                                   |
      +-----------------------------------+-----------------------------------------------------------------------------------------------------------------------------------------------+
      | Description                       | Description of the alarm rule.                                                                                                                |
      +-----------------------------------+-----------------------------------------------------------------------------------------------------------------------------------------------+
      | Alarm Type                        | Select **Event**.                                                                                                                             |
      +-----------------------------------+-----------------------------------------------------------------------------------------------------------------------------------------------+
      | Event Type                        | Select **System event**.                                                                                                                      |
      +-----------------------------------+-----------------------------------------------------------------------------------------------------------------------------------------------+
      | Event Source                      | Select **Image Management Service**.                                                                                                          |
      +-----------------------------------+-----------------------------------------------------------------------------------------------------------------------------------------------+
      | Monitoring Scope                  | Specify the resource scope that the alarm rule will apply to.                                                                                 |
      +-----------------------------------+-----------------------------------------------------------------------------------------------------------------------------------------------+
      | Method                            | Use the default value **Configure manually**.                                                                                                 |
      +-----------------------------------+-----------------------------------------------------------------------------------------------------------------------------------------------+
      | Alarm Policy                      | Configure a policy for triggering an alarm. You can configure a policy for triggering an alarm when an image is created, updated, or deleted. |
      +-----------------------------------+-----------------------------------------------------------------------------------------------------------------------------------------------+
      | Alarm Notification                | Specifies whether to send alarm notifications. Select an option based on your requirements.                                                   |
      |                                   |                                                                                                                                               |
      |                                   | .. note::                                                                                                                                     |
      |                                   |                                                                                                                                               |
      |                                   |    Alarm messages are sent by SMN, which may incur a small charge.                                                                            |
      +-----------------------------------+-----------------------------------------------------------------------------------------------------------------------------------------------+

#. Click **Create**.

   After the alarm rule is created, the **Alarm Rules** page is displayed, showing the new alarm rule.

.. |image1| image:: /_static/images/en-us_image_0000002335922469.png
