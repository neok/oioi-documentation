.. highlight:: js

.. _calls-vehiclegetall-docs:

Get All Vehicles
================

Request
-------

``"vehicle-get-all"`` identifies the call as a vehicle-get-all call.

Fields
~~~~~~

There are no request fields.

Response
--------

Fields
~~~~~~

vehicles
    An array of objects.

    id
        The internal DB ID of the vehicle (integer).
    brand
        The maker of the vehicle (string).
    model
        The model of the vehicle (string).
    max-speed
        The maximum charging speed of the vehicle in kW (float).
    connector-types
        An array of connector types the vehicle supports (strings).

        Types are of:

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

Status codes
~~~~~~~~~~~~

200 OK
   Request was processed successfully

Examples
--------

Request::

    {
        "vehicle-get-all": {}
    }

Response::

    {
        "vehicle-get-all": {
            "vehicles": [
                {
                    "id": 1,
                    "brand": "BMW",
                    "model": "i3",
                    "max-speed": 3.7,
                    "connector-types": [
                        "Type3"
                    ]
                },
                {
                    "id": 2,
                    "brand": "Renault",
                    "model": "Twizzy",
                    "max-speed": 45,
                    "connector-types": [
                        "Schuko"
                    ]
                }
            ]
        }
    }
