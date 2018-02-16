.. highlight:: js

.. _calls-stationgetsurface-docs:

Station Get Surface
===================

Request
-------

``"station-get-surface"`` identifies the call as a station-get-surface call.

Define a rectangle on a map by providing two corners:

    1. Minimum latitude and longitude
    2. Maximum latitude and longitude

Fields
~~~~~~

user (optional)
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

min-lat
    Minimum latitude of the area you are querying (float).
max-lat
    Maximum latitude of the area you are querying (float).
min-long
    Minimum longitude of the area you are querying (float).
max-long
    Maximum longitude of the area you are querying (float).
filters
    An object to filter the response (object).

    Omit any filter you do not want to use in the request.

    Available Filters:

    excludes
        A list of station IDs to exclude from the result (array of integers).
    company-types
        A list of owner types of the charging stations (array of strings).

        E.g. ``"hotel"``.
    connector-types
        A list of connector types to filter for (array of strings).

        Allowed types are:

        * ``"Type2"``
        * ``"Combo"``
        * ``"Chademo"``
        * ``"Schuko"``
        * ``"Type3"``
        * ``"CeeBlue"``
        * ``"3PinSquare"``
        * ``"Type1"``
        * ``"CeeRed"``
        * ``"Cee2Poles"``
        * ``"Tesla"``
        * ``"Scame"``
        * ``"Nema5"``
        * ``"CeePlus"``
        * ``"T13"``
        * ``"T15"``
        * ``"T23"``
        * ``"Marechal"``
        * ``"TypeE"``

    connector-speeds-greater
        Minimum value for charging speed in kW (float).
    connector-speeds-less
        Maximum value for charging speed in kw (float).
    operator-ids
        List of charging station operator ids (array of integers).
    payable
        List of service providers that should be available (array of strings).

        Examples are

        * ``"PSA_EU"`` for PlugSurfing App payable
        * ``"PSC_EU"`` for PlugSurfing Charging Key payable

Response
--------

Fields
~~~~~~


stations
    An array of charging stations (objects).

    id
        The reponder's ID of the station (integer).

        Use this ID in the excludes filter (see request) or to get more details.
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

        * ``"Available"``
        * ``"Occupied"``
        * ``"Offline"``
        * ``null``

    owner-type
        The type of the company (string or ``null``).

        E.g. "hotel".
    last-static-change
        The last time the station was updated (string).

        The date/time format is RFC3339 (``Y-m-d\TH:i:sP``).

    connector-statuses
        Array of connectors' statuses (id (string): status (string)).

    connector-reservations (optional)
        Array of connectors' reservations (id (string): reservation (object)).

            reservation
                end
                    When this reservation ends (string; format RFC3339 ``"2016-05-09T04:08:06+02:00"``)
                own
                    If reservation by the user included in User request object. If request object isn't set this will default to false. (boolean)

HTTP Status codes
~~~~~~~~~~~~~~~~~

200 OK
    The request was processed successfully.

Result codes
~~~~~~~~~~~~
0
    Success

Examples
--------

Request::

    {
        "station-get-surface": {
            "min-lat": 0,
            "max-lat": 45,
            "min-long": 30,
            "max-long": 40,
            "filters": {
                "excludes": [
                    11131
                ],
                "company-types": [
                    "hotel"
                ],
                "connector-types": [
                    "Type2"
                ],
                "connector-speeds-greater": 3,
                "connector-speeds-less": 100,
                "operator-ids": [
                    122,
                    32
                ],
                "payable": [
                    "app",
                    "rfid"
                ]
            }
        }
    }

    {
        "station-get-surface": {
            "user": {
                "identifier-type": "username",
                "identifier": "john",
                "token": "b3853b6d910849f3b4392555b8acb984"
            },
            "min-lat": 0,
            "max-lat": 45,
            "min-long": 30,
            "max-long": 40,
            "filters": {
                "excludes": [
                    11131
                ],
                "company-types": [
                    "hotel"
                ],
                "connector-types": [
                    "Type2"
                ],
                "connector-speeds-greater": 3,
                "connector-speeds-less": 100,
                "operator-ids": [
                    122,
                    32
                ],
                "payable": [
                    "app",
                    "rfid"
                ]
            }
        }
    }

Response::

    {
        "stations": [
            {
                "id": 1169,
                "name": "Marktparkhaus am Südwall",
                "latitude": 51.516123,
                "longitude": 6.322554,
                "dynamic-status-summary": null,
                "owner-type": null,
                "last-static-change": "2017-01-13T18:07:23+01:00",
                "connector-statuses": {
                    "165946": "Available",
                    "165947": "Available"
                }
            },
            {
                "id": 1622,
                "name": "Markt",
                "latitude": 51.51599,
                "longitude": 6.322551,
                "dynamic-status-summary": null,
                "owner-type": null,
                "last-static-change": "2017-01-13T18:07:23+01:00",
                "connector-statuses": {
                    "142867": "Unknown"
                },
                "connector-reservations": {
                    "142867": {
                        "end": "2017-01-14T12:37:11+01:00",
                        "own": false
                    }
                }
            }
        ],
        "result": {
            "code": 0,
            "message": "Success."
        }
    }
