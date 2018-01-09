.. highlight:: js

.. _calls-sessionstop-docs:

Session Stop
============

Request
-------

``"session-stop"`` identifies the call as a session-stop call.

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

        .. warning:: For a session stop request,
                     it is usually required that the ``"identifier-type"`` **must** be ``"evco-id"``.

    identifier
        The identifier is something that uniquely identifies the customer,
        depending on the identifier-type (string).
    token (optional)
        A token can be used to authenticate the user (string).

        For example: if the identifier type is username and the identifier is the user's username,
        then token is used for authentication instead of a password.
connector-id
   The EVSE ID that identifies the connector where the session should be stopped (string).
session-id (optional)
   A unique ID that identifies this session (string).

   .. warning:: Depending on the CPO's requirements, a ``session-id`` may be mandatory.

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
140
    Authentication failed: No positive authentication response
144
    Authentication failed: Email does not exist
145
    Authentication failed: User token not valid
181
    EVSE not found

Examples
--------

Request::

    {
        "session-stop": {
            "user": {
                "identifier-type": "evco-id",
                "identifier": "DE*8PS*123456*7"
            },
            "connector-id": "1356",
            "session-id": "dfdf"
        }
    }

Response::

    {
        "result": {
            "code": 0,
            "message": "Success."
        }
    }
