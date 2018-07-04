.. highlight:: js

.. _calls-usersubscriptiongetactive-docs:

Get active user subscription
============================

Request
-------

``"user-subscription-get-active"`` identifies the call as a user-subscription-get-active call.

Fields
~~~~~~

user
    This field identifies the customer (object).

    identifier-type
        How to identify the user (string).

        The identifier-type can be one of:

        * ``"evco-id"``
        * ``"rfid"``
        * ``"username"``
        * ``"token"``

    identifier
        The identifier is something that uniquely identifies the customer,
        depending on the identifier-type (string).

    token (optional)
        A token can be used to authenticate the user (string).

        For example: if the identifier type is username and the identifier is the user's username,
        then token is used for authentication instead of a password.

Response
--------

Fields
~~~~~~

subscription
    This field contains the active user subscription (object).

    id
        Subscription id (int)

    subscribed-at
        Subscription start date (string; format: ``"2016-05-09T04:08:06+02:00"``)

    expired-at
        Subscription expiration date (string; format: ``"2016-05-09T04:08:06+02:00"``)

    cancelled-at (optional)
        Subscription cancellation date (string; format: ``"2016-05-09T04:08:06+02:00"``)

    payment-method-reference (optional)
        The internal reference to refer to user's payment method (string).

    subscription-plan
        Subscription plan of this subscription (object)

        id
            Subscription plan id (int)

        localized-names
            Localized name of the subscription plan (object, format: ``{"language": "text"}``)

            language
                Localization language (string).
                Expected is a lowercase, two-character string in accordance with `ISO 639-1:2002`_.
            text
                Localized name of the subscription plan (string)

        localized-descriptions
            Localized desciption of the subscription plan (object, format: ``{"language": "text"}``)

            language
                Localization language (string).
                Expected is a lowercase, two-character string in accordance with `ISO 639-1:2002`_.
            text
                Localized desciption of the subscription plan (string)

        duration
            Minimum contract duration in months (int)
            Valid values are 6 or 12

        valid-from
            Start date of the subscription offer (string; format: ``"2016-05-09T04:08:06+02:00"``)

        valid-to
            End date of the subscription offer (string; format: ``"2016-05-09T04:08:06+02:00"``)

        monthly-price
            Monthly gross price of the subscription plan (string; format ``"1.23"``)

        currency
            The currency of the subscription plan monthly fee (string; format ``"EUR"``).

        country (optional)
            Country where this subscription is valid for. Only applied to sessions in that country (string)
            Please use international two letter codes (ISO 3166-1 alpha-2).

        ac-component
            AC component (object)

            free-minutes
                Free minutes for each session, e.g. first “60” minutes are free for each session (int)

            parking-time-price
                Fixed price per minute for any CPO (string; format ``"1.23"``)

            parking-time-step-size
                Step size in seconds (int)

            discount-percent
                Discount of total charging costs in percent (int)

        dc-component
            DC component (object)

            free-minutes
                Free minutes for each session, e.g. first “60” minutes are free for each session (int)

            parking-time-price
                Fixed price per minute for any CPO (string; format ``"1.23"``)

            parking-time-step-size
                Step size in seconds (int)

            discount-percent
                Discount of total charging costs in percent (int)


HTTP Status codes
~~~~~~~~~~~~~~~~~

200 OK
    The request was processed successfully.

Result codes
~~~~~~~~~~~~
0
    Success
140
    Authentication failed: No positive authentication response
144
    Authentication failed: Email does not exist
145
    Authentication failed: User token not valid

Examples
--------

Request::

    {
        "user-subscription-get-active": {
            "user": {
                "identifier-type": "username",
                "identifier": "some_user",
                "token": "b3853b6d910849f3b4392555b8acb984"
            }
        }
    }

Response::

    {
      "subscription": [
        {
          "id": 1,
          "subscribed-at": "2018-06-01T13:24:27+02:00",
          "expired-at": "2020-10-10T00:00:00+02:00",
          "cancelled-at": null,
          "payment-method-reference": "12345678",
          "subscription-plan": {
            "id": 2,
            "localized-names": {
                "en": "Name",
                "de": "Name"
              }
            },
            "localized-descriptions": {
                "en": "Description",
                "de": "Beschreibung"
              }
            },
            "duration": 12,
            "valid-from": "2018-05-18T00:00:00+02:00",
            "valid-to": "2018-12-15T00:00:00+01:00",
            "monthly-price": "33.00",
            "currency": "EUR",
            "country": "DE",
            "ac-component": {
              "free-minutes": 30,
              "parking-time-price": "5.00",
              "parking-time-step-size": 1,
              "discount-percent": 10
            },
            "dc-component": {
              "free-minutes": 10,
              "parking-time-price": "5.00",
              "parking-time-step-size": 1,
              "discount-percent": 5
            }
          }
        }
      ],
      "result": {
        "code": 0,
        "message": "Success."
      }
    }
