Statistic Information
#####################

All calls to **/stats/** endpoint only work with a beta API account.

TLD Statistics
**************

Command
=======

**GET /stats/tlds**

Arguments
    -- None

Response
    :stats: total stats object
    :tlds: named list of TLD objects

Total Stats Object
    :total_domains: total count of registered domains
    :total_tlds: total count of tlds
    
TLD Object
    :zone: name of tld, idn encoded
    :zone_utf8: name of tld in native language
    :registry: Registry object
    :backend: Backend object
    :current_stage: name of current stage
    :domain_count: total count of registered domains in this TLD
    
Registry Object
    :id: id of Registry
    :name: name of Registry
    :info_url: public nTLDStats_ URL to get more information about Registry
    :url: url of Registry

Backend Object
    :id: id of Backend
    :name: name of Backend
    :info_url: public nTLDStats_ URL to get more information about Backend
    :url: url of Backend

Example
=======

Request

::

    GET /stats/tlds

Response

::

    {
        "resData": {
            "stats": {
                "total_domains": 3097027,
                "total_tlds": 430
            },
            "tlds": { 
                "xyz": {
                    "zone": "xyz",
                    "zone_utf8": "xyz",
                    "registry": {
                        "name": "XYZ.COM LLC",
                        "id": "XYZCOM-LLC",
                        "info_url": "http:\/\/ntldstats.com\/registry\/XYZCOM-LLC",
                        "url": "http:\/\/nic.xyz"
                    },
                    "backend": {
                        "name": "CentralNic",
                        "id": "CentralNic",
                        "info_url": "http:\/\/ntldstats.com\/backend\/CentralNic",
                        "url": "http:\/\/www.centralnic.com"
                    },
                    "current_stage": "GA",
                    "domain_count": 704262
                }
            }
        },
        "code": 1000,
        "msg":"Command completed successfully",
    }

Sample Link: http://api.ntldstats.net/stats/tlds

Registrar Statistics
********************

Command
=======

**GET /stats/registrars**

Arguments
    -- None

Response
    :registrars: named list of Statistic objects

Statistic Object
    :registrar: Registrar object
    :tlds: named list of TLD objects
    
Registrar Object
    :id: id of Registrar
    :iana_id: registrar IANA id
    :name: name of Registrar
    :url: homepage of Registrar
    :registrar_group: Registrar Group object
    :domain_count: total registered domains
    
Registrar Group Object
    :name: name of Registrar Group
    :url: homepage of Registrar Group

TLD Object
    :zone: name of tld, idn encoded
    :zone_utf8: name of tld in native language
    :current_stage: name of current stage
    :domain_count: total count of registered domains in this TLD
    
Example
=======

Request

::

    GET /stats/registrars

Response

::

    {
        "resData": {
            "registrars": {
                "146-GoDaddycom-LLC": {
                    "registrar": {
                        "id": "146-GoDaddycom-LLC",
                        "iana_id": "146",
                        "name": "GoDaddy.com, LLC",
                        "url": "http:\/\/www.godaddy.com",
                        "domain_count": 487559,
                        "registrar_group": {
                            "name": "GoDaddy Group",
                            "url": "http:\/\/godaddy.com\/"
                        }
                    },
                    "tlds": {
                        "guru": {
                            "zone": "guru",
                            "zone_utf8": "guru",
                            "domain_count": 44145,
                            "current_stage": "GA"
                        },
                    }
                }
            }
        },
        "code": 1000,
        "msg":"Command completed successfully",
    }

Sample Link: http://api.ntldstats.net/stats/registrars

Backend Statistics
******************

Command
=======

**GET /stats/backends**

Arguments
    -- None

Response
    :backends: named list of Statistic objects

Statistic Object
    :backend: Backend object
    :tlds: named list of TLD objects

Backend Object
    :id: id of Backend
    :name: name of Backend
    :url: homepage of Backend
    :domain_count: total registered domains
    
TLD Object
    :zone: name of tld, idn encoded
    :zone_utf8: name of tld in native language
    :current_stage: name of current stage
    :domain_count: total count of registered domains in this TLD
    
Example
=======

Request

::

    GET /stats/backends

Response

::

    {
        "resData": {
            "backends": {
                "Donuts-Inc": {
                    "backend": {
                        "id": "Donuts-Inc",
                        "name": "Donuts Inc.",
                        "url": "http:\/\/www.donuts.co",
                        "domain_count": 1047140
                    },
                    "tlds": {
                        "guru": {
                            "zone": "guru",
                            "zone_utf8": "guru",
                            "domain_count": 75568,
                            "current_stage": "GA"
                        },
                    }
                }
            }
        },
        "code": 1000,
        "msg":"Command completed successfully",
    }

Sample Link: http://api.ntldstats.net/stats/backends

Registry Statistics
*******************

Command
=======

**GET /stats/registries**

Arguments
    -- None

Response
    :registries: named list of Statistic objects

Statistic Object
    :registry: Registry object
    :tlds: named list of TLD objects

Registry Object
    :id: id of Registry
    :name: name of Registry
    :url: homepage of Registry
    :domain_count: total registered domains
    
TLD Object
    :zone: name of tld, idn encoded
    :zone_utf8: name of tld in native language
    :current_stage: name of current stage
    :domain_count: total count of registered domains in this TLD
    
Example
=======

Request

::

    GET /stats/registries

Response

::

    {
        "resData": {
            "registries": {
                "Donuts-Inc": {
                    "registry": {
                        "id": "Donuts-Inc",
                        "name": "Donuts Inc.",
                        "url": "http:\/\/www.donuts.co",
                        "domain_count": 1047140
                    },
                    "tlds": {
                        "guru": {
                            "zone": "guru",
                            "zone_utf8": "guru",
                            "domain_count": 75568,
                            "current_stage": "GA"
                        },
                    }
                }
            }
        },
        "code": 1000,
        "msg": "Command completed successfully",
    }

Sample Link: http://api.ntldstats.net/stats/registries

Parking Statistics by TLD
*************************

Command
=======

**GET /stats/parking/tld**

Arguments
    -- None

Response
    :stats: Global Statistic object
    :tlds: named list of TLD Statistic objects

Global Statistic Object
    :total_domains: total count of registered domains
    :total_tlds: total count of tlds
    :parking_domains: total count of parking domains
    :no_ns: total count of domains without nameservers
    :parking_ns: total count of domains with parking nameservers
    :no_record: total count of domains without A record
    :parking_ip: total count of domains with parking IP
    :private_ip: total count of domains resolving to private IPs
    :parking_check: total count of domains returning parking websites
    :http_error: total count of domains with HTTP errors
    :redirect: total count of domains returning redirect code

TLD Statistic Object
    :stats: Statistic object
    :tld: TLD object

Statistic Object
    :parking_domains: total count of parking domains
    :no_ns: total count of domains without nameservers
    :parking_ns: total count of domains with parking nameservers
    :no_record: total count of domains without A record
    :parking_ip: total count of domains with parking IP
    :private_ip: total count of domains resolving to private IPs
    :parking_check: total count of domains returning parking websites
    :http_error: total count of domains with HTTP errors
    :redirect: total count of domains returning redirect code

TLD Object
    :zone: name of tld, idn encoded
    :zone_utf8: name of tld in native language
    :domain_count: total count of registered domains in this TLD
    
Example
=======

Request

::

    GET /stats/parking/tld

Response

::

    {
        "resData": {
            "stats": {
                "total_tlds": 431,
                "total_domains": 3097027,
                "parking_domains": 2054579,
                "no_ns": 11698,
                "parking_ns": 230587,
                "no_record": 487353,
                "parking_ip": 97251,
                "private_ip": 7198,
                "parking_check": 1220492,
                "http_error": 286100,
                "redirect": 279899
            },
            "tlds": {
                "xyz": {
                    "stats": {
                        "parking_domains": 485385,
                        "no_ns": 3356,
                        "parking_ns": 6129,
                        "no_record": 68282,
                        "parking_ip": 4190,
                        "private_ip": 3496,
                        "parking_check": 399932,
                        "http_error": 104691,
                        "redirect": 20200
                    },
                    "tld": {
                        "zone": "xyz",
                        "zone_utf8": "xyz",
                        "domain_count": 706699
                    }
                }
            }
        },
        "code": 1000,
        "msg": "Command completed successfully",
    }

Sample Link: http://api.ntldstats.net/stats/parking/tld

Parking Statistics by Registrar
*******************************

Command
=======

**GET /stats/parking/registrar**

Arguments
    -- None

Response
    :stats: Global Statistic object
    :tlds: named list of Registrar Statistic objects

Global Statistic Object
    :total_domains: total count of registered domains
    :total_tlds: total count of tlds
    :parking_domains: total count of parking domains
    :no_ns: total count of domains without nameservers
    :parking_ns: total count of domains with parking nameservers
    :no_record: total count of domains without A record
    :parking_ip: total count of domains with parking IP
    :private_ip: total count of domains resolving to private IPs
    :parking_check: total count of domains returning parking websites
    :http_error: total count of domains with HTTP errors
    :redirect: total count of domains returning redirect code

Registrar Statistic Object
    :stats: Statistic object
    :registrar: Registrar object

Statistic Object
    :parking_domains: total count of parking domains
    :no_ns: total count of domains without nameservers
    :parking_ns: total count of domains with parking nameservers
    :no_record: total count of domains without A record
    :parking_ip: total count of domains with parking IP
    :private_ip: total count of domains resolving to private IPs
    :parking_check: total count of domains returning parking websites
    :http_error: total count of domains with HTTP errors
    :redirect: total count of domains returning redirect code

Registrar Object
    :id: id of Registrar
    :iana_id: registrar IANA id
    :name: name of Registrar
    :url: homepage of Registrar
    :registrar_group: Registrar Group object
    :domain_count: total registered domains
    
Registrar Group Object
    :name: name of Registrar Group
    :url: homepage of Registrar Group

Example
=======

Request

::

    GET /stats/parking/registrar

Response

::

    {
        "resData": {
            "stats": {
                "total_tlds": 431,
                "total_domains": 3097027,
                "parking_domains": 2054579,
                "no_ns": 11698,
                "parking_ns": 230587,
                "no_record": 487353,
                "parking_ip": 97251,
                "private_ip": 7198,
                "parking_check": 1220492,
                "http_error": 286100,
                "redirect": 279899
            },
            "registrars": {
                "2-Network-Solutions-LLC": {
                    "stats": {
                        "parking_domains": 401623,
                        "no_ns": 37,
                        "parking_ns": 143,
                        "no_record": 15926,
                        "parking_ip": 6,
                        "private_ip": 28,
                        "parking_check": 385483,
                        "http_error": 7507,
                        "redirect": 2862
                    },
                    "registrar": {
                        "domain_count": 413441,
                        "id": "2-Network-Solutions-LLC",
                        "iana_id": "2",
                        "name": "Network Solutions, LLC",
                        "info_url": "http:\/\/ntldstats.com\/registrar\/2-Network-Solutions-LLC",
                        "registrar_group": {
                            "name": "Web.com",
                            "url": "https:\/\/www.web.com\/"
                        }
                    }
                }
            }
        }
        "code": 1000,
        "msg": "Command completed successfully",
    }

Sample Link: http://api.ntldstats.net/stats/parking/registrar

.. _nTLDStats: http://ntldstats.com
