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
   This field identifies the customer.
   The identifier is something that uniquely identifies the customer, depending on the identifier-type.
   The identifier field is of type string.
   The identifier-type can be one of:

   * ``"evco-id"``
   * ``"rfid"``
   * ``"username"``

   The token field is an optional field of type string and can be used to authenticate the user.

Response
--------

Fields
~~~~~~

vehicles
    An array of all vehicles.

    id
        The internal DB id of the vehicle.
    brand
        The maker of the vehicle (string).
    model
        The model of the vehicle (string).
    max-speed
        The maximum charging speed of the vehicle in kW (float).
    connector-types
        An array of connector types the vehicle supports (strings).

Status codes
~~~~~~~~~~~~

200 OK
   Request was processed successfully

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
        }
    }
