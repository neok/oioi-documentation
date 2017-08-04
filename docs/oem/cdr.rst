.. _oem-cdr-docs:

Receiving CDRs
==============
CDRs are the basis of all billing and clearing.
A CDR contains all required information about a session,
e.g. the customer or the consumed energy.

.. note:: A :ref:`Roaming Platform <glossary-roaming-platform>` can also use this method to send information about sessions that just started or are still ongoing.
          To do this, the Roaming Platform omits optional data that is not available at the moment, e.g. the session interval's stop time.

* **Role:** Receiver
* **Implementation:** :ref:`calls-sessionpost-docs`
