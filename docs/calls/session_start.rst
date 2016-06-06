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

        .. note:: For session-start and session-stop it is common to use ``"evco-id"`` as the identifier-type.

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

success
   Whether or not the call was a success (boolean).
is-stoppable (optional)
   Indicates whether the session can be stopped via "session-stop" API call (boolean).
session-id (optional)
   The session id of the started session (string).

   .. warning:: Depending on the CPO's requirements, a ``session-id`` may be mandatory if the session is stoppable.

Status codes
~~~~~~~~~~~~

200 OK
   Request was processed successfully
401 Unauthorized
   The token, username or identifier type were incorrect
404 Not found
   A connector could not be found by the supplied identifier

Examples
--------

Request::

    {
       "session-start": {
           "user": {
               "identifier-type": "username",
               "identifier": "youridentifier",
               "token": "87d4e3085af04671834ebeb127df33bf"
           },
           "connector-id": "1356",
           "payment-reference": "1212"
       }
    }

Response::

    {
        "session-start": {
            "success": true
        }
    }
