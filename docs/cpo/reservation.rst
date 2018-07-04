.. _cpo-reservation-docs:

Receiving Reservations
======================

Starting a Reservation
----------------------
Whenever an EV driver wants to make an EVSE reservation in your network,
the EMP will send a ``reservation-start`` request.
The EMP will analyze the CPO's response and must display an appropriate
message to the user.
*All* EVCO IDs and UIDs of the reservation call should be able to start a session.
No other EVCO ID or UID should be able to start a session in that reservation window.

.. note:: If another user makes a ``session-start`` request while there is an active reservation on the same EVSE, it is the CPO's responsibility to reject that session.

* **Role:** Receiver
* **Implementation:** :ref:`calls-reservationstart-docs`

Cancelling a Reservation
------------------------
Whenever an EV driver wants to cancel an active reservation,
the EMP will send a ``reservation-stop`` request.
*Any* EVCO ID or UID of the reservation call should be able to stop the reservation for *all* EVCO IDs/UIDs of the reservation.

* **Role:** Receiver
* **Implementation:** :ref:`calls-reservationstop-docs`
