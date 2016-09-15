.. highlight:: js

.. _calls-companygetimages-docs:

Company Get Images
==================

Request
-------

``"company-get-images"`` identifies the call as a company-get-images call.

Fields
~~~~~~

company-id
    This field identifies the company (integer).

Response
--------

Fields
~~~~~~

company
    This field contains the name of the company (string).

urls
    This field contains all URLs that point to images of the company (array of strings).

HTTP Status codes
~~~~~~~~~~~~~~~~~

200 OK
    The request was processed successfully.

Result codes
~~~~~~~~~~~~
0
    Success

Examples
--------

Request::

    {
        "company-get-images": {
            "company-id": 123
        }
    }

Response::

    {
        "company": "ACME Inc.",
        "urls": [
            "https://s3.amazonaws.com/ksr/projects/392582/photo-main.jpg",
            "https://commons.wikimedia.org/wiki/File:Acme_anvil.gif#/media/File:Acme_anvil.gif"
        ],
        "result": {
            "code": 0,
            "message": "Success."
        }
    }
