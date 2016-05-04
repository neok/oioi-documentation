.. highlight:: js

.. _calls-usergetrecentstations-docs:

User Logout
===========

Request
-------

``"user-get-recent-stations"`` identifies the call as a user-get-recent-stations call.

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

    identifier
        The identifier is something that uniquely identifies the customer,
        depending on the identifier-type (string).
    token (optional)
        A token can be used to authenticate the user (string).

        For example: if the identifier type is username and the identifier is the user's username,
        then token is used for authentication instead of a password.
limit
    Limit the response to this number of stations (integer).

Response
--------

Fields
~~~~~~

stations
    An array of stations (array of objects).

    id
        PlugSurfing's ID of the station (integer).

        Use this ID to get more details.
        See also :ref:`calls-stationgetbyids-docs`.
    name
        The name of the station, human readable (string).
    latitude
        Latitude of this station (float).
    longitude
        Longitude of this station (float).
    dynamic-status-summary
        Whether the station has available connectors (string).

        Can be one of:

        * ``"AVAILABLE"``
        * ``"OCCUPIED"``
        * ``"OFFLINE"``
        * ``null``

    owner-type
        The type of the company (string or ``null``).

        E.g. "hotel".


Status codes
~~~~~~~~~~~~

200 OK
    The request was processed successfully.
401 Unauthorized
    The username does not exist or the username and password/token did not match.

Examples
--------

Request::

    {
        "user-get-recent-stations": {
            "user": {
                "identifier-type": "username",
                "identifier": "youridentifier",
                "token": "87d4e3085af04671834ebeb127df33bf"
            },
            "limit": 2
        }
    }

Response::

    {
        "user": {
            "stations": [
                [
                    {
                        "id": 1247,
                        "name": "Vattenfall Ladestation",
                        "latitude": 52.52119,
                        "longitude": 13.32143,
                        "dynamic-status-summary": "AVAILABLE",
                        "owner-type": null
                    },
                    {
                        "id": 1248,
                        "name": "Hotel Station",
                        "latitude": 52.82119,
                        "longitude": 12.12143,
                        "dynamic-status-summary": "OCCUPIED",
                        "owner-type": "hotel"
                    }
                ]
            ]
        }
    }