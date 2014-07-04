Public Informations
###################

All calls to **/i/** endpoint work without API token authentication.

Get detailed list of all domains
********************************

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
    :registry: Registry object (optional)
    :backend: Backend object (optional)
    :whois: Whois object (optional)

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

Get list of launch events
*************************

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

.. _nTLDStats: http://ntldstats.com
