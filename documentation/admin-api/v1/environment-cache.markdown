---
layout: default
title: "Puppet Server: Admin API: Environment Cache"
canonical: "/puppetserver/latest/admin-api/v1/environment-cache.html"
---

When using directory environments, the Puppet master
[caches](https://docs.puppetlabs.com/puppet/latest/reference/environments_configuring.html)
the data it loads from disk for each environment.  Puppet Server adds a new
endpoint to the master's HTTP API:


## `DELETE /puppet-admin-api/v1/environment-cache`

To trigger a complete invalidation of the data in this cache, make an HTTP
request to this endpoint.


### Response

A successful request to this endpoint will return an `HTTP 204: No Content`.
The response body will be empty.


### Example

~~~
$ curl -i -k -X DELETE https://localhost:8140/puppet-admin-api/v1/environment-cache
HTTP/1.1 204 No Content
~~~


### Relevant Configuration

This endpoint is gated behind the security provisions in the `puppet-admin`
part of the configuration data; see
[this page](https://github.com/puppetlabs/puppet-server/blob/master/documentation/configuration.markdown)
for more information.  In the example above, we have configured
`authorization-required: false` for brevity.
