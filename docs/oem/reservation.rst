.. _oem-reservation-docs:

Sending Reservations
====================

Starting a Reservation
----------------------
Whenever an EV driver wants to start an EVSE reservation in the :ref:`Roaming Platform's <glossary-roaming-platform>` network,
the OEM will send a ``reservation-start`` request.
The OEM must analyze the Roaming Platform's response and must display an appropriate
message to the user.

* **Role:** Sender
* **Implementation:** :ref:`calls-reservationstart-docs`

Cancelling a Reservation
------------------------
Whenever an EV driver wants to cancel an active reservation,
the OEM must send a ``reservation-stop`` request.

* **Role:** Sender
* **Implementation:** :ref:`calls-reservationstop-docs`
