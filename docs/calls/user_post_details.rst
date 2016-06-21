.. highlight:: js

.. _calls-userpostdetails-docs:

User Post Details
=================

Request
-------

``"user-post-details"`` identifies the call as user-post-details call.

Fields
~~~~~

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

    locale
        Defining the locale of the user (string).

        Two lower case letters. E.g. en for English or de for German. Can be null.

    vat
        The VAT number is validated, can be null (string).

    social-security-number
        Social security number, can be null (string).

    billing-name
        If the name on te bill should not be first and lastname. Can be null (string).

    billing-address
        In case the address on the bill shall be different from the address, it can be specified. Can be null (object).

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

Response
--------

Fields
~~~~~~
success
    A boolean specifying whether the request was handled successfully.

reason
    An optional response field. If present, it is a string stating the reason for an error.

Status codes
~~~~~~~~~~~~
200 OK
   Request was processed successfully
400 Invalid
   If the country or VAT is invalid (reason is displayed in response)
401 Unauthorized
   The token, username or identifier type were incorrect

Examples
--------

Request::

    {
        "user-post-details": {
            "user": {
                "identifier-type": "username",
                "identifier": "iAmUser",
                "token": "abababa"
            },
            "details": {
                "first-name": "Firstname",
                "last-name": "Lastname",
                "address": {
                    "street": "Torgauer Str.",
                    "street-number": "12 - 15",
                    "zip": "10829",
                    "city": "Berlin",
                    "country": "DE"
                },
                "locale": "de",
                "vat": "DE1234567",
                "social-security-number": null,
                "billing-name": "PlugSurfing GmbH",
                "billing-address": {
                    "street": "Torgauer Str.",
                    "street-number": "12 - 15",
                    "zip": "10829",
                    "city": "Berlin",
                    "country": "DE"
                }
            }
        }
    }

Response::

    {
        "user-post-details": {
            "success": true
        }
    }

    {
        "user-post-details": {
            "success": false,
            "reason": "Could not validate VAT number: DE1234567"
        }
    }
