.. _emp-remote-start-docs:

Sending Remote Starts
=====================

Starting a Session
------------------
Whenever an EV driver wants to start a session in c CPO's network,
the EMP will send a ``session-start`` request.
The EMP must analyze the CPO's response and must display an appropriate
message to the user.

Implementation: :ref:`calls-sessionstart-docs`

Stopping a Session
------------------
Whenever an EV driver wants to stop a running session,
the EMP must send a ``session-stop`` request.

Please note that in order for a session to be stoppable,
the response to ``session-start`` must include ``"is-stoppable": true``.
See also :ref:`calls-sessionstart-docs`.

Implementation: :ref:`calls-sessionstop-docs`
