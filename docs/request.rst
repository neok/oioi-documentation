.. highlight:: none

Sending a Message to OIOI
=========================

To send a message, your server issues a POST request to::

    https://api.plugsurfing.com/api/v3/request

.. note:: The staging server for testing is located at https://dev-api.plugsurfing.com/api/v3/request

A message request is made of 2 parts: HTTP header and HTTP body.
The HTTP header must contain the following headers::

    Authorization: key=<your-API-key>
    Content-Type: application/json

The HTTP body must contain the JSON request.
Example HTTP request::

    Content-Type: application/json
    Authorization: key=a39ff3fb-fe0a-40a3-bdde-df6372c07c89

    {
        "station-get-by-center-radius": {
            "center-lat": 52.5167,
            "center-long": 13.3833,
            "radius": 100,
            "unit": "km"
        }
    }

Response
--------

If the request was valid and successful,
the response will contain the requested data or information about the success.
Otherwise, the HTTP Response Code will not be 200 and more information about the error will be inside the response body.

Possible response codes and their meanings:

+----------+----------------------------------------------------------------------------------------------------------+
| Response | Description                                                                                              |
+==========+==========================================================================================================+
| ``200``  | **Success.**                                                                                             |
|          | The request was handled successfully.                                                                    |
|          |                                                                                                          |
|          | The response body will contain more details about the message status in JSON format.                     |
+----------+----------------------------------------------------------------------------------------------------------+
| ``4xx``  | **Error.**                                                                                               |
|          | Something was wrong with your request.                                                                   |
|          |                                                                                                          |
|          | The response body will contain more information in JSON format.                                          |
|          |                                                                                                          |
|          | The property error will contain more detailed information as to what was wrong.                          |
+----------+----------------------------------------------------------------------------------------------------------+
| ``400``  | **Bad request.**                                                                                         |
|          | Your request contains data and/or is in a format that is not allowed.                                    |
+----------+----------------------------------------------------------------------------------------------------------+
| ``401``  | **Unauthorized.**                                                                                        |
|          | Your request contains user data that is not authenticated or athorized.                                  |
+----------+----------------------------------------------------------------------------------------------------------+
| ``403``  | **Forbidden.**                                                                                           |
|          | You do not have access to this method and/or resource.                                                   |
+----------+----------------------------------------------------------------------------------------------------------+
| ``404``  | **Not Found.**                                                                                           |
|          | One or more of the requested stations were not found.                                                    |
+----------+----------------------------------------------------------------------------------------------------------+
| ``5xx``  | **Server Error.**                                                                                        |
|          |                                                                                                          |
|          | Errors in the ``500``-``599`` range (such as ``500`` or ``503``)                                         |
|          | indicate that there was an internal error in the PlugSurfing server while trying to process the request, |
|          | or that the server is temporarily unavailable (for example, because of timeouts).                        |
|          |                                                                                                          |
|          | You must retry later, honoring any Retry-After header included in the response.                          |
|          |                                                                                                          |
|          | Your servers must implement exponential back-off.                                                        |
+----------+----------------------------------------------------------------------------------------------------------+
