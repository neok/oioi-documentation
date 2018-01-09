.. highlight:: js

.. _calls-usergetdetails-docs:

User Get Details
================

Request
-------

``"user-get-details"`` identifies the call as a user-get-details call.

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

user
    This field contains the user (object).

    first-name
        First name of a user, can be null (string).

    last-name
        Last name of a user, can be null (string).

    address
        The address where the user lives. Can be null (object).

        street
            Street name (string).

        street-number
            Street number (string).

        zip
            Zipcode for the address (string).

        city
            Name of the City (string).

        country
            Country, mandatory (string).

            Please use international two letter codes (ISO 3166-1 alpha-2).

    billing-name
        If the name on the bill should not be first and lastname. Can be null (string).

    billing-address
        The address where the user lives. Can be null (object).

        street
            Street name (string).

        street-number
            Street number (string).

        zip
            Zipcode for the address (string).

        city
            Name of the City (string).

        country
            Country, mandatory (string).

            Please use international two letter codes (ISO 3166-1 alpha-2).

    locale
        Locale of the user (string).

        Two lower case letters. E.g. en for English or de for German. Can be null.

    vat
        The VAT number is validated, can be null (string).

    social-security-number
        Social Security Number, can be null (string).

    evco-id
        The EVCO-ID of the Customer, can be null (string).

    phone
        The phone of the Customer, can be null (string).

    company-name
        Company name of the Customer, can be null (string).

HTTP Status codes
~~~~~~~~~~~~~~~~~

200 OK
    The request was processed successfully.

Result codes
~~~~~~~~~~~~
0
    Success
140
    Authentication failed: No positive authentication response
144
    Authentication failed: Email does not exist
145
    Authentication failed: User token not valid

Examples
--------

Request::

    {
        "user-get-details": {
            "user": {
                "identifier-type": "username",
                "identifier": "youridentifier",
                "token": "87d4e3085af04671834ebeb127df33bf"
            }
        }
    }

Response::

    {
        "user": {
            "first-name": "Firstname",
            "last-name": "Lastname",
            "address": {
                "street": "Warschauer Str.",
                "street-number": "1",
                "city": "Berlin",
                "zip": "10247",
                "country": "Germany"
            },
            "billing-name": "PlugSurfing GmbH",
            "billing-address": {
                "street": "Torgauer Str.",
                "street-number": "12-15",
                "city": "Berlin",
                "zip": "10829",
                "country": "Germany"
            },
            "locale": "de",
            "vat": "DE123456",
            "social-security-number": "SocialSecNumber",
            "evco-id": "DE*8PS*156456730*9",
            "phone": "+49 151 84512991",
            "company-name": "PlugSurfing GmbH"
        },
        "result": {
            "code": 0,
            "message": "Success."
        }
    }
