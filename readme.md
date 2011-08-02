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

Apache mod_rewrite support.
PHP XMLWriter extension.


Notes
-----

- Following is the directory structure to be followed to use this library properly.

Support your url is http://example.com which is mapped to /var/www on your server
then to have rest uri http://example.com/rest/test, you need to upload the files
in src folder to /var/www/rest folder. The controllers should go in 
/var/www/rest/Controllers folder. Currently only one level of api is supported

- The .htaccess converts the rest uri /rest/test?123 into /rest/index.php?RESTurl=test.
This test will load Controllers/Test.php. 
- This library follows Zend convention of path mapping.
For e.g. Controllers_Test will look for Controllers/Test.php
- Controllers directory is required.
- The controller file name should be equal to rest resource uri.
For e.g. for REST uri "/rest/test", there should be Controllers/Test.php
- The controller class name should have "Controllers_" prefix.
- The controller class should extend RestController defined in Rest.php.

For e.g.
 
	class Controllers_Test extends RestController {	}

- Suppose, you only want to enable POST method for a REST api and disable
other methods (GET/PUT/DELETE). In that case the disabled methods should 
return "null".

For e.g.
	
	class Controllers_Test extends RestController {
		public function get() {
			return null;
		}

		public function post() {
			$this->response = array('TestResponse' => 'MyResponse');
			$this->responseStatus = 200;
		}

		public function put() {
			return null;
		}

		public function delete() {
			return null;
		}
	}

- The functions get, post, put, delete methods of a controller maps to
the HTTP GET, POST, PUT, DELETE respectively.
- The $this->response and $this->responseStatus variables should be 
mandatorily populated by a enabled api method. $this->response will be
the response body and $this->responseStatus will be the HTTP response
status. $this->response should be in associative array format and there should
be always one and only key in the immediate first parent. The reason for having
one key in the parent is because in xml response this key will become the
root node for the xml. The nesting level of the response array can go to 
any level.

For e.g.

$this->response = array('root' => array('xyz' => '123', 'abc' => '567'));

- For XML based responses, in case of integer keys in the response array, 
its parent key will be taken and will be suffixed with the integer index 
to form the nodename in the response.

For e.g.

$this->response = array('root' => array('xyz' => '123', 'abc' => array('567','890')));

will be converted to

<?xml version="1.0" encoding="UTF-8"?>
<root>
	<xyz>123</xyz>
	<abc>
		<abc0>567</abc0>
		<abc1>456</abc1>
	</abc>
</root>


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



