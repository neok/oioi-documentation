.. highlight:: js

.. _calls-useraddpayment-docs:

User Add Payment
================

This call will return a URL that the frontend must use to load and show a webview.
The frontend should monitor the activity in the webview to determine success or failure of the operation.
For PlugSurfing the return URL wil be ``https://my.plugsurfing.com/profile/bankAccountAdded/oioi``.
If you need more info, please contact PlugSurfing directly.

Request
-------

``"user-add-payment"`` identifies the call as a user-add-payment call.

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

payment-type
    The type of payment that shall be added (string).

    Can be one of (directEbanking = Sofortueberweisung):

    * ``"paypal"``
    * ``"directEbanking"``
    * ``"ideal"``

Response
--------

Fields
~~~~~~

url
   The UTF encoded URL for the request (string)

HTTP Status codes
~~~~~~~~~~~~~~~~~

200 OK
    The request was processed successfully.

Result codes
~~~~~~~~~~~~
0
    Success
800
    Payment system error
805
    This user is not allowed to use this method

Examples
--------

Request::

    {
        "user-add-payment": {
            "payment-type": "paypal",
            "user": {
                "identifier-type": "username",
                "identifier": "youridentifier",
                "token": "87d4e3085af04671834ebeb127df33bf"
            }
        }
    }

Response::

    {
        "user-add-payment": {
            "url": "https://test.adyen.com/hpp/details.shtml?&paymentAmount=100&currencyCode=EUR&shipBeforeDate=2015-03-01&merchantReference=Authorization+youridentifier&skinCode=GfUFVL5L&merchantAccount=PlugSurfing&sessionValidity=2015-02-27T14%3A47%3A28%2B01%3A00&shopperEmail=customer%40gmail.com&shopperReference=youridentifier&allowedMethods=&blockedMethods=&offset=&recurringContract=RECURRING&orderData=H4sIAAAAAAAAAwvIKU0PLi1Ky8xLBwBbAAADCwAAAA%3D%3D&countryCode=DE&brandCode=paypal&merchantSig=2LUxxOwNdXV9nnAAAAJ4J%2FE4V8%3D"
        },
        "result": {
            "code": 0,
            "message": "Success."
        }

    }
