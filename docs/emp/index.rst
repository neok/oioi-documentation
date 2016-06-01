.. highlight:: none

Introduction for EMPs
=====================

In order for an EMP to connect to a CPO and make their charging stations
available in the EMP's network, the following steps need to be taken:

* :ref:`emp-user-docs`
* :ref:`emp-poi-docs`
* :ref:`emp-cdr-docs`
* :ref:`emp-remote-start-docs`
* :ref:`emp-rfid-start-docs`

Additional HTTP Header
----------------------
For basic info, see :ref:`Sending a Message to OIOI <request-docs>`.

Example HTTP request::

    Content-Type: application/json
    Authorization: key=a39ff3fb-fe0a-40a3-bdde-df6372c07c89

    {
        "user-verify": {
            "username": "your-user",
            "password": "mypassword",
            "is-token": false,
            "language": "en"
        }
    }
