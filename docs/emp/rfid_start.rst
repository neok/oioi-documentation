.. _emp-rfid-start-docs:

Allowing RFID Starts as EMP
===========================
There are two options to allow RFID charging as an EMP:

* :ref:`emp-rfid-online-docs`
* :ref:`emp-rfid-offline-docs`

With online authorization,
a UID is verified every time a customer wants to charge.

With offline authorization,
the EMP must send a whitelist of known UIDs to the CPO.

.. _emp-rfid-online-docs:

Online Authorization
--------------------
With online authorization,
the CPO will send a verification request to the EMP every time an RFID token is used at on of the stations in the CPO's network.
Depending on the EMP's response,
the CPO does or does not allow charging for the given UID.
If an EMP authorizes the UID,
the CPO can allow the session and subsequently send the correlating CDR to that EMP.
See also :ref:`emp-cdr-docs`.

Implementation: :ref:`calls-rfidverify-docs`

.. _emp-rfid-offline-docs:

Offline Authorization
---------------------
With offline authorization,
the EMP will send all known UIDs to the CPO in regular intervals,
e.g. once per day.
It is then the CPO's responsibility to authorize any UID and send the subsequent CDR to the correct EMP,
if the UID was part of the last push of UIDs from that EMP to the CPO.
See also :ref:`emp-cdr-docs`.

Implementation: :ref:`calls-rfidpost-docs`
