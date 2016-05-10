.. _cpo-remote-start-docs:

Receiving Remote Starts
=======================

Starting a Session
------------------
Whenever an EV driver wants to start a session in your network,
the EMP will send a ``session-start`` request.
The EMP will analyze the CPO's response and must display an appropriate
message to the user.

* **Role:** Receiver
* **Implementation:** :ref:`calls-sessionstart-docs`

Stopping a Session
------------------
Whenever an EV driver wants to stop a running session,
the EMP will send a ``session-stop`` request.

* **Role:** Receiver
* **Implementation:** :ref:`calls-sessionstop-docs`
