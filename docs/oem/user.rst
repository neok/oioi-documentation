.. _oem-user-docs:

Managing Users
==============
As an OEM you can manage your users on the platform.
For example registration and log-in.

After user registration or log-in, you will get a token in the response.
That token will be used in future calls to authenticate the user,
so that your application does not store any user passwords.

.. _oem-user-register-docs:

Register Users
--------------
To register a new user on the platform, send this call.

* **Role:** Sender
* **Implementation:** :ref:`calls-userregister-docs`

.. _oem-user-verification-docs:

Verify Users (Log-In)
---------------------------------
If you want to verify an existing user by asking for the password,
you can use this call.

* **Role:** Sender
* **Implementation:** :ref:`calls-userverify-docs`

.. _oem-user-details-docs:

User Details
------------
If you want to manage additional user data, like for example the address,
you can send that data to the platform.

* **Role:** Sender
* **Implementation:** :ref:`calls-userpostdetails-docs`

Later it is possible to get the data, e.g. for displaying in an app.

* **Role:** Sender
* **Implementation:** :ref:`calls-usergetdetails-docs`

.. _oem-user-rfids-docs:

RFID Management
---------------
To register a new RFID medium for a user, do the following.

* **Role:** Sender
* **Implementation:** :ref:`calls-useraddrfid-docs`

It is possible that a user lost the RFID medium and wants to block it.
This call allows a user to do so.

* **Role:** Sender
* **Implementation:** :ref:`calls-userblockrfid-docs`

.. note:: It may take up to 24h until the block has propagated throughout all networks.
