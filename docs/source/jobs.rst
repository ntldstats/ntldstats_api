Jobs
####

List pending jobs
*****************

Return list of all pending jobs for your user

Command
=======

**GET /jobs**

Arguments
    -- None

Response
    :jobs: List of all jobs

Job Item
    :status: Status of job. Could be either **Unprocessed**, **Processing**, **Error** or **Finished**
    :job_id: ID of job
    :added: DateTime when item got added

Example
=======

Request
::

    GET /jobs    

Response
::

    {
        "code": 1000,
        "msg":"Command completed successfully",
        "resData": {
            "jobs": [ 
                {
                    "status": "Unprocessed",
                    "job_id": "a15e98ca-17f5-56cc-b654-4661013749e6",
                    "added": "2014-04-17T00:40:00Z"
                }
            ]
        }
    }

Get job details
***************

Command
=======

**GET /jobs/<jobid>**

Arguments

    -- None

Response

    :status: Status of job. Could be either **Unprocessed**, **Processing**, **Error** or **Finished**
    :job_id: ID of job
    :added: DateTime when item got added

Example
=======

Request
::

    GET /jobs/a15e98ca-17f5-56cc-b654-4661013749e6

Response
::

    {
        "code": 1000,
        "msg":"Command completed successfully",
        "resData": {
            "status": "Unprocessed",
            "job_id": "a15e98ca-17f5-56cc-b654-4661013749e6",
            "added": "2014-04-17T00:40:00Z"
        }
    }
