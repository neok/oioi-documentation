.. highlight:: none

Introduction for OEMs
=====================

In order for an OEM to connect to a :ref:`Roaming Platform <glossary-roaming-platform>` and make their charging stations
available in the OEM's network, the following steps need to be taken:

* :ref:`oem-user-docs`
* :ref:`oem-poi-docs`
* :ref:`oem-cdr-docs`
* :ref:`oem-remote-start-docs`
* :ref:`oem-rfid-start-docs`

Additional HTTP Header
----------------------
For basic info, see :ref:`Sending a Message via OIOI <request-docs>`.

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
