.. highlight:: js

Request/Response
================

``"station-post"`` identifies the call as a station-post call.

.. warning:: It is not allowed to change the connectors of an existing station.

.. warning:: The station's connectors' IDs may not be changed once it is created.

Request fields
--------------

station
    An object that holds the station data. Fields of a station are:

    id
        string, mandatory

        An identifier that uniquely identifies the station in your system.
    name
        string, mandatory

        The name is shown to the EV driver.
    description
        string, optional

        A more detailed description of the station.
    latitude
        float, mandatory
    longitude
        float, mandatory
    address
        object, mandatory
        The address helps EV drivers locate the station.

        street
            string, mandatory
        street-number
            string, mandatory
        city
            string, mandatory
        zip
            string, mandatory
        country
            string, mandatory

            Format: international two letter codes (``ISO 3166-1 alpha-2``).

    contact
        object, mandatory

        phone
            string, mandatory
        fax
            string, optional
        website
            string, optional
        email
            string, optional

    cpo-id
        string, mandatory

        The EVSE identifier, e.g. ``+49*8PS``, of the CPO of the charging station.
    is-open-24
        boolean, mandatory

        Whether or not the station is always accessible (24 hours per day).
    connectors
        array of objects, mandatory

        All the connectors belonging to this station:

            id
                string, mandatory

                The EVSE ID of the conncetor.
                See also :ref:`EVSE <glossary-evse>`.
            name
                string, mandatory

                The name of the type of connector.
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

                If your type is missing, please do not hesitate to contact PlugSurfing.
            speed
                float, mandatory

                Speed in kilowatts (e.g. ``3.7``).

    open-hour-notes
        array of objects, optional

        An array of objects containing certain opening periods:

            times
                string, mandatory

                An array of two strings. Opening and closing time.
            days
                array of two strings, mandatory

                Weekdays when the interval starts and ends.
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

    notes
        string, optional

        Additional notes, for example how to find the station.
    is-reservable
        boolean, optional
    floor-level
        integer, optional

        On which floor the station is located, for example in a parking house.
    is-free-charge
        boolean, optional

        Whether charging can be done without cost.
    total-parking
        integer, optional

        The number of parking spots that are available at the station.
    is-green-power-available
        boolean, optional
    is-plugin-charge
        boolean, optional
    is-roofed
        boolean, optional
    is-private
        boolean, optional

        Whether the station is privately owned.
        This has multiple implications and the station won't show up everywhere on the PlugSurfing platforms.
        For details, please contact PlugSurfing.
    deleted
        boolean, optional

        Soft delete the station and its related connectors

partner-identifier
    The partner identifier of the partner that shall be associated with this station.
    See also :ref:`partner identifier <glossary-partner-identifier>`

Response fields
---------------

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
                    "street-number": 123,
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
                "cpo-id": "+49*8PS",
                "is-open-24": false,
                "connectors": [
                    {
                        "id": "+49*8PS*E123456",
                        "name": "Schuko",
                        "speed": 3.7
                    },
                    {
                        "id": "+49*8PS*E123457",
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
                "notes": false,
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
