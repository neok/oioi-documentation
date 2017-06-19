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
Optional fields may be omitted or have the value ``null``.

user
    The user details (object).

    first-name (optional)
        The first name of the user (string).
    last-name (optional)
        The last name of the user (string).
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
    billing-name (optional)
        The name of the user that should be used when addressing a bill (string).
    billing-address (optional)
        If a billing address is given, it should be used instead of the address when sending a bill (object).

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
    locale (optional)
        The locale of the user (string).

        A lowercase, two-character string in accordance with `ISO 639-1:2002`_.
    vat (optional)
        The VAT number of the user (string).
    social-security-number (optional)
        The social security number of the user (string).
    evco-id (optional)
        The EVCO ID that identifies this user when the suer uses the app (string).

Status codes
~~~~~~~~~~~~

200 OK
    The request was processed successfully.
400 Bad Request
    The request is not valid, e.g. if an invalid identifier type is sent.
401 Unauthorized
    The username does not exist or the username and password/token did not match.

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

.. _iso 639-1:2002: https://en.wikipedia.org/wiki/ISO_639-1
