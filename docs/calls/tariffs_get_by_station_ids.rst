.. highlight:: js

.. _calls-tariffsgetbystationids-docs:

Tariffs Get By Station IDs
==========================

Request
-------

``"tariffs-get-by-station-ids"`` identifies the call as a tariffs-get-by-station-ids call.

Fields
~~~~~~

user (optional)
    This field identifies the customer

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
    is-free-charge
        Whether charging can be done without cost (boolean).
    connectors (optional)
        id
            The responder's internal ID of the station (integer)
        tariff (optional)
            A tariff object consists of a list of one or more tariff elements,
            these elements can be used to create complex Tariff structures.

            currency
                Currency of this tariff, ISO 4217 Code
            tariff_alt_text
                List of multi language alternative tariff info text
            tariff_alt_url
                Alternative URL to tariff info
            elements
                List of tariff elements

                restrictions
                    Tariff restrictions object

                    start_time
                        Start time of day, for example 13:30, valid from this time of the day.
                        Must be in 24h format with leading zeros. Hour/Minute separator: ":"
                        Regex: [0-2][0-9]:[0-5][0-9]
                    end_time
                        End time of day, for example 19:45, valid until this time of the day.
                        Same syntax as start_time
                    start_date
                        Start date, for example: 2015-12-24, valid from this day
                    end_date
                        End date, for example: 2015-12-27, valid until this day (excluding this day)
                    min_kwh
                        Minimum used energy in kWh, for example 20, valid from this amount of energy is used
                    max_kwh
                        Maximum used energy in kWh, for example 50, valid until this amount of energy is used
                    min_power
                        Minimum power in kW, for example 0, valid from this charging speed
                    max_power
                        Maximum power in kW, for example 20, valid up to this charging speed
                    min_duration
                        Minimum duration in seconds, valid for a duration from x seconds
                    max_duration
                        Maximum duration in seconds, valid for a duration up to x seconds
                    day_of_week
                        Which day(s) of the week this tariff is valid

                price_components
                    List of price components that make up the pricing of this tariff

                    type
                        Type of tariff dimension
                    price
                        Price per unit (excluding VAT) for this tariff dimension
                    step_size
                        Minimum amount to be billed. This unit will be billed in this step_size blocks.
                        For example: if type is time and step_size is 300, then time will be billed in blocks
                        of 5 minutes,so if 6 minutes is used, 10 minutes (2 blocks of step_size) will be billed.
            energy_mix
                Details on the energy supplied with this tariff.
                    is_green_energy
                        True if 100% from regenerative sources. (CO2 and nuclear waste is zero)
                    energy_sources
                        Key-value pairs (enum + percentage) of energy sources of this location's tariff.

                        source
                            The type of energy source
                        percentage
                            Percentage of this source (0-100) in the mix
                    environ_impact
                        Key-value pairs (enum + percentage) of nuclear waste and CO2 exhaust of this location's tariff

                        source
                            The category of this value
                        amount
                            Amount of this portion in g/kWh
                    supplier_name
                        Name of the energy supplier, delivering the energy for this location or tariff
                    energy_product_name
                        Name of the energy suppliers product/tariff plan used at this location
            last_updated
                Timestamp when this Tariff was last updated (or created).

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
        "tariffs-get-by-station-ids": {
            "station-ids": [
                1770
            ]
        }
    }

    {
        "tariffs-get-by-station-ids": {
            "user": {
                "identifier-type": "username",
                "identifier": "john",
                "token": "b3853b6d910849f3b4392555b8acb984"
            },
            "station-ids": [
                1770
            ]
        }
    }

Response::

    {
        "stations": [
            {
                "id": 1770,
                "is-free-charge": false,
                "connectors": [
                    {
                        "id": 11154,
                        "tariff": {
                            "currency": "EUR",
                            "elements": {
                                "restrictions": {
                                    "start_time": "13:30",
                                    "end_time": "19:45",
                                    "start_date": "2015-12-24",
                                    "end_date": "2015-12-27",
                                    "min_kwh": 20,
                                    "max_kwh": 50,
                                    "min_power": 32.00,
                                    "max_power": 74.00,
                                    "min_duration": 40,
                                    "max_duration": 70,
                                    "day_of_week": ["SATURDAY", "SUNDAY"]
                                },
                                "price_components": {
                                    "type": "FLAT",
                                    "price": "0.00",
                                    "step_size": 1
                                },
                                {
                                    "type": "PARKING_TIME",
                                    "price": "0.00",
                                    "step_size": 1
                                },
                                {
                                    "type": "TIME",
                                    "price": "0.00",
                                    "step_size": 1
                                },
                                {
                                    "type": "ENERGY",
                                    "price": "0.00",
                                    "step_size": 1
                                }
                            }
                            "energy_mix": {
                                "is_green_energy": false,
                                "energy_sources": [
                                        { "source": "GENERAL_GREEN", "percentage": 35.9 },
                                        { "source": "GAS", "percentage": 6.3  },
                                        { "source": "COAL", "percentage": 33.2 },
                                        { "source": "GENERAL_FOSSIL", "percentage": 2.9 },
                                        { "source": "NUCLEAR", "percentage": 21.7 }
                                    ],
                                "environ_impact": [
                                        { "source": "NUCLEAR_WASTE", "amount": 0.0006 },
                                        { "source": "CARBON_DIOXIDE", "amount": 372 }
                                    ],
                                "supplier_name": "E.ON Energy Deutschland",
                                "energy_product_name": "E.ON DirektStrom eco"
                                },
                                "last_updated": "2018-07-09T11:13:56Z"
                            }
                        }
                    }
                ]
            }
        ]
    }
