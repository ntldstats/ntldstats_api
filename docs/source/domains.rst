Domains
#######

Post a new domain
*****************

Command
=======

**POST /domains/create**

Arguments
    :domain: domain name to create
    :iana_id: registrar IANA id
    :registration_date: date of registration
    :registrant_handle: handle of registrant of domain (optional)
    :nameservers: list of nameservers

Response
    :total: number of domains added
    :job_id: id of created job

Example
=======

Request

::

    POST /domains/create
    {
        "domain": "test.guru",
        "iana_id": 0001,
        "registration_date": "2014-01-01T03:10:00Z",
        "registrant_handle": "ABC-1234567",
        "nameservers": [
            "ns1.example.com",
            "ns2.example.com"
        ]
    }

Response

::

    {
        "resData": {
            "total": 1,
            "job_id": "7635318e-8f50-510c-b2a2-27de5cc691f1"
        },
        "code": 1001,
        "msg": "Command completed successfully; action pending"
    }

Upload file with multiple domains
*********************************

Command
=======

**PUT|POST /domains**

Arguments
    -- None

Response
    :total: number of domains added
    :job_id: id of created job

To post multiple domains in one request, you can simply send all data as CSV, where each field is separated by a **;**.

Example
=======

::
    xn--domainname.tld;1;2014-02-01T23:00.00Z;ABC1234;NS1.EXAMPLE.COM;NS2.EXAMPLE.COM

This file could be send by either POST Request (Default HTTP file upload, field named 'domains') or PUT Request (file content as request payload).

