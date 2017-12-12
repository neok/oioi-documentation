.. highlight:: js

.. _calls-adyensetup-docs:

Adyen Setup
===========

Request
-------

``"adyen-setup"`` identifies the call as a adyen-setup call.
Currently, this method serves as a proxy, it just sends requests from mobile application to Adyen and then sends
responses back from Adyen to application.

Fields
~~~~~~

Server does not perform any validation on requests, so you need to fill fields by yourself. Please check `Adyen documentation for setup call`_.

Please see Examples section to see the request object with minimum number of required fields.


Response
--------

Response from Adyen in JSON format that should be passed to the Adyen SDK.

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
       "adyen-setup":{
          "amount":{
             "currency":"EUR",
             "value":1
          },
          "channel":"web",
          "countryCode":"DE",
          "merchantAccount":"PlugSurfing",
          "reference":"9c19a19a-b58c-414e-9c5a-82da2056e27e",
          "returnUrl":"",
          "shopperLocale":"en_GB",
          "shopperReference":"test-email@test-server.test",
          "token":"some valid token from SDK"
       }
    }

Response::

    {
        "adyen-setup":{
            "response": {
                "property1":"value1"
            }
        },
        "result": {
            "code": 0,
            "message": "Success."
        }
    }
    
.. _Adyen documentation for setup call: https://docs.adyen.com/developers/in-app-integration/checkout-api-reference#setup