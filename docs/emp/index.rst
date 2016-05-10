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

For EMPs that also want to let the other party manage their users,
the HTTP request must contain an additional header::

    B2B-Customer: <your-company-name>

Example HTTP request if your company name is "Acme Inc."::

    Content-Type: application/json
    Authorization: key=a39ff3fb-fe0a-40a3-bdde-df6372c07c89
    B2B-Customer: acme

    {
        "user-verify": {
            "username": "your-user",
            "password": "mypassword",
            "is-token": false,
            "language": "en"
        }
    }

.. warning:: When connecting to PlugSurfing, make sure you communicate your chosen ``B2B-Customer`` header before the first request.
