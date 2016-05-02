.. _cpo-remote-start-docs:

Receiving Remote Starts
=======================

Starting a Session
------------------
Whenever PlugSurfing wants to start a session in your network,
PlugSurfing will send a ``session-start`` request.
PlugSurfing will analyze the CPO's response and display an appropriate
message to the user.

Implementation: :ref:`calls-sessionstart-docs`

Stopping a Session
------------------
Whenever a user wants to stop a running session,
PlugSurfing will send a ``session-stop`` request.

Implementation: :ref:`calls-sessionstop-docs`
