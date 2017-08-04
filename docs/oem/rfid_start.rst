.. _oem-rfid-start-docs:

Allowing RFID Starts as OEM
===========================
There are two options to allow RFID charging as an OEM:

* :ref:`oem-rfid-online-docs`
* :ref:`oem-rfid-offline-docs`

With online authorization,
a UID is verified every time a customer wants to charge.

With offline authorization,
the OEM must send a whitelist of known UIDs to the :ref:`Roaming Platform <glossary-roaming-platform>`.

.. _oem-rfid-online-docs:

Online Authorization
--------------------
With online authorization,
the :ref:`Roaming Platform <glossary-roaming-platform>` will send a verification request to the OEM every time an RFID token is used at on of the stations in the CPO's network.
Depending on the OEM's response,
the Roaming Platform does or does not allow charging for the given UID.
If an OEM authorizes the UID,
the Roaming Platform can allow the session and subsequently send the correlating CDR to that OEM.
See also :ref:`oem-cdr-docs`.

* **Role:** Receiver
* **Implementation:** :ref:`calls-rfidverify-docs`

.. _oem-rfid-offline-docs:

Offline Authorization
---------------------
With offline authorization,
the OEM will send all known UIDs to the :ref:`Roaming Platform <glossary-roaming-platform>` in regular intervals,
e.g. once per day.
It is then the Roaming Platform's responsibility to authorize any UID and send the subsequent CDR to the correct OEM,
if the UID was part of the last push of UIDs from that OEM to the Roaming Platform.
See also :ref:`oem-cdr-docs`.

* **Role:** Sender
* **Implementation:** :ref:`calls-rfidpost-docs`
