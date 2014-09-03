Public Informations
###################

All calls to **/i/** endpoint work without API token authentication.

API response format can be set to CSV as append /csv to the URL:

Sample Links:
  - http://api.ntldstats.net/i/tlds/csv
  - http://api.ntldstats.net/i/applications/csv


List tlds
*********

Command
=======

**GET /i/tlds**

Arguments
    -- None

Response
    :tlds: list of TLD objects

TLD Object
    :zone: name of tld, idn encoded
    :zone_utf8: name of tld in native language
    :delegated: true if tld is already delegated
    :applications: list of Small Application object
    :registry: Registry object (optional)
    :backend: Backend object (optional)
    :whois: Whois object (optional)

Small Application Object
    :id: id of application
    :applicant: name of applicant
    :status: current application status

Registry Object
    :id: id of Registry
    :name: name of Registry
    :info_url: public nTLDStats_ URL to get more informations about Registry
    :url: url of Registry

Backend Object
    :id: id of Backend
    :name: name of Backend
    :info_url: public nTLDStats_ URL to get more informations about Backend
    :url: url of Backend

Whois Object
    :hostname: hostname of whois server
    :charset: default charset of whois server
    :ipv6: true if whois server supports IPv6 connections
    :options: additional options to prefix whois request

Example
=======

Request

::

    GET /i/tlds

Response

::

    {
        "resData": {
            "tlds": [{
                "zone": "xn--ngbc5azd",
                "zone_utf8": "\u0634\u0628\u0643\u0629",
                "delegated": true,
                "applications": [{
                    "id": "1-1926-49360",
                    "applicant": "International Domain Registry Pty. Ltd.",
                    "status": "delegated"
                }],
                "registry": {
                    "name": "International Domain Registry Pty. Ltd.",
                    "id": "International-Domain-Registry-Pty-Ltd",
                    "info_url": "http:\/\/ntldstats.com\/registry\/International-Domain-Registry-Pty-Ltd",
                    "url": "http:\/\/www.dotshabaka.com"
                },
                "backend": {
                    "name": "ARI Registry Services",
                    "id": "ARI-Registry-Services",
                    "info_url": "http:\/\/ntldstats.com\/backend\/ARI-Registry-Services",
                    "url": "http:\/\/www.ariservices.com"
                },
                "whois": {
                    "hostname": "whois.nic.xn--ngbc5azd",
                    "charset": "ascii",
                    "ipv6": true,
                    "options": ""
                }
            }],
        },
        "code": 1000,
        "msg":"Command completed successfully",
    }

Sample Link: http://api.ntldstats.net/i/tlds

List new gtld applications
**************************

Command
=======

**GET /i/applications**

Arguments
    -- None

Response
    :applications: list of Application objects

Application Object
    :id: id of application
    :priority_number: priority number of application
    :label: name of label, idn encoded
    :label_utf8: name of label in native language
    :status: current application status as string
    :applicant: Applicant object
    :evaluation: Evaluation object
    :cpe_status: current CPE status (optional)

Applicant Object
    :name: name of Applicant
    :country_code: Country code indicated by applicant as principal place of business
    :primary_contact: Primary Contact object
    :suport_result: Result of support evaluation (optional)

Primary Contact Object
    :name: name of primary applicant contact
    :email: email of primary applicant contact

Evaluation Object
    :result: result of evaluation as string
    :pdf: link to official result PDF

Example
=======

Request

::

    GET /i/applications

Response

::

    {
        "resData": {
            "applications": [{
                "id": "1-1114-79381",
                "priority_number": "1016",
                "status": "delegated",
                "label": "schmidt",
                "label_utf8": "schmidt",
                "applicant": {
                    "name": "SALM S.A.S.",
                    "country_code": "FR",
                    "primary_contact": {
                        "name": "Jacques Haas",
                        "email": "jacques.haas@salm.fr"
                    }
                },
                "evaluation": {
                    "result": "Pass IE",
                    "pdf": "http:\/\/newgtlds.icann.org\/en\/program-status\/application-results\/ie-1-1114-79381-en.pdf"
                }
            }],
        },
        "code": 1000,
        "msg":"Command completed successfully",
    }

Sample Link: http://api.ntldstats.net/i/applications

List launch events
******************

Command
=======

**GET|POST /i/launch**

Arguments (to filter Response)
    :tld: filter by given tld
    :filterby: filter start/end by **start**, **end** or **inrange**, default **start**
    :start: either "empty" (no limit) or date as 'YYYY-MM-DD'
    :end: either "empty" (no limit) or date as 'YYYY-MM-DD'
    :stage: list of stages (**SR**, **LR**, **EA**, **GA** or **OT**)

Response
    :events: list of Event objects
    :filter: used filters

Event Object
    :tld: TLD object
    :stage: Stage object
    :start: DateTime of event start
    :end: DateTime of event end
    :name: name of event, only given if stage is **OT**,
    :description: additional informations as text
    :flags: list of Flag objects

Stage Object
    :id: ID of Stage
    :name: Name of Stage

Flag Object
    :id: ID of Flag
    :name: Name of Flag
    :description: additional informations as text
    :short_name: short cut name of Flag

Example
=======

Request

::

    POST /i/launch
    {
        "tld": "bar"
    }

Response

::

    {
        "resData": {
            "events": [{
                "tld": {
                    "zone": "bar",
                    "zone_utf8": "bar",
                    "registry": {
                        "name": "Punto 2012 Sociedad Anonima Promotora de Inversion de Capital Variable",
                        "id": "Punto-2012-Sociedad-Anonima-Promotora-de-Inversion-de-Capital-Variable",
                        "info_url": "http:\/\/ntldstats.com\/registry\/Punto-2012-Sociedad-Anonima-Promotora-de-Inversion-de-Capital-Variable",
                        "url": "http:\/\/nic.bar"
                    },
                    "backend": {
                        "name": "CentralNic",
                        "id": "CentralNic",
                        "info_url": "http:\/\/ntldstats.com\/backend\/CentralNic",
                        "url": "http:\/\/www.centralnic.com"
                    }
                },
                "stage": {
                    "id": "SR",
                    "name": "Sunrise"
                },
                "start": "2014-04-09T00:00:00Z",
                "end": "2014-06-08T00:00:00Z",
                "name": null,
                "description": null,
                "flags": []
            }, {
                "tld": {
                    "zone": "bar",
                    "zone_utf8": "bar",
                    "registry": {
                        "name": "Punto 2012 Sociedad Anonima Promotora de Inversion de Capital Variable",
                        "id": "Punto-2012-Sociedad-Anonima-Promotora-de-Inversion-de-Capital-Variable",
                        "info_url": "http:\/\/ntldstats.com\/registry\/Punto-2012-Sociedad-Anonima-Promotora-de-Inversion-de-Capital-Variable",
                        "url": "http:\/\/nic.bar"
                    },
                    "backend": {
                        "name": "CentralNic",
                        "id": "CentralNic",
                        "info_url": "http:\/\/ntldstats.com\/backend\/CentralNic",
                        "url": "http:\/\/www.centralnic.com"
                    }
                },
                "stage": {
                    "id": "LR",
                    "name": "Landrush"
                },
                "start": "2014-06-11T12:00:00Z",
                "end": "2014-07-09T07:00:00Z",
                "name": null,
                "description": null,
                "flags": []
            }, {
                "tld": {
                    "zone": "bar",
                    "zone_utf8": "bar",
                    "registry": {
                        "name": "Punto 2012 Sociedad Anonima Promotora de Inversion de Capital Variable",
                        "id": "Punto-2012-Sociedad-Anonima-Promotora-de-Inversion-de-Capital-Variable",
                        "info_url": "http:\/\/ntldstats.com\/registry\/Punto-2012-Sociedad-Anonima-Promotora-de-Inversion-de-Capital-Variable",
                        "url": "http:\/\/nic.bar"
                    },
                    "backend": {
                        "name": "CentralNic",
                        "id": "CentralNic",
                        "info_url": "http:\/\/ntldstats.com\/backend\/CentralNic",
                        "url": "http:\/\/www.centralnic.com"
                    }
                },
                "stage": {
                    "id": "OT",
                    "name": "Other"
                },
                "start": "2014-07-03T00:00:00Z",
                "end": "2014-07-31T23:59:00Z",
                "name": "Bar Family Names Sunrise",
                "description": "The purpose of this Sunrise is to allow resident Bar people to register their surnames under the .bar TLD prior to general availability. This is called the \u201cBar Family Names Sunrise\u201d or locally the \u201cSanrajz period za registraciju prezimena na .bar domenima\u201d.\r\n\r\nThis Sunrise is restricted to applicants meeting the strict application and eligibility requirements set forth in this Policy.",
                "flags": [{
                    "name": "Country restricted",
                    "short_name": "COR",
                    "description": "Registration is restricted for registrants from one country"
                }, {
                    "name": "Special Restrictions",
                    "short_name": "SPR",
                    "description": "Registration is restricted to registrants\/organizations named by Registry"
                }]
            }, {
                "tld": {
                    "zone": "bar",
                    "zone_utf8": "bar",
                    "registry": {
                        "name": "Punto 2012 Sociedad Anonima Promotora de Inversion de Capital Variable",
                        "id": "Punto-2012-Sociedad-Anonima-Promotora-de-Inversion-de-Capital-Variable",
                        "info_url": "http:\/\/ntldstats.com\/registry\/Punto-2012-Sociedad-Anonima-Promotora-de-Inversion-de-Capital-Variable",
                        "url": "http:\/\/nic.bar"
                    },
                    "backend": {
                        "name": "CentralNic",
                        "id": "CentralNic",
                        "info_url": "http:\/\/ntldstats.com\/backend\/CentralNic",
                        "url": "http:\/\/www.centralnic.com"
                    }
                },
                "stage": {
                    "id": "GA",
                    "name": "General Availability"
                },
                "start": "2014-07-14T12:00:00Z",
                "end": "2099-12-31T23:59:59Z",
                "name": null,
                "description": null,
                "flags": []
            }],
            "filter": {
                "start": "",
                "end": "",
                "stage": [],
                "tld": "bar",
                "filterby": "start"
            }
        },
        "code": 1000,
        "msg": "Command completed successfully"
    }

Sample Link: http://api.ntldstats.net/i/launch

List current CZDS requests
**************************

Command
=======

**GET /i/czds**

Arguments
    -- None

Response
    :total: Total Object
    :requests: list of Request Objects

Total Object
    :requests: total count of requests send
    :approved: total count of approved requests
    :pending: total count of current pending requests
    :expired: total count of expired requests
    :revoked: total count of revoked requests
    :denied: total count of denied requests
    :open: count of currently unrequested zones
    :zones: total count of zones available on CZDS
    
Request Object
    :id: CZDS Request ID
    :status: current status
    :zone: name of tld, idn encoded
    :zone_utf8: name of tld in native language
    :approve_date: DateTime when request approved
    :expire_date: DateTime when request expired
    :request_date: DateTime when request created
    :last_zone_update: DateTime when zone got last update
    :zones_count: Count of unique domains in last zone update
    :registry: Registry object
    :backend: Backend object

Registry Object
    :id: id of Registry
    :name: name of Registry
    :info_url: public nTLDStats_ URL to get more informations about Registry

Backend Object
    :id: id of Backend
    :name: name of Backend
    :info_url: public nTLDStats_ URL to get more informations about Backend

Example
=======

Request

::

    GET /i/czds

Response

::

    {
        "resData": {
            "total": {
                "requests": 633,
                "approved": 337,
                "pending": 29,
                "expired": 258,
                "revoked": 1,
                "denied": 8,
                "open": 0,
                "zones": 367
            },
            "requests": [{
                "id": 210385,
                "status": "pending",
                "zone": "top",
                "zone_utf8": "top",
                "approve_date": "0000-00-00 00:00:00",
                "expire_date": "0000-00-00 00:00:00",
                "request_date": "2014-08-21 00:00:00",
                "last_zone_update": "0000-00-00 00:00:00",
                "zones_count": 0,
                "registry": {
                    "name": "Jiangsu Bangning Science & Technology Co.,Ltd.",
                    "id": "Jiangsu-Bangning-Science-Technology-CoLtd",
                    "info_url": "http:\/\/ntldstats.com\/registry\/Jiangsu-Bangning-Science-Technology-CoLtd"
                },
                "backend": {
                    "name": "Jiangsu Bangning Science & technology Co.,Ltd.",
                    "id": "Jiangsu-Bangning-Science-technology-CoLtd",
                    "info_url": "http:\/\/ntldstats.com\/backend\/Jiangsu-Bangning-Science-technology-CoLtd"
                }
            }],
        },
        "code": 1000,
        "msg": "Command completed successfully"
    }

Sample Link: http://api.ntldstats.net/i/czds


.. _nTLDStats: http://ntldstats.com
