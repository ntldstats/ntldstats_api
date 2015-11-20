Overview
########

nTLDstats.com API beta
**********************

1. What is this beta about?
In this beta we will give interested parties the opportunity to check out our new API. All data displayed on our website will be accessible through it, without limitations like rate limits, etc.

2. How long will the beta be available?
Unfortunately, we don't know yet. We will, though, send a 2 weeks notice prior to shutdown of the beta API to every participant.

3. What should I do if I encounter an error / something is not working?
Please give us as much information as possible related to the error you ran into. Send those informations to mail@ntldstats.com and we will get back to you as soon as possible.

[Request API beta Access](https://ntldstats.com/signup)


Request Format
**************

The base URL for all API resources is **http://api.ntldstats.net/**. All data is sent as JSON. All arguments must be send JSON encoded by POST.

Example
=======

::

    POST /domains/create
    Content-Type: application/json
    {"domain":"test.guru","iana_id":1,"registration_date":"2014-01-01T03:10:00Z","registrant_handle":"ABC-1234567","nameservers":["ns1.example.com","ns2.example.com"]}

Response Format
***************

Status codes are used properly. If you get a 200 response, you can expect the normal response body as documented. Otherwise the response body will contain a plain text error message.

For example, if you don’t include the Authorization header, you will get a 401 UNAUTHORIZED status code.

Standard Response Fields
************************

All response have at least a **code** and a **msg** field. Calls which return additional data will return a **resData** field.

Successful call response example:

::

	{
		"code": 1000,
		"msg": "Command completed successfully"
	}

The returned MIME type from requests is always

::

	application/json

All result codes base on RFC5730_ (Extensible Provisioning Protocol, EPP)

Authentication
**************

You need a valid API Token to use our API. Please sign in to the dashboard and generate a new token if you haven't done it by now.

The API needs you to provide the API Token either as HTTP Header **X-API-TOKEN** or as HTTP Basic Authenticate username on every request. It is also possible to post it as URL parameter **token** append to every endpoint.

Errors
******

All error responses are being delivered in following format, with the corresponding status code:

::

    {
        "code": 2003,
        "msg": "Required parameter missing",
        "resData": {
            "elem": "domains"
        }
    }

Units
*****

- Durations will always be in seconds.
- Timestamps will always be in RFC3339_ format (e.g. *2012-05-14T17:54:16Z*). Timestamps from the API will always be UTC.


.. _RFC5730: http://tools.ietf.org/html/rfc5730
.. _RFC3339: http://tools.ietf.org/html/rfc3339
