nTLDStats API
#############

The NTLDStats_ API enables your own application to interact with our website.
The following pages list the resources that our API provides.

Documentation Format
********************

Each API method you can call is in the following format:

    [METHOD] [PATH]
    
    Arguments
    
        :[ARG1]: [DESCRIPTION] (required)
        :[ARG2]: [DESCRIPTION]
    
    Response
    
        :[ARG1]: [DESCRIPTION]

Where METHOD is POST/GET/PUT...
and PATH is the path relative to the endpoint.

Resources
*********

.. toctree::
    :maxdepth: 2

    overview
    login
    domains
    jobs
    stats
    info

.. _nTLDStats: http://ntldstats.com
