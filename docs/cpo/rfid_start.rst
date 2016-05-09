.. _cpo-rfid-start-docs:

Allowing RFID Starts as CPO
===========================
There are two options to allow RFID charging at a CPO:

* :ref:`cpo-rfid-online-docs`
* :ref:`cpo-rfid-offline-docs`

With online authorization,
a UID is verified every time a customer wants to charge at one of the CPO's stations.

With offline authorization,
the EMP must send a whitelist of known UIDs to the CPO.

.. _cpo-rfid-online-docs:

Online Authorization
--------------------
With online authorization,
the CPO has to send a verification request to the EMP every time an RFID token is used at on of the CPO's stations.
Depending on the EMP's response,
the EMP does or does not allow charging for the given UID.
If an EMP authorizes the UID,
the CPO can allow the session and subsequently send the correlating CDR to that EMP.
See also :ref:`cpo-cdr-docs`.

Implementation: :ref:`calls-rfidverify-docs`

.. _cpo-rfid-offline-docs:

Offline Authorization
---------------------
With offline authorization,
the EMP will send all known UIDs to the CPO in regular intervals,
e.g. once per day.
It is then the CPO's responsibility to authorize any UID and send the subsequent CDR to the corresponding EMP,
if the UID was part of the last push of UIDs from the EMP to the CPO.
See also :ref:`cpo-cdr-docs`.

Implementation: :ref:`calls-rfidpost-docs`
