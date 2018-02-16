.. highlight:: none

.. _request-docs:

Sending a Message via OIOI
==========================

To send a message, your server issues a POST request to::

    https://api.plugsurfing.com/api/v4/request

.. note:: The staging server for testing is located at https://dev-api.plugsurfing.com/api/v4/request

.. important:: All the concepts explained here apply also to any server instance that you may create.
               If you expect any party to send requests to you using OIOI,
               make sure your servers accept calls as described here.

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

.. important:: OIOI is not a REST interface. Instead, it is simple JSON over HTTP.
               All requests are sent to the same endpoint.
               The receiver will know which resource to use based on the request body.

.. important:: All data must be UTF-8 encoded.

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

A more general code must always be accepted in parellel to the more
specific code.
For example: If a customer successfully starts a charging session,
the code ``000`` is valid, as well as the more specific ``011``.
The same is true for errors. If a client wants to authenticate a
customer, any ``14x`` error could be returned. At the same time,
a ``100`` could also be returned and must be accepted by the client.

+------------+------------------------------------------------------------+
| Error Code | Description                                                |
+============+============================================================+
| ``0xx``    | **Success**                                                |
+------------+------------------------------------------------------------+
| ``000``    | Success                                                    |
+------------+------------------------------------------------------------+
| ``011``    | Successfully started a charging session                    |
|            |                                                            |
|            | The customer is charging at the EVSE                       |
+------------+------------------------------------------------------------+
| ``012``    | Successfully authorized a charging session                 |
|            |                                                            |
|            | The customer must now plug in the cable to start           |
+------------+------------------------------------------------------------+
| ``1xx``    | **PlugSurfing Errors**                                     |
+------------+------------------------------------------------------------+
| ``100``    | System error                                               |
+------------+------------------------------------------------------------+
| ``101``    | Database error                                             |
+------------+------------------------------------------------------------+
| ``102``    | System timeout                                             |
+------------+------------------------------------------------------------+
| ``140``    | Authentication failed: No positive authentication response |
+------------+------------------------------------------------------------+
| ``141``    | Authentication failed: Invalid email or password           |
+------------+------------------------------------------------------------+
| ``142``    | Authentication failed: Invalid email                       |
+------------+------------------------------------------------------------+
| ``143``    | Authentication failed: Email already exists                |
+------------+------------------------------------------------------------+
| ``144``    | Authentication failed: Email does not exist                |
+------------+------------------------------------------------------------+
| ``145``    | Authentication failed: User token not valid                |
+------------+------------------------------------------------------------+
| ``180``    | Entity not found                                           |
+------------+------------------------------------------------------------+
| ``181``    | EVSE not found                                             |
+------------+------------------------------------------------------------+
| ``182``    | Session not found                                          |
+------------+------------------------------------------------------------+
| ``183``    | Company not found                                          |
+------------+------------------------------------------------------------+
| ``184``    | Vehicle not found                                          |
+------------+------------------------------------------------------------+
| ``185``    | Subscription plan not found                                |
+------------+------------------------------------------------------------+
| ``186``    | Group not found                                            |
+------------+------------------------------------------------------------+
| ``187``    | EVSE ID does not support direct pay                        |
+------------+------------------------------------------------------------+
| ``188``    | EVSE ID does not support remote stop                       |
+------------+------------------------------------------------------------+
| ``189``    | Reservation not found                                      |
+------------+------------------------------------------------------------+
| ``190``    | EVCO ID error                                              |
+------------+------------------------------------------------------------+
| ``191``    | EVCO ID not found                                          |
+------------+------------------------------------------------------------+
| ``192``    | EVCO ID locked                                             |
+------------+------------------------------------------------------------+
| ``193``    | EVCO ID has no valid payment method                        |
+------------+------------------------------------------------------------+
| ``194``    | EVCO ID has another active reservation                     |
+------------+------------------------------------------------------------+
| ``2xx``    | **Client Error**                                           |
+------------+------------------------------------------------------------+
| ``200``    | Client request error                                       |
+------------+------------------------------------------------------------+
| ``210``    | Invalid API key                                            |
+------------+------------------------------------------------------------+
| ``211``    | Invalid partner identifier                                 |
+------------+------------------------------------------------------------+
| ``220``    | API key not allowed to access the requested resource       |
+------------+------------------------------------------------------------+
| ``230``    | Invalid request format                                     |
+------------+------------------------------------------------------------+
| ``3xx``    | **Operator and EVSE Errors**                               |
+------------+------------------------------------------------------------+
| ``300``    | System error                                               |
+------------+------------------------------------------------------------+
| ``302``    | System timeout                                             |
+------------+------------------------------------------------------------+
| ``310``    | EVSE error                                                 |
+------------+------------------------------------------------------------+
| ``312``    | EVSE timeout                                               |
+------------+------------------------------------------------------------+
| ``320``    | EVSE already in use                                        |
+------------+------------------------------------------------------------+
| ``321``    | No EV connected to EVSE                                    |
+------------+------------------------------------------------------------+
| ``322``    | Connector with the same EVSE ID, but with different        |
|            | latitude/longitude exists                                  |
+------------+------------------------------------------------------------+
| ``323``    | EVSE already reserved                                      |
+------------+------------------------------------------------------------+
| ``330``    | EVSE does not support reservation                          |
+------------+------------------------------------------------------------+
| ``4xx``    | **Hub Errors**                                             |
+------------+------------------------------------------------------------+
| ``400``    | System error                                               |
+------------+------------------------------------------------------------+
| ``402``    | System timeout                                             |
+------------+------------------------------------------------------------+
| ``8xx``    | **Payment Provider Errors**                                |
+------------+------------------------------------------------------------+
| ``800``    | System error                                               |
+------------+------------------------------------------------------------+
| ``802``    | System timeout                                             |
+------------+------------------------------------------------------------+
| ``805``    | This user is not allowed to use this method                |
+------------+------------------------------------------------------------+
| ``830``    | Invalid format                                             |
+------------+------------------------------------------------------------+
| ``850``    | Invalid payment method                                     |
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
| ``880``    | PayPal error                                               |
+------------+------------------------------------------------------------+
