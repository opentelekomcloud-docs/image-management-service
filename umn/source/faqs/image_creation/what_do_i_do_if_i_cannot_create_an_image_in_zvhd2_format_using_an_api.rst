:original_name: en-us_topic_0096558549.html

.. _en-us_topic_0096558549:

What Do I Do If I Cannot Create an Image in ZVHD2 Format Using an API?
======================================================================

Symptom
-------

When you create a ZVHD2 image using an API, the image is created in the ZVHD format.

Solution
--------

Check whether your token contains the **op_gated_lld** role (**op_gated_lld** is the OBT tag, which can be viewed in the body of the response message of the API used to obtain a user token). The ZVHD2 image has the lazy loading feature. If the current environment does not support this feature or this feature is in the OBT phase, the ZVHD2 image will fail to be created.

Contact the customer service to ensure that the current environment supports lazy loading, obtain a new token, and use the new token to create an image.
