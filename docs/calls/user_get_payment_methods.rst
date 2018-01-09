.. highlight:: js

.. _calls-usergetpaymentmethods-docs:

User Get Payment Methods
========================

Request
-------

``"user-get-payment-methods"`` identifies the call as a user-get-payment-methods call.

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

Response
--------

Fields
~~~~~~

.. important:: The API response may include question marks ``?`` if a value is unknown.

payment-methods
    This field contains the payment methods of the user (array).

    reference
        The internal reference to refer to this payment method (string).

    method
        The type of the payment method (string).

        Can be one of:

        * ``"Bank"``
        * ``"Credit Card"``
        * ``"PayPal"``
        * ``"Invoice"``
        * ``"SEPA"``

    created
        The date and time when the method was created (string).

        The date/time format is RFC3339 (``Y-m-d\TH:i:sP``).

    number (optional - in case of a ``Credit Card``)
        Credit card number (string).

        The credit card number format is ``****-****-****-<last four digets>``.

    valid (optional - in case of a ``Credit Card``)
        The date when the credit card expires (string).

        The expiration format is ``MM/YYYY``.

    name (optional - in case of a ``Credit Card`` or ``Bank``)
        Name of the credit card holder or name of the owner of a bank account (string).

    iban (optional - in case of a ``Bank``)
        The IBAN of the bank account (string).

    bic (optional - in case of a ``Bank``)
        The BIC of the bank account (string).

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
        "user-get-payment-methods": {
            "user": {
                "identifier-type": "username",
                "identifier": "some_user",
                "token": "b369f99e82fa097ba9cff8658c74e47c"
            }
        }
    }

Response::

    {
        "user": {
            "payment-methods": [
                {
                    "reference": "1823048264562525",
                    "method": "Credit Card",
                    "created": "2017-12-15T17:41:18+02:00",
                    "number": "****-****-****-1234",
                    "valid": "3\/2021",
                    "name": "Smart Man"
                }
            ]
        },
        "result": {
            "code": 0,
            "message": "Success."
        }
    }

