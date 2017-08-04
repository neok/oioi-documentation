.. _oem-remote-start-docs:

Sending Remote Starts
=====================

Starting a Session
------------------
Whenever an EV driver wants to start a session in the :ref:`Roaming Platform's <glossary-roaming-platform>` network,
the OEM will send a ``session-start`` request.
The OEM must analyze the Roaming Platform's response and must display an appropriate
message to the user.

* **Role:** Sender
* **Implementation:** :ref:`calls-sessionstart-docs`

Stopping a Session
------------------
Whenever an EV driver wants to stop a running session,
the OEM must send a ``session-stop`` request.

Please note that in order for a session to be stoppable,
the response to ``session-start`` must include ``"is-stoppable": true``.
See also :ref:`calls-sessionstart-docs`.

* **Role:** Sender
* **Implementation:** :ref:`calls-sessionstop-docs`
