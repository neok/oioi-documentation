.. highlight:: js

.. _calls-stationgetbyids-docs:

Station Get By IDs
==================

Request
-------

``"station-get-by-ids"`` identifies the call as a station-get-by-ids call.

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

station-ids
    An array of IDs (integers).

    The maximum number of IDs per call is ten.

Response
--------

Fields
~~~~~~
Optional fields may be omitted or have the value ``null``.

stations
    An array of charging stations (objects).

    id
        The responder's internal ID of the station (integer)
    address (optional)
        street (optional)
            string
        street-number (optional)
            string
        city (optional)
            string
        zip (optional)
            string
        country (optional)
            string
    contact (optional)
        email (optional)
            string
        web (optional)
            string
        phone (optional)
            string
        fax (optional)
            string
    operator-company-id (optional)
        The CPO of the charging station.

        The charge point operator is the company responsible for the functioning of the station.
        Access to the station usually also goes through the CPO.
    operator-logo (optional)
        URL to the logo image (string).
    floor-level (optional)
        On which floor the station is located, for example in a parking house (integer).
    is-free-charge
        Whether charging can be done without cost (boolean).
    last-static-change (optional)
        string (format: ``"2016-05-09T04:08:06+02:00"``)
    last-dynamic-change (optional)
        string (format: ``"2016-05-09T04:08:06+02:00"``)
    name
        string
    description (optional)
        string
    latitude
        float
    longitude
        float
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
    total-parking
        The number of parking spots that are available at the station (integer).
    notes (optional)
        Additional notes, for example how to find the station (string).
    is-green-power-available
        boolean
    is-plugin-charge
        boolean
    is-roofed
        boolean
    is-reservable
        boolean
    has-dynamic-info
        boolean
    is-open-24
        boolean
    dynamic-status-summary (optional)
        Whether the station is currently available (string).

        One of:

        * ``"Available"``
        * ``"Occupied"``
        * ``"Reserved"``
        * ``"Offline"``
        * ``"Unknown"``

    is-validated
        boolean
    is-private
        Whether the station is privately owned (boolean).

        For details, please contact the connected partner.
    owner-company-id (optional)
        The owner of the charging station.

        The owner is usually either the CPO or something like a restaurant or Ikea, owning the stations on their property.
    service-providers (optional)
        An array of all service providers of the charging station.

        A service provider is a company that grants access to a charging station.
        See :ref:`EMP <glossary-emp>`.
    connectors (optional)
        id
            The responder's internal ID of the station (integer)
        status (optional)
            Whether the connector is currently available (string).

            One of:

            * ``"Available"``
            * ``"Occupied"``
            * ``"Reserved"``
            * ``"Offline"``
            * ``"Unknown"``

        last-change (optional)
            string (format: ``"2016-05-09T04:08:06+02:00"``)
        name (optional)
            The type of connector (string).

            One of:

            * ``"UNKNOWN"``
            * ``"Type1"``
            * ``"Type2"``
            * ``"Type3"``
            * ``"Schuko"``
            * ``"Combo"``
            * ``"CeeBlue"``
            * ``"CeeRed"``
            * ``"Cee2Poles"``
            * ``"CeePlus"``
            * ``"3PinSquare"``
            * ``"Chademo"``
            * ``"Tesla"``
            * ``"Scame"``
            * ``"Nema5"``
            * ``"T13"``
            * ``"T15"``
            * ``"T23"``
            * ``"Marechal"``
            * ``"TypeE"``

        speed (optional)
            Max. available charging speed of the connector (string).
        mode (optional)
            string
        external-id (optional)
            If available, the EVSE ID of the conncetor (string).
            See also :ref:`EVSE <glossary-evse>`.

            If an EVSE ID is not available,
            another ID provided by the CPO may be returned.
        prices (optional)
            Prices for charging at this connector (object).
            The prices of a connector always override the prices of a station.

            Connector prices may also be returned if they equal the station prices.

            starting-fee
                The fee of starting a session at this connector (string; format ``"1.23"``).
            charging-per-hour
                The fee of charging energy at this connector, per hour (string; format ``"1.23"``).
            parking-per-hour
                The fee of parking with a connection to this connector, per hour (string; format ``"1.23"``).
            charging-per-kwh
                The fee of charging energy at this connector, per kWh (string; format ``"1.23"``).
            currency
                The currency of the prices (string; format ``"EUR"``).
        reservation (optional)
            Active reservation for this connector (object).

            end
                When this reservation ends (string; format RFC3339 ``"2016-05-09T04:08:06+02:00"``)
            own
                If reservation by the user included in User request object. If request object isn't set this will default to false. (boolean)
