.. highlight:: js

.. _calls-usergetrecentsessions-docs:

User Get Recent Sessions
========================

Request
-------

``"user-get-recent-sessions"`` identifies the call as a user-get-recent-sessions call.

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

Response
--------

Fields
~~~~~~
Optional fields may be omitted or have the value ``null``.

sessions
    An array of sessions (array of objects).

    request-sent (optional)
        The date/time at which the session was requested by the user (string; format: ``"2014-06-23T18:32:49+02:00"``).
    connector-id (optional)
        Internal database ID of the related connector (integer).
    charging-station-id (optional)
        Internal database ID of the related charging station (integer).
    session-interval
        Start and end time of the session (object).

        The session interval is the time between connecting the car to the station and disconnecting.

        start (optional)
            The date/time at which the session was started (string; format: ``"2014-06-23T18:32:49+02:00"``).
        end (optional)
            The date/time at which the session was stopped (string; format: ``"2014-06-23T18:32:49+02:00"``).
    charging-interval
        Start and end time of charging (object).

        The charging interval is the time between the first and the last time that energy was transferred to the car.

        start (optional)
            The date/time at which charging started (string; format: ``"2014-06-23T18:32:49+02:00"``).
        end (optional)
            The date/time at which charging stopped (string; format: ``"2014-06-23T18:32:49+02:00"``).
    energy-consumed (optional)
        The consumed energy in kWh (float).
    cost
        The total cost of the session (string).
    currency
        Currency of the cost (string).
    external-session-id (optional)
        The session ID at the CPO (string).
    address (optional)
        The address where the session took place (string).


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

Examples
--------

Request::

    {
        "user-get-recent-sessions": {
            "user": {
                "identifier-type": "username",
                "identifier": "youridentifier",
                "token": "87d4e3085af04671834ebeb127df33bf"
            }
        }
    }

Response::

    {
        "user": {
            "sessions": [
                {
                    "request-sent": "2014-06-23T18:32:49+02:00",
                    "connector-id": 9835,
                    "charging-station-id": 19018,
                    "session-interval": {
                        "start": "2014-06-23T16:32:22+02:00",
                        "end": "2014-06-23T17:42:47+02:00"
                    },
                    "charging-interval": {
                        "start": "2014-06-23T16:32:28+02:00",
                        "end": "2014-06-23T17:30:21+02:00"
                    },
                    "energy-consumed": 3,
                    "cost": "3.76",
                    "currency": "EUR",
                    "external-session-id": "abc-def",
                    "address": "Tempelhofer Ufer 17, 10963 Berlin, Germany"
                },
                {
                    "request-sent": "2014-06-23T18:40:50+02:00",
                    "connector-id": null,
                    "charging-station-id": null,
                    "session-interval": {
                        "start": "2014-06-23T16:38:18+02:00",
                        "end": "2014-06-23T16:40:45+02:00"
                    },
                    "charging-interval": {
                        "start": null,
                        "end": null
                    },
                    "energy-consumed": 0.053,
                    "cost": "2.03",
                    "currency": "EUR",
                    "external-session-id": "abc-def",
                    "address": "Tempelhofer Ufer 17, 10963 Berlin, Germany"
                }
            ]
        },
        "result": {
            "code": 0,
            "message": "Success."
        }
    }
