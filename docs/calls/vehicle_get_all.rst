.. highlight:: js

.. _calls-vehiclegetall-docs:

Get All Vehicles
================

Request
-------

``"vehicle-get-all"`` identifies the call as a vehicle-get-all call.

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

HTTP Status codes
~~~~~~~~~~~~~~~~~

200 OK
   Request was processed successfully

Result codes
~~~~~~~~~~~~
0
    Success

Examples
--------

Request::

    {
        "vehicle-get-all": {
            "user": {
                "identifier-type": "username",
                "identifier": "johndoe",
                "token": "87d4e3085af04671834ebeb127df33bf"
            }
        }
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
        },
        "result": {
            "code": 0,
            "message": "Success."
        }
    }
