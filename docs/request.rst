.. highlight:: none

.. _request-docs:

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
Otherwise, the HTTP response code will not be 200 and more information about the error will be inside the response body.

Possible HTTP response codes and their meanings:

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
|          | One or more of the requested entities were not found.                                                    |
+----------+----------------------------------------------------------------------------------------------------------+
| ``5xx``  | **Server Error.**                                                                                        |
|          |                                                                                                          |
|          | Errors in the ``500``-``599`` range (such as ``500`` or ``503``)                                         |
|          | indicate that there was an internal error in the server while trying to process the request,             |
|          | or that the server is temporarily unavailable (for example, because of timeouts).                        |
|          |                                                                                                          |
|          | You must retry later, honoring any Retry-After header included in the response.                          |
|          |                                                                                                          |
|          | Your services must implement exponential back-off.                                                       |
+----------+----------------------------------------------------------------------------------------------------------+

OIOI Response Codes
~~~~~~~~~~~~~~~~~~~

.. note:: OIOI Error codes are not part of the OIOI response, yet.
          These codes will be added to the OIOI shortly.

+------------+------------------------------------------------------------+
| Error Code | Description                                                |
+============+============================================================+
| ``0xx``    | **PlugSurfing Errors**                                     |
+------------+------------------------------------------------------------+
| ``000``    | System error                                               |
+------------+------------------------------------------------------------+
| ``001``    | Database error                                             |
+------------+------------------------------------------------------------+
| ``002``    | System timeout                                             |
+------------+------------------------------------------------------------+
| ``040``    | Authentication failed: No positive authentication response |
+------------+------------------------------------------------------------+
| ``041``    | Authentication failed: Invalid email or password           |
+------------+------------------------------------------------------------+
| ``042``    | Authentication failed: Invalid email                       |
+------------+------------------------------------------------------------+
| ``043``    | Authentication failed: Email already exists                |
+------------+------------------------------------------------------------+
| ``044``    | Authentication failed: Email does not exist                |
+------------+------------------------------------------------------------+
| ``050``    | No valid payment method                                    |
+------------+------------------------------------------------------------+
| ``080``    | EVSE ID unknown                                            |
+------------+------------------------------------------------------------+
| ``090``    | EVCO ID error                                              |
+------------+------------------------------------------------------------+
| ``091``    | EVCO ID unknown                                            |
+------------+------------------------------------------------------------+
| ``092``    | EVCO ID locked                                             |
+------------+------------------------------------------------------------+
| ``1xx``    | **Client Error**                                           |
+------------+------------------------------------------------------------+
| ``100``    | Client request error                                       |
+------------+------------------------------------------------------------+
| ``110``    | Invalid API key                                            |
+------------+------------------------------------------------------------+
| ``120``    | API key not allowed to access the requested resource       |
+------------+------------------------------------------------------------+
| ``130``    | Invalid request format                                     |
+------------+------------------------------------------------------------+
| ``2xx``    | **Operator and EVSE Errors**                               |
+------------+------------------------------------------------------------+
| ``200``    | System error                                               |
+------------+------------------------------------------------------------+
| ``202``    | System timeout                                             |
+------------+------------------------------------------------------------+
| ``210``    | EVSE error                                                 |
+------------+------------------------------------------------------------+
| ``212``    | EVSE timeout                                               |
+------------+------------------------------------------------------------+
| ``220``    | EVSE already in use                                        |
+------------+------------------------------------------------------------+
| ``221``    | No EV connected to EVSE                                    |
+------------+------------------------------------------------------------+
| ``3xx``    | **Hub Errors**                                             |
+------------+------------------------------------------------------------+
| ``300``    | System error                                               |
+------------+------------------------------------------------------------+
| ``302``    | System timeout                                             |
+------------+------------------------------------------------------------+
| ``8xx``    | **Payment Provider Errors**                                |
+------------+------------------------------------------------------------+
| ``800``    | System error                                               |
+------------+------------------------------------------------------------+
| ``802``    | System timeout                                             |
+------------+------------------------------------------------------------+
| ``830``    | Invalid format                                             |
+------------+------------------------------------------------------------+
| ``860``    | Bank transfer error                                        |
+------------+------------------------------------------------------------+
| ``861``    | Bank account not valid                                     |
+------------+------------------------------------------------------------+
| ``862``    | Invalid name                                               |
+------------+------------------------------------------------------------+
| ``863``    | Invalid IBAN                                               |
+------------+------------------------------------------------------------+
| ``864``    | Invalid BIC                                                |
+------------+------------------------------------------------------------+
| ``870``    | Credit card error                                          |
+------------+------------------------------------------------------------+
| ``871``    | Credit card not valid                                      |
+------------+------------------------------------------------------------+
| ``872``    | Invalid card holder name                                   |
+------------+------------------------------------------------------------+
| ``874``    | Invalid credit card number                                 |
+------------+------------------------------------------------------------+
| ``875``    | Invalid expiration date                                    |
+------------+------------------------------------------------------------+
| ``876``    | Invalid CVC                                                |
+------------+------------------------------------------------------------+
