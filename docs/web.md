# cAdvisor Web UI

cAdvisor exposes a web UI at its port:

`http://<hostname>:<port>/`

This UI has one primary resource at `/containers` which exports live information about all containers on the machine.

## Web UI authentication

You can add authentication to the web UI by either HTTP basic or HTTP digest authentication. 

NOTE: The Web UI authentication only protects the `/containers` endpoint, and not the other cAdvisor HTTP endpoints such as `/api/...` and `/metrics`. Some of these endpoints can expose sensitive information, so it is not advised to expose these endpoints publicly.

### HTTP basic authentication

You will need to add a *http_auth_file* parameter with a HTTP basic auth file generated using htpasswd to enable HTTP basic auth. By default the auth realm is set as localhost.

`./cadvisor --http_auth_file test.htpasswd --http_auth_realm localhost`

The [test.htpasswd](https://github.com/QubitPi/cadvisor/blob/master/test.htpasswd) file provided has a username and password already added (`admin:password1`) for testing purposes.

### HTTP Digest authentication

You will need to add a *http_digest_file* parameter with a HTTP digest auth file generated using htdigest to enable HTTP Digest auth. By default the auth realm is set as localhost.

`./cadvisor --http_digest_file test.htdigest --http_digest_realm localhost`

The [test.htdigest](https://github.com/QubitPi/cadvisor/blob/master/test.htdigest) file provided has a username and password already added (`admin:password1`) for testing purposes.

**Note** : You can use either type of authentication, in case you decide to use both files in the arguments only HTTP basic auth will be enabled. 
