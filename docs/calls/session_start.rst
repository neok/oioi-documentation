.. highlight:: js

Request/Response
================

``"session-start"`` identifies the call as a session-start call.

Request fields
--------------

user
   This field identifies the customer.
   The identifier is something that uniquely identifies the customer, depending on the identifier-type.
   The identifier field is of type string.
   The identifier-type can be one of:

   * ``"evco-id"``
   * ``"rfid"``
   * ``"username"``

   The token field is an optional field of type string and can be used to authenticate the user.
connector-id
   The EVSE ID that identifies the connector where the session should take place.
payment-reference (optional)
   Identifies the chosen payment reference the user wants to use to pay for this session.
   This field is of type string.

Response fields
---------------

success
   Whether or not the call was a success (of type boolean)
is-stoppable
   Indicates whether the session can be stopped via "session-stop" API call
session-id
   Optionally returned when a session can be stopped

Status codes
------------

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
