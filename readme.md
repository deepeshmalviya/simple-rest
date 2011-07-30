Simple-REST - PHP REST Library (v1.0)
=====================================

Simple-REST is a lightweight PHP based REST library which can
quickly enable RESTfulness in your application. It does all the
Request/Response processing and can return response in multiple
formats like JSON, XML and QUERYSTRING.
The Simple-REST is licensed under the Apache Licence, Version 2.0
(http://www.apache.org/licenses/LICENSE-2.0.html)

Requirement
-----------

mod_rewrite support is required.

Usage
-----

Look in the [examples][examples] folder for the implementation details.

[examples]: https://github.com/deepeshmalviya/simple-rest/tree/master/examples

To test the examples, run the following curl commands in shell after uploading
folder to your localhost document root.

- GET Request (JSON Response)
curl "http://localhost/simple-rest/examples/test?a=123"

- POST Request (JSON Response)
curl -X POST -d 'b=456' "http://localhost/simple-rest/examples/test?a=123"

- PUT Request (JSON Response)
curl -X PUT -d 'b=456' "http://localhost/simple-rest/examples/test"

- DELETE Request (JSON Response)
curl -X DELETE -d '' "http://localhost/simple-rest/examples/test?a=123"

- GET Request (XML Response)
curl "http://localhost/simple-rest/examples/test?a=123&format=xml"

- POST Request (XML Response)
curl -X POST -d 'b=456' "http://localhost/simple-rest/examples/test?a=123&format=xml"

- PUT Request (XML Response)
curl -X PUT -d 'b=456' "http://localhost/simple-rest/examples/test?format=xml"

- DELETE Request (XML Response)
curl -X DELETE -d '' "http://localhost/simple-rest/examples/test?a=123$format=xml"

- GET Request (Querystring Response)
curl "http://localhost/simple-rest/examples/test?a=123&format=xml"

- POST Request (Querystring Response)
curl -X POST -d 'b=456' "http://localhost/simple-rest/examples/test?a=123&format=xml"

- PUT Request (Querystring Response)
curl -X PUT -d 'b=456' "http://localhost/simple-rest/examples/test&format=xml"

- DELETE Request (Querystring Response)
curl -X DELETE -d '' "http://localhost/simple-rest/examples/test?a=123$format=xml"


Feedback
--------

File bugs or other issues [here].

[here]: https://github.com/deepeshmalviya/simple-rest/issues



