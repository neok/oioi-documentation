.. _emp-poi-docs:

Receiving POIs
==============
As an EMP, you can connect to a CPO to display their POI data and allow your customers to charge at the CPO's charging stations.
For example to display charging stations on an app's map.

.. note:: For EMPs, OIOI does not offer a full download of all available data.
          Please use the provided methods to display geographically limited data to your users.

.. note:: The total number of stations returned per request is limited,
          regardless of the geographical dimensions.

.. warning:: A CPO may cancel your access if your API key is associated with malicious behaviour.

.. _emp-poi-area-docs:

Displaying stations in an area
------------------------------
To display basic data about stations on a map or in a list,
you can get stations by providing a surface (via latitude/longitude).

Implementation: :ref:`calls-stationgetsurface-docs`

.. _emp-poi-details-docs:

Displaying details of a station
-------------------------------
If you want to display more detailed information,
you can query for those by a station's ID.

Implementation: :ref:`calls-stationgetbyids-docs`
