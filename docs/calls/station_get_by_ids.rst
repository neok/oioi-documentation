.. highlight:: js

.. _calls-stationgetbyids-docs:

Station Get By IDs
==================

Request
-------

``"station-get-by-ids"`` identifies the call as a station-get-by-ids call.

Fields
~~~~~~

station-ids
    An array of IDs (integers).

    The maximum number of IDs per call is ten.

Response
--------

Fields
~~~~~~


stations
    An array of charging stations (objects).

    operator-company-id
        The CPO of the charging station.

        The charge point operator is the company responsible for the functioning of the station.
        Access to the station usually also goes through the CPO.
    owner-company-id
        The owner of the charging station.

        The owner is usually either the CPO or something like a restaurant or Ikea, owning the stations on their property.
    service-providers
        An array of all service providers of the charging station.

        A service provider is a company that grants access to a charging station.
        See :ref:`EMP <glossary-emp>`.

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

Status codes
~~~~~~~~~~~~

200 OK
    The request was processed successfully.

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
                        "status": "UNKNOWN",
                        "last-change": "2014-07-01T15:24:28+02:00",
                        "name": "Schuko",
                        "speed": "3.7kW",
                        "mode": "Mode1",
                        "external-id": "+49*123*1234567"
                    }
                ],
                "prices": {
                    "starting-fee": null,
                    "charging-per-hour": null,
                    "parking-per-hour": "4.50",
                    "charging-per-kwh": null,
                    "currency": "EUR"
                }
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
                "dynamic-status-summary": null,
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
                        "status": "UNKNOWN",
                        "last-change": "2014-07-01T15:25:40+02:00",
                        "name": "Type2",
                        "speed": "22.2kW",
                        "mode": "Mode3"
                    },
                    {
                        "id": 11452,
                        "status": "UNKNOWN",
                        "last-change": "2014-07-01T15:25:40+02:00",
                        "name": "Type2",
                        "speed": "22.2kW",
                        "mode": "Mode3"
                    }
                ],
                "prices": {
                    "starting-fee": null,
                    "charging-per-hour": null,
                    "parking-per-hour": "1.10",
                    "charging-per-kwh": "0.36",
                    "currency": "EUR"
                }
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
                "dynamic-status-summary": "AVAILABLE",
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
                        "status": "AVAILABLE",
                        "last-change": "2014-12-29T21:48:08+01:00",
                        "name": "Type2",
                        "speed": "22.2kW",
                        "mode": "Mode3"
                    },
                    {
                        "id": 8614,
                        "status": "AVAILABLE",
                        "last-change": "2014-12-23T21:22:09+01:00",
                        "name": "Type2",
                        "speed": "22.2kW",
                        "mode": "Mode3"
                    }
                ],
                "prices": {
                    "starting-fee": null,
                    "charging-per-hour": null,
                    "parking-per-hour": "1.10",
                    "charging-per-kwh": "0.36",
                    "currency": "EUR"
                }
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
                        "status": "UNKNOWN",
                        "last-change": "2014-08-14T18:00:37+02:00",
                        "name": "Type2",
                        "speed": "3.7kW",
                        "mode": "Mode3"
                    },
                    {
                        "id": 25444,
                        "status": "UNKNOWN",
                        "last-change": "2014-08-14T18:00:37+02:00",
                        "name": "3PinSquare",
                        "speed": "3.7kW",
                        "mode": "Mode1"
                    }
                ],
                "prices": {
                    "starting-fee": null,
                    "charging-per-hour": null,
                    "parking-per-hour": null,
                    "charging-per-kwh": null,
                    "currency": "EUR"
                }
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
        ]
    }
