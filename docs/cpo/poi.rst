.. _cpo-poi-docs:

Sending POI Data
================
In order to add your stations to the network,
The EMP has to to know about your charging station locations and attributes.

POI is split into two sections:

* :ref:`cpo-poi-static-docs`
* :ref:`cpo-poi-dynamic-docs`

Static data is data that does not change very often,
including for example the address and latitude/longitude of a station.

Dynamic data is the name for the statuses of the connectors.
This will show the EV driver whether a connector is currently available or not.

.. _cpo-poi-static-docs:

Sending Static Data
-------------------
The CPO must send all stations via OIOI.
In the beginning, there will be a one-time push of all existing charging stations.
From then on, only new stations and station deletions will be pushed.

It is possible that a connected CPO will send stations from multiple CPOs.
It is also possible that the EMP already has some of those CPOs listed in their database.
Therefore, the EMP needs to be able to associate the pushed stations' CPOs with existing CPOs in the database.
Before the CPO pushes their first station, they need to inform the EMP about their internal identifiers for all given CPOs.
Then, when the CPO pushes a station with a certain CPO identifier that may be unique to the CPO's system,
the EMP knows which CPO to pick from their database.

**Summary:** For a new CPO, pushing POI data is done in three steps:

1. Setting up CPOs
2. Full load of all existing charging stations (push)
3. Continuously sending updates for new and existing charging stations (push)

Implementation: :ref:`calls-stationpost-docs`

.. _cpo-poi-dynamic-docs:

Sending Dynamic Data
--------------------
When the status of a connector changes,
the CPO must send a ``connector-post-status`` request to push the change.

.. note:: PlugSurfing only accepts dynamic data changes if they are associated to stations that were pushed by the same partner.

Implementation: :ref:`calls-connectorpoststatus-docs`
