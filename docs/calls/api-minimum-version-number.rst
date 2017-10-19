.. highlight:: js

.. _calls-apiminimumversionnumber-docs:

API minimum version number
===========

.. warning:: You have to update the client if you are not using at least the API version returned by this call and you should not let the user interact with the API.

Request
-------

``"api-minimum-version-number"`` returns minimum required API version that must be used by any client.

Response
--------

HTTP Status code
~~~~~~~~~~~~~~~~

200 OK
    The request was processed successfully.

Result code
~~~~~~~~~~~

0
    Success

Examples
--------

Request::

    {
        "api-minimum-version-number": {
        }
    }

Response::

    {
        "api-minimum-version-number": {
            "minimum-version": "3.3.3"
        }
    }