companies
    An array of companies.

    This array lists all companies that are relevant for the returned stations.

    id
        The internal id of the company (integer).

        The id of the company relates to the following fields in stations:

        * operator-company-id
        * owner-company-id
        * service-providers

    name
        The name of this company, e.g. "PlugSurfing".
    contact
        Available methods of contact.

        email
            string or ``null``.
        web
            string or ``null``.
        phone
            string or ``null``.
        fax
            string or ``null``.
    address
        street
            string or ``null``.
        street-number
            string or ``null``.
        city
            string or ``null``.
        zip
            string or ``null``.
        country
            string or ``null``.
    description
        A description (string or ``null``).
    type
        The type of the company (string or ``null``).

        E.g. "hotel".

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
        "station-get-by-ids": {
            "station-ids": [
                1770,
                1169,
                1003,
                2057
            ]
        }
    }

    {
        "station-get-by-ids": {
            "user": {
                "identifier-type": "username",
                "identifier": "john",
                "token": "b3853b6d910849f3b4392555b8acb984"
            },
            "station-ids": [
                1770,
                1169,
                1003,
                2057
            ]
        }
    }

Response::

    {
        "stations": [
            {
                "id": 1003,
                "address": {
                    "street": "Am Neckartor",
                    "streetNumber": "2",
                    "city": "Stuttgart",
                    "zip": "70190",
                    "country": "Germany"
                },
                "contact": {
                    "email": "e-mobilitaet@enbw.com",
                    "web": "www.enbw.com",
                    "phone": null,
                    "fax": null
                },
                "operator-company-id": 710,
                "operator-logo": "http://operatorlogopath.png",
                "floor-level": null,
                "is-free-charge": false,
                "last-static-change": "2015-01-23T18:54:52+01:00",
                "last-dynamic-change": "2013-02-12T01:43:23+01:00",
                "name": "Am Neckartor",
                "description": null,
                "latitude": 48.786574,
                "longitude": 9.190824,
                "open-hour-notes": [
                    {
                        "times": [
                            "24h"
                        ],
                        "days": [
                            "Mo",
                            "Su"
                        ]
                    }
                ],
                "total-parking": 1,
                "notes": "",
                "is-green-power-available": true,
                "is-plugin-charge": true,
                "is-roofed": false,
                "is-reservable": false,
                "has-dynamic-info": false,
                "is-open-24": true,
                "dynamic-status-summary": null,
                "is-validated": true,
                "is-private": false,
                "owner-company-id": null,
                "service-providers": [
                    710
                ],
                "connectors": [
                    {
                        "id": 11154,
                        "status": "Unknown",
                        "last-change": "2014-07-01T15:24:28+02:00",
                        "name": "Schuko",
                        "speed": "3.7kW",
                        "mode": "Mode1",
                        "external-id": "DE*123*1234567",
                        "prices": null,
                        "reservation": {
                            "end": "2016-07-01T15:24:28+02:00",
                            "own": false
                        }
                    }
                ]
            },
            {
                "id": 1169,
                "address": {
                    "street": "Südwall",
                    "streetNumber": "32",
                    "city": "Geldern",
                    "zip": "47608",
                    "country": "Germany"
                },
                "contact": {
                    "email": null,
                    "web": "www.stadtwerke-geldern.de",
                    "phone": null,
                    "fax": null
                },
                "operator-company-id": 715,
                "operator-logo": null,
                "floor-level": null,
                "is-free-charge": false,
                "last-static-change": "2015-01-23T18:54:52+01:00",
                "last-dynamic-change": "2013-02-12T01:49:05+01:00",
                "name": "Marktparkhaus am Südwall",
                "description": null,
                "latitude": 51.516123,
                "longitude": 6.322554,
                "open-hour-notes": [
                    {
                        "times": [
                            "07:30",
                            "20:00"
                        ],
                        "days": [
                            "Mo",
                            "Fr"
                        ]
                    },
                    {
                        "times": [
                            "07:30",
                            "15:00"
                        ],
                        "days": [
                            "Sa",
                            "Sa"
                        ]
                    }
                ],
                "total-parking": 1,
                "notes": "PARKING CHARGE",
                "is-green-power-available": true,
                "is-plugin-charge": true,
                "is-roofed": false,
                "is-reservable": false,
                "has-dynamic-info": false,
                "is-open-24": false,
                "dynamic-status-summary": "Available",
                "is-validated": true,
                "is-private": false,
                "owner-company-id": 28,
                "service-providers": [
                    715,
                    1224
                ],
                "connectors": [
                    {
                        "id": 11451,
                        "status": "Available",
                        "last-change": "2014-07-01T15:25:40+02:00",
                        "name": "Chademo",
                        "speed": "52kW",
                        "mode": "Mode4",
                        "external-id": "DE*123*E00000002",
                        "prices": {
                            "starting-fee": "0.00",
                            "charging-per-hour": "0.00",
                            "parking-per-hour": "1.30",
                            "charging-per-kwh": "0.17",
                            "currency": "EUR"
                        }
                    },
                    {
                        "id": 11452,
                        "status": "Occupied",
                        "last-change": "2014-07-01T15:25:40+02:00",
                        "name": "Type2",
                        "speed": "22.2kW",
                        "mode": "Mode3",
                        "external-id": "DE*123*E00000002",
                        "prices": {
                            "starting-fee": "0.00",
                            "charging-per-hour": "0.00",
                            "parking-per-hour": "1.10",
                            "charging-per-kwh": "0.36",
                            "currency": "EUR"
                        }
                    }
                ]
            },
            {
                "id": 1770,
                "address": {
                    "street": "Torgauer Straße",
                    "streetNumber": "12",
                    "city": "Berlin",
                    "zip": "10829",
                    "country": "Germany"
                },
                "contact": {
                    "email": null,
                    "web": "https://www.rwe-mobility.com",
                    "phone": null,
                    "fax": null
                },
                "operator-company-id": 715,
                "operator-logo": null,
                "floor-level": null,
                "is-free-charge": false,
                "last-static-change": "2015-01-23T18:54:52+01:00",
                "last-dynamic-change": "2014-12-29T21:48:08+01:00",
                "name": "Torgauer Straße",
                "description": null,
                "latitude": 52.482327,
                "longitude": 13.357278,
                "open-hour-notes": [
                    {
                        "times": "[24h]",
                        "days": [
                            "Mo",
                            "Su"
                        ]
                    }
                ],
                "total-parking": 1,
                "notes": "",
                "is-green-power-available": true,
                "is-plugin-charge": true,
                "is-roofed": false,
                "is-reservable": false,
                "has-dynamic-info": true,
                "is-open-24": true,
                "dynamic-status-summary": "Available",
                "is-validated": true,
                "is-private": false,
                "owner-company-id": 28,
                "service-providers": [
                    715,
                    1224,
                    1337,
                    1338
                ],
                "connectors": [
                    {
                        "id": 8613,
                        "status": "Available",
                        "last-change": "2014-12-29T21:48:08+01:00",
                        "name": "Type2",
                        "speed": "22.2kW",
                        "mode": "Mode3",
                        "external-id": null,
                        "prices": {
                            "starting-fee": "0.00",
                            "charging-per-hour": "0.00",
                            "parking-per-hour": "1.10",
                            "charging-per-kwh": "0.36",
                            "currency": "EUR"
                        }
                    },
                    {
                        "id": 8614,
                        "status": "Available",
                        "last-change": "2014-12-23T21:22:09+01:00",
                        "name": "Type2",
                        "speed": "22.2kW",
                        "mode": "Mode3",
                        "external-id": null,
                        "prices": {
                            "starting-fee": "0.00",
                            "charging-per-hour": "0.00",
                            "parking-per-hour": "1.10",
                            "charging-per-kwh": "0.36",
                            "currency": "EUR"
                        }
                    }
                ]
            },
            {
                "id": 2057,
                "address": {
                    "street": "Church Row",
                    "streetNumber": "23",
                    "city": "London",
                    "zip": "NW3 6UR",
                    "country": "United Kingdom"
                },
                "contact": {
                    "email": "membership@sourcelondon.net",
                    "web": "https://www.sourcelondon.net/",
                    "phone": null,
                    "fax": null
                },
                "operator-company-id": 39,
                "operator-logo": null,
                "floor-level": null,
                "is-free-charge": true,
                "last-static-change": "2015-01-23T18:54:52+01:00",
                "last-dynamic-change": "2013-02-19T20:17:41+01:00",
                "name": "Church Row",
                "description": null,
                "latitude": 51.556097,
                "longitude": -0.179109,
                "open-hour-notes": [
                    {
                        "times": "[24h]",
                        "days": [
                            "Mo",
                            "Su"
                        ]
                    }
                ],
                "total-parking": 1,
                "notes": "",
                "is-green-power-available": false,
                "is-plugin-charge": true,
                "is-roofed": false,
                "is-reservable": false,
                "has-dynamic-info": false,
                "is-open-24": true,
                "dynamic-status-summary": null,
                "is-validated": true,
                "is-private": false,
                "owner-company-id": null,
                "service-providers": null,
                "connectors": [
                    {
                        "id": 25443,
                        "status": "Unknown",
                        "last-change": "2014-08-14T18:00:37+02:00",
                        "name": "Type2",
                        "speed": "3.7kW",
                        "mode": "Mode3",
                        "external-id": null,
                        "prices": {
                            "starting-fee": "0.00",
                            "charging-per-hour": "0.00",
                            "parking-per-hour": "0.00",
                            "charging-per-kwh": "0.00",
                            "currency": "EUR"
                        }
                    },
                    {
                        "id": 25444,
                        "status": "Unknown",
                        "last-change": "2014-08-14T18:00:37+02:00",
                        "name": "3PinSquare",
                        "speed": "3.7kW",
                        "mode": "Mode1",
                        "external-id": null,
                        "prices": {
                            "starting-fee": "0.00",
                            "charging-per-hour": "0.00",
                            "parking-per-hour": "0.00",
                            "charging-per-kwh": "0.00",
                            "currency": "EUR"
                        }
                    }
                ]
            }
        ],
        "companies": [
            {
                "id": 28,
                "name": "RWE",
                "contact": {
                    "email": null,
                    "web": "https://www.rwe-mobility.com",
                    "phone": "0800 2335335",
                    "fax": null
                },
                "address": {
                    "street": null,
                    "streetNumber": null,
                    "city": null,
                    "zip": null,
                    "country": "United Kingdom"
                },
                "description": "RWE",
                "type": null
            },
            {
                "id": 39,
                "name": "Source London",
                "contact": {
                    "email": "membership@sourcelondon.net",
                    "web": "https://www.sourcelondon.net/",
                    "phone": "+448458500653",
                    "fax": null
                },
                "address": {
                    "street": null,
                    "streetNumber": null,
                    "city": "POOLE",
                    "zip": "BH12 9HE",
                    "country": "United Kingdom"
                },
                "description": null,
                "type": null
            },
            {
                "id": 710,
                "name": "ENBW",
                "contact": {
                    "email": "e-mobilitaet@enbw.com",
                    "web": "www.enbw.com",
                    "phone": "+498003629001",
                    "fax": null
                },
                "address": {
                    "street": null,
                    "streetNumber": null,
                    "city": null,
                    "zip": null,
                    "country": "Germany"
                },
                "description": null,
                "type": null
            },
            {
                "id": 715,
                "name": "RWE",
                "contact": {
                    "email": null,
                    "web": "https://www.rwe-mobility.com",
                    "phone": "+498002255793",
                    "fax": null
                },
                "address": {
                    "street": null,
                    "streetNumber": null,
                    "city": null,
                    "zip": null,
                    "country": "Germany"
                },
                "description": null,
                "type": null
            },
            {
                "id": 1224,
                "name": "SMS",
                "contact": {
                    "email": null,
                    "web": null,
                    "phone": null,
                    "fax": null
                },
                "address": {
                    "street": null,
                    "streetNumber": null,
                    "city": null,
                    "zip": null,
                    "country": "Germany"
                },
                "description": null,
                "type": null
            },
            {
                "id": 1337,
                "name": "PlugSurfing App",
                "contact": {
                    "email": "service@plugsurfing.com ",
                    "web": "https://www.plugsurfing.com/",
                    "phone": null,
                    "fax": null
                },
                "address": {
                    "street": "Torgauerstr",
                    "streetNumber": "12-15",
                    "city": "Berlin",
                    "zip": "10829",
                    "country": "Germany"
                },
                "description": null,
                "type": null
            },
            {
                "id": 1338,
                "name": "Intercharge QR-Code",
                "contact": {
                    "email": "service@plugsurfing.com ",
                    "web": "https://www.plugsurfing.com/",
                    "phone": null,
                    "fax": null
                },
                "address": {
                    "street": "Torgauerstr",
                    "streetNumber": "12-15",
                    "city": "Berlin",
                    "zip": "10829",
                    "country": "Germany"
                },
                "description": null,
                "type": null
            }
        ],
        "result": {
            "code": 0,
            "message": "Success."
        }
    }
