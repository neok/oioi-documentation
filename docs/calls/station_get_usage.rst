.. highlight:: js

.. _calls-stationgetusage-docs:

Station Get Usage
=================

Request
-------

``"station-get-usage"`` identifies the call as a station-get-usage call.

Fields
~~~~~~

station-id
    A station ID (integer).

Response
--------

Fields
~~~~~~
Optional fields may be omitted or have the value ``null``.

station-usage
    This field contains the station usage data (object).

    last-7-days-usage-count
        Sessions within the last 7 days (integer).

    last-30-days-usage-count
        Sessions within the last 7 days (integer).

    last-station-usage-date
        Date of the last usage of the station (string).

        The date/time format is RFC3339 (``Y-m-d\TH:i:sP``).

HTTP Status codes
~~~~~~~~~~~~~~~~~

200 OK
    The request was processed successfully.

Result codes
~~~~~~~~~~~~
0
    Success
181
    EVSE not found

Examples
--------

Request::

    {
        "station-get-usage": {
            "station-id": 1770
        }
    }

Response::

    {
        "station-usage": {
            "last-7-days-usage-count": 2,
            "last-30-days-usage-count": 4,
            "last-station-usage-date": "2017-04-12T19:10:02+02:00"
        }
    }
