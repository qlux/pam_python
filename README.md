[![Build Status](https://travis-ci.org/privacyidea/pam_python.svg?branch=master)](https://travis-ci.org/privacyidea/pam_python)

This module is to be used with http://pam-python.sourceforge.net/.
It can be used to authenticate with OTP against privacyIDEA. It will also
cache future OTP values to enable offline authentication.

To be used like this::

```
   auth   requisite    pam_python.so /path/to/modules/privacyidea-pam.py
```

It can take the following parameters:

**url=https://your-server**

   Default is https://localhost

**debug**

   Write debug information to the system log

**realm=yourRealm**

   Pass additional realm to privacyidea

**nosslverify**

   Do not verify the SSL certificate

**prompt=<Prompt>**

   The password prompt. Default is "Your OTP".

**api_token=<token>**

   The API Token to access admin REST API for auto-enrolment. Requires the following Actions:
   ``{ "enrollEMAIL": true, "enrollpin": true, "tokenlist": true }``

**grace=<time>**

   Grace time in minutes.

**user_attribute=<uid,gid,gecos>**

   Override the username to send to privacyIDEA with an attribute from the
   user's password entry

**users=<list,of,users>**

   Comma-separated list of users to apply the plugin to.
   If not specified, apply to all users.

**sqlfile=<file>**

   This is the SQLite file that is used to store the offline authentication
   information.
   The default file is /etc/privacyidea/pam.sqlite

**mysql=<uri>**

   Use MySQL/MariaDB instead of SQLite to store refill/history tables.
   URI form: mysql://username:password@host:3306/db_name
   If absent, fallback to sqlfile
