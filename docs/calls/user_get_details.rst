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
        A string, can be null.

    last-name
        A string, can be null.

    address
        The address where the user lives. Can be null.

        street
            A string.

        street-number
            A string.

        zip
            A string.

        city
            A string.

        country
            String, mandatory. Please use international two letter codes (ISO 3166-1 alpha-2).

    billing-name
        A String. If the name on the bill should not be first and lastname. Can be null.

    billing-address
        The address where the user lives. Can be null.

        street
            A string.

        street-number
            A string.

        zip
            A string.

        city
            A string.

        country
            String, mandatory. Please use international two letter codes (ISO 3166-1 alpha-2).

    locale
        A string defining the locale of the user. Two lower case letters. E.g. en for English or de for German. Can be null.
    vat
        A string. The VAT number is validated. Can be null.

    social-security-number
        A string. Can be null.

    evco-id
        A String. The EVCO-ID of the Customer. Can be null.

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
            "evco-id": "DE*8PS*156456730*9"
        }
    }
