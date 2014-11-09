Statistic Information
#####################

All calls to **/stats/** endpoint work only with payed API account.

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
    :domain_count: total registered domains by registrar
    :tlds: named list of TLD object
    
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
    :domain_count: total registered domains by registrar
    :tlds: named list of TLD object
    
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
                Donuts-Inc": {
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

Sample Link: http://api.ntldstats.net/stats/registrars

.. _nTLDStats: http://ntldstats.com
