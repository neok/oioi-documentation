.. highlight:: js

.. _calls-userregister-docs:

User Register
=============

Request
-------

.. note:: The field "language" is optional.

Fields
~~~~~~

username
    The desired username of the new user (string).
email
    The email of the new user (string).
password
    The plain password of the new user (string).
language
    The locale of the new user (string).
    Expected is a lowercase, two-character string in accordance with `ISO 639-1:2002`_.

Response
--------

Fields
~~~~~~

registered
    ``true``, if the registration was a success, ``false`` otherwise (boolean).
token
    A token to authenticate the user in future requests (string).
    Keep this token.
    When you make future requests where the user needs to be authenticated,
    you supply this token with the request.
evco-id
    The EVCO ID of the user (string).
    See also :ref:`EVCO ID <glossary-evco-id>`

Status codes
~~~~~~~~~~~~

200 OK
    The request was processed successfully.
    The user now exists in the system.
400 Bad Request
    The user could not be registered.
    This is due to the email or username already being taken.

Examples
--------

Request::

    {
        "user-register": {
            "username": "user",
            "email": "name@mail.com",
            "password": "plain-password",
            "language": "en"
        }
    }

Response::

    {
        "user": {
            "registered": true,
            "token": "e2af72d7a9084431ab0b1a5c42df7745",
            "evco-id": "DE*8PS*123456*7"
        }
    }

.. _iso 639-1:2002: https://en.wikipedia.org/wiki/ISO_639-1
