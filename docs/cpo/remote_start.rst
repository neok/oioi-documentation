.. _cpo-remote-start-docs:

Receiving Remote Starts
=======================

Starting a Session
------------------
Whenever PlugSurfing wants to start a session in your network,
we will send a ``session-start`` request.
If the start is successful and the session is stoppable,
the response has to contain a ``session-id``.

.. toctree::
   :maxdepth: 2

   ../calls/session_start

Stopping a Session
------------------
Whenever PlugSurfing wants to stop a running session,
we will send a ``session-stop`` request.

.. toctree::
   :maxdepth: 2

   ../calls/session_stop
