.. highlight:: js

.. _calls-userverify-docs:

User Verify
===========

Request
-------

Fields
~~~~~~

.. note:: The field "language" is optional.

username
    The username of the user (string).
password
    The plain password or token of the user (string).
is-token
    Defines whether the supplied password is actually a token (boolean).

    If ``is-token`` is ``true``, the password is interpreted as a token of the user.
    Otherwise, the password is interpreted as the plain password of the user.
language
    The locale of the user (string).

    Expected is a lowercase, two-character string in accordance with `ISO 639-1:2002`_.

Response
--------

Fields
~~~~~~

verified
    ``true``, if the verification was a success, ``false`` otherwise (boolean).
token
    A token to authenticate the user in future requests (string).
    
    Keep this token.
    When you make future requests where the user needs to be authenticated,
    you supply this token with the request.

Status codes
~~~~~~~~~~~~

200 OK
    The request was processed successfully.
    The username and password/token are correct.
401 Unauthorized
   The username does not exist or the username and password/token did not match.

Examples
--------

Request::

    {
        "user-verify": {
            "username": "your-user",
            "password": "mypassword",
            "is-token": false,
            "language": "en"
        }
    }

Response::

    {
        "user": {
            "verified": true,
            "token": "e2af72d7a9084431ab0b1a5c42df7745"
        }
    }

.. _iso 639-1:2002: https://en.wikipedia.org/wiki/ISO_639-1
