.. _cpo-cdr-docs:

Sending CDRs
============
CDRs are the basis of all billing and clearing.
A CDR contains all required information about a finished session,
e.g. the customer or the consumed energy.

.. note:: You can also use this method to send information about sessions that just started or are still ongoing.
          To do this, simply omit optional data that is not available at the moment, e.g. the session interval's stop time.

Implementation: :ref:`calls-sessionpost-docs`
