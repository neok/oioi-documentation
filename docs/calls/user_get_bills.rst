.. highlight:: js

.. _calls-usergetbills-docs:

User Get Bills
==========================

Request
-------

``"user-get-bills"`` identifies the call as a user-get-bills call.

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
        * ``"token"``

    identifier
        The identifier is something that uniquely identifies the customer,
        depending on the identifier-type (string).

    token (optional)
        A token can be used to authenticate the user (string).

        For example: if the identifier type is username and the identifier is the user's username,
        then token is used for authentication instead of a password.

date-interval
    This field sets the date interval for which bills should be returned (object).

        start
            Date/Time as string in format Y-m-d\TH:i:sP. E.g. 2015-03-04T13:32:12+01:00.

        end
            Date/Time as string in format Y-m-d\TH:i:sP. E.g. 2015-03-06T00:00:00+01:00.

Response
--------

Fields
~~~~~~

bills
   This field contains the bills for the requested date interval (array).

   external-session-ids
     List of session ID's for the invoice (array).

   bill
     URL with link to the invoice (string).

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
        "user-get-bills": {
            "user": {
                "identifier-type": "username",
                "identifier": "some_user",
                "token": "b369f99e82fa097ba9cff8658c74e47c"
            },
            "date-interval": {
                "start": "2015-03-04T13:32:12+01:00",
                "end": "2015-03-06T00:00:00+01:00"
            }
        }
    }

Response::

    {
        "user": {
            "bills": [
                {
                    "external-session-ids": [
                        "6a2f25f6-0a88-1293-5ab0-0e3da7abcdef"
                    ],
                    "bill": "https://api.plugsurfing.com/uploads/bills/Invoice-201503051-10000.pdf"
                },
                {
                    "external-session-ids": [
                        "6a2f25f6-a82c-1234-9090-0e3da7abcde1",
                        "6a2f25f6-927f-6578-1432-8394caabcde2"
                    ],
                    "bill": "https://api.plugsurfing.com/uploads/bills/Invoice-201503052-10000.pdf"
                }
            ]
        },
        "result": {
            "code": 0,
            "message": "Success."
        }
    }
