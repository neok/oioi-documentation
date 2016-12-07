.. highlight:: js

.. _calls-stationpost-docs:

Station Post
============

.. warning:: It is not allowed to change the connectors of an existing station.

.. warning:: The station's connectors' IDs may not be changed once it is created.

You have to send one request for each station.
It is not possible to send multiple stations with one request.

.. note:: To ensure very high data quality, PlugSurfing manually curates all charging station and connector data.
          This means that data on the PlugSurfing platform may not correspond 100% to the data you push.

          Furthermore, PlugSurfing groups stations to simplify access from clients like the PlugSurfing app.
          As a result, multiple stations you push may show as a single station on the PlugSurfing platform,
          with all connectors from all individual stations associated to the grouped station.

Request
-------

``"station-post"`` identifies the call as a station-post call.

Fields
~~~~~~

station
    An object that holds the station data. Fields of a station are:

    id
        An identifier that uniquely identifies the station (string).

        .. important:: Every station id must be globally unique.

    name
        The name is shown to the EV driver (string).
    description (optional)
        A more detailed description of the station (string).
    latitude
        Latitude of the station (float).
    longitude
        Longitude of the station (float).
    address
        The address helps EV drivers locate the station (object).

        street
            string
        street-number
            string
        city
            string
        zip
            string
        country
            string

            Format: international two-letter codes in accordance with `ISO 3166-1 alpha-2`_.

    contact
        object

        phone
            string
        fax (optional)
            string
        website (optional)
            string
        email (optional)
            string

    cpo-id
        The EVSE identifier, e.g. ``DE*8PS``, of the CPO of the charging station (string).
    is-open-24
        Whether or not the station is always accessible (24 hours per day) (boolean).
    connectors
        array of objects

        All the connectors belonging to this station:

            id
                The EVSE ID of the conncetor (string).

                See also :ref:`EVSE <glossary-evse>`.

                .. important:: The id of every connector must be globally unique.

            name
                The name of the type of connector (string).

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

                If your type is missing, please do not hesitate to contact PlugSurfing.
            speed
                Speed in kW (float).

    open-hour-notes (optional)
        An array of objects containing certain opening periods:

            times
                Opening and closing time (array of strings).
            days
                Weekdays when the interval starts and ends (array of two strings).

                Both are the same if it is for one specific day only.

            Example::

                {
                    "open-hour-notes": [
                        {
                            "times": [
                                "07:30",
                                "19:00"
                            ],
                            "days": [
                                "Mo",
                                "Fr"
                            ]
                        },
                        {
                            "times": [
                                "09:00",
                                "15:00"
                            ],
                            "days": [
                                "Sa",
                                "Sa"
                            ]
                        }
                    ]
                }

            This example means the following:
            For the interval Monday to Friday, the station is open from 07:30 to 19:00.
            On Saturday, the station is open from 09:00 to 15:00.

    notes (optional)
        Additional notes, for example how to find the station (string).
    is-reservable (optional)
        boolean
    floor-level (optional)
        On which floor the station is located, for example in a parking house (integer).
    is-free-charge (optional)
        Whether charging can be done without cost (boolean).
    total-parking (optional)
        The number of parking spots that are available at the station (integer).
    is-green-power-available (optional)
        boolean
    is-plugin-charge (optional)
        Whether or not a user can authorize with the proprietary "Plugin-Charge" method (boolean).
    is-roofed (optional)
        Whether the station is under a roof, for example in a parking garage (boolean).
    is-private (optional)
        Whether the station is privately owned (boolean).

        This has multiple implications depending on the connected partner and the station won't show up everywhere on their platforms.
        For details, please contact the connected partner.
    deleted
        Soft delete the station and its related connectors (boolean).

partner-identifier
    The partner identifier of the partner that shall be associated with this station.
    See also :ref:`partner identifier <glossary-partner-identifier>`

Response
--------

Fields
~~~~~~

success
    Whether or not the call was a success (of type boolean)

Examples
--------

Request::

    {
        "station-post": {
            "station": {
                "id": "abcdef-12345",
                "name": "test",
                "description": "Nice station!",
                "latitude": 1.123,
                "longitude": 2.345,
                "address": {
                    "street": "streetname",
                    "street-number": "123a",
                    "city": "Berlin",
                    "zip": "10243",
                    "country": "DE"
                },
                "contact": {
                    "phone": "+49 30 8122321",
                    "fax": "+49 30 8122322",
                    "web": "www.example.com",
                    "email": "contact@example.com"
                },
                "cpo-id": "DE*8PS",
                "is-open-24": false,
                "connectors": [
                    {
                        "id": "DE*8PS*E123456",
                        "name": "Schuko",
                        "speed": 3.7
                    },
                    {
                        "id": "DE*8PS*E123457",
                        "name": "Type2",
                        "speed": 11.1
                    }
                ],
                "open-hour-notes": [
                    {
                        "times": [
                            "07:30",
                            "19:00"
                        ],
                        "days": [
                            "Mo",
                            "Fr"
                        ]
                    },
                    {
                        "times": [
                            "09:00",
                            "15:00"
                        ],
                        "days": [
                            "Sa",
                            "Sa"
                        ]
                    }
                ],
                "notes": "Additional info.",
                "is-reservable": false,
                "floor-level": 1,
                "is-free-charge": false,
                "total-parking": 2,
                "is-green-power-available": false,
                "is-plugin-charge": false,
                "is-roofed": false,
                "is-private": false,
                "deleted": true
            },
            "partner-identifier": "1"
        }
    }

Response ::

    {
        "station-post": {
            "success": true
        }
    }

.. _iso 3166-1 alpha-2: https://en.wikipedia.org/wiki/ISO_3166-1_alpha-2
