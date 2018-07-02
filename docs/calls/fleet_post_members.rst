.. highlight:: js

.. _calls-fleetpostmembers-docs:

Fleet Post Member
=================

Request
-------

``"fleet-post-members"`` identifies the call as fleet-post-members call.

Fields
~~~~~~
partner-identifier
    The partner identifier of the owner of this fleet. (string)

members
    An array of fleet members (array of objects).

    fleet-member-uid
        Id of fleet member provided by Fleet. This shall not be changed by MSP (integer).

    external-id (optional)
        Fleet Owner's reference/ID for this Fleet Member. Managed by Fleet (string; max length 20 characters).

    contact
        Fleet member contact details (object).

        first-name
            (string; max length 50 characters)

        last-name
            (string; max length 50 characters)

        title (optional)
            Addressing title: Mr, Ms, Mrs, Dr, Prof. (string; max length 10 characters)

        job-title (optional)
            (string; max length 20 characters)

        phone (optional)
            (string; max length 20 characters)

        email (optional)
            (string; max length 50 characters)

    address
        The address where the fleet member lives (object).

        address-line-1
            (string; max length 50 characters)

        address-line-2 (optional)
            (string; max length 50 characters)

        postal-code (optional)
            (string; max length 10 characters)

        city
            (string; max length 50 characters)

        state-province (optional)
            (string; max length 20 characters)

        country
            ISO 3166-1 alpha-2 code for countries (string; length 2 characters).

    default-language
        ISO_639-1 2 letter language code (string; length 2 characters).

    fleet-id
        Fleet id of the fleet that Fleet Member belongs to (string; max length 10 characters).

    fleet-name
        Descriptive name of the fleet (string; max length 50 characters).

    fleet-cpo-id
        The operator id associated with the fleet in format <country><party>, e.g. DE8PS, NLALL, etc (string; length 5 characters).
        This will be used to associate this user to the correct Fleet where we have to send the bill for the users’ sessions, also public ones.

    fleet-reference-id (optional)
        Fleet Owner's reference for this fleet (string; max length 20 characters).

    evses (optional)
        List of EVSEs of the fleet member's charge points, includes reimbursement information (array of objects).

        fm-evse-uid
            (integer)

        evse-id
            (string; max length 50 characters)

        reimbursement-fee
            An array of Fleet Member Reimbursements (array of objects).

            date-start
                Start date as of when reimbursement fee is valid (string; format: ``"2014-06-23T18:32:49+02:00"``).
                If this is not the first reimbursement record, then this date start must be equal to the previous date end so that there will be no gap in between.

            date-end (optional)
                End date of reimbursement fee (string; format: ``"2014-06-23T18:32:49+02:00"``).

            allow-reimbursement
                True if reimbursement is allowed, false if not allowed (boolean).

            reimbursement-iban (optional)
                IBAN bank account number to reimburse to (string; max length 50 characters).
                Can be null or empty if allow reimbursement == false.

            reimbursement-full-name (optional)
                Full name of bank account holder (string; max length 50 characters).
                Can be null or empty if allow reimbursement == false.

            kwh-reimbursement
                In the major denominator of the local currency. E.g. 0.31 for "31 cents in Germany" (float).
                Will be 0 if no reimbursement is allowed or needed.

            reimbursement-currency
                ISO 4217 3 char currency code (string; length 3 characters).



Response
--------

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
230
    Invalid request format

Examples
--------

Request::

    {
        "fleet-post-members": {
            "members": [
                {
                    "fleet-member-uid": 1234,
                    "external-id": "Member 1234",
                    "address": {
                        "address-line-1": "Torgauer Str.",
                        "address-line-2": "12 - 15",
                        "postal-code": "10829",
                        "city": "Berlin",
                        "state-province": "Berlin",
                        "country": "DE"
                    },
                    "contact": {
                        "first-name": "Jack",
                        "last-name": "Daniels",
                        "title": "Mr.",
                        "job-title": "CEO",
                        "phone": "+4915184512991",
                        "email": "jack@daniels.com"
                    },
                    "default-language": "en",
                    "fleet-id": "Fleet 1",
                    "fleet-name": "Allego Fleet 1",
                    "fleet-cpo-id": "NLALL",
                    "fleet-reference-id": "ref123",
                    "evses": [
                        {
                            "fm-evse-uid": 12345,
                            "evse-id": "NL*ALL*E0008A3",
                            "reimbursement-fee": [
                                {
                                    "date-start": "2014-06-23T18:32:49+02:00",
                                    "date-end": "2014-06-23T18:32:49+02:00",
                                    "allow-reimbursement": true,
                                    "reimbursement-iban": "DE89370400440532013000",
                                    "reimbursement-full-name": "Jack Daniels",
                                    "kwh-reimbursement": 10.0,
                                    "reimbursement-currency": "EUR"
                                }
                            ]
                        }
                    ]
                }
            ]
        }
    }

Response::

    {
        "result": {
            "code": 0,
            "message": "Success."
        }
    }
