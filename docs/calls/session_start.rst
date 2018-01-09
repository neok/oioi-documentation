.. highlight:: js

.. _calls-sessionstart-docs:

Session Start
=============

Request
-------

``"session-start"`` identifies the call as a session-start call.

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

        .. warning:: For a session start request,
                     it is usually required that the ``"identifier-type"`` **must** be ``"evco-id"``.

    identifier
        The identifier is something that uniquely identifies the customer,
        depending on the identifier-type (string).
    token (optional)
        A token can be used to authenticate the user (string).

        For example: if the identifier type is username and the identifier is the user's username,
        then token is used for authentication instead of a password.
connector-id
   The EVSE ID that identifies the connector where the session should take place (string).
payment-reference (optional)
   Identifies the chosen payment reference the user wants to use to pay for this session (string).

Response
--------

Fields
~~~~~~

is-stoppable (optional)
   Indicates whether the session can be stopped via "session-stop" API call (boolean).
session-id (optional)
   The session id of the started session (string).

   .. warning:: Depending on the CPO's requirements, a ``session-id`` may be mandatory if the session is stoppable.

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
300
    CPO error
302
    CPO timeout
310
    EVSE error
312
    EVSE timeout
320
    EVSE already in use
321
    No EV connected to EVSE

Examples
--------

Request::

    {
       "session-start": {
           "user": {
               "identifier-type": "evco-id",
               "identifier": "DE*8PS*123456*7"
           },
           "connector-id": "1356",
           "payment-reference": "1212"
       }
    }

Response::

    {
        "result": {
            "code": 0,
            "message": "Success."
        }
    }

Stoppable response::

    {
        "session-start": {
            "session-id": "abcdef-123456-abc123-456def",
            "is-stoppable": true
        },
        "result": {
            "code": 0,
            "message": "Success."
        }
    }
