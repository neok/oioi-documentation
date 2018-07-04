.. highlight:: js

.. _calls-usermanagesubscription-docs:

User Manage Subscription
========================

With this request user can subscribe to one of available subscription plans or cancel already active subscription.

.. warning:: Cancelling user's active subscription means that subscription will not be renewed on the end of expiration
            date. Cancelled subscription will still be ACTIVE till the end of expiration date which is set based on subscription's
            plan duration (usually 6 or 12 months at minimum).

.. warning:: One user can only have one active subscription at the time.

Request
-------

``"user-manage-subscription"`` identifies the call as a user-manage-subscription call.

Fields
~~~~~~

user
    This field identifies the customer (object).

    identifier-type
        How to identify the user (string).

        The identifier-type can be one of:

        * ``"evco-id"``
        * ``"rfid"``
        * ``"username"``
        * ``"token"``

    identifier
        The identifier is something that uniquely identifies the customer,
        depending on the identifier-type (string).

    token (optional)
        A token can be used to authenticate the user (string).

        For example: if the identifier type is username and the identifier is the user's username,
        then token is used for authentication instead of a password.

id
    ID of Subscription Plan for which we want to start/cancel subscription (int).

cancel (optional)
    `false` or omitted if we want to subscribe. `true` if we want to cancel subscription (bool).


Response
--------

HTTP Status codes
~~~~~~~~~~~~~~~~~

200 OK
    The request was processed successfully.

Result codes
~~~~~~~~~~~~
0
    Success
100
    System error.
140
    Authentication failed: No positive authentication response
144
    Authentication failed: Email does not exist
145
    Authentication failed: User token not valid
180
    Entity not found.
185
    Subscription plan not found.
195
    User has already active rating subscription.

Examples
--------

Request::

    {
        "user-manage-subscription": {
            "user": {
                "identifier-type": "username",
                "identifier": "some_user",
                "token": "b3853b6d910849f3b4392555b8acb984"
            },
            "id": 1,
            "cancel": false
        }
    }

Response::

    {
      "result": {
        "code": 0,
        "message": "Success."
      }
    }
