.. _cpo-poi-docs:

Sending POI Data
================
In order for PlugSurfing to enable its users to charge in your network,
we have to to know about your charging stations.

POI is split into two sections:

* :ref:`cpo-poi-static-docs`
* :ref:`cpo-poi-dynamic-docs`

Static data is data that does not change very often,
including for example the address and latitude/longitude of a station.

Dynamic data is the name for the statuses of the connectors.
This will show the user whether a connector is currently available or not.

.. _cpo-poi-static-docs:

Sending Static Data
-------------------
When the status of a connector changes, PlugSurfing expects the CPO to send
a ``connector-post-status`` request.
The update will be immediately visible to all customers.

.. toctree::
   :maxdepth: 2

   ../calls/station_post

.. _cpo-poi-dynamic-docs:

Sending Dynamic Data
--------------------
When the status of a connector changes, PlugSurfing expects the CPO to send
a ``connector-post-status`` request.
The update will be immediately visible to all customers.

.. toctree::
   :maxdepth: 2

   ../calls/connector_post_status
