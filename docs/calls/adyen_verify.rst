.. highlight:: js

.. _calls-adyenverify-docs:

Adyen Verify
============

Request
-------

``"adyen-verify"`` identifies the call as a adyen-verify call.
Currently, this method serves as a proxy, it just sends requests from mobile application to Adyen and then sends
responses back from Adyen to application.

Fields
~~~~~~

Server does not perform any validation on requests, so you need to fill fields by yourself. Please check `Adyen documentation for verify call`_.

Please see Examples section to see the request object with minimum number of required fields.


Response
--------

Response from Adyen in JSON format.

HTTP Status codes
~~~~~~~~~~~~~~~~~

200 OK
    The request was processed successfully.

Result codes
~~~~~~~~~~~~
0
    Success
100
    System error


Examples
--------

Request::

    {
       "adyen-verify":{
            "payload":"payload from SDK"
       }
    }

Response::

    {
        "adyen-verify":{
            "response": {
                "authResponse":"authentication result",
                "merchantReference":"reference from setup call",
                "pspReference":"unique reference associated with the transaction"
            }
        },
        "result": {
            "code": 0,
            "message": "Success."
        }
    }

.. _Adyen documentation for verify call: https://docs.adyen.com/developers/in-app-integration/checkout-api-reference#verify