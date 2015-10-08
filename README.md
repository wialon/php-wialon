PHP classes for Wialon Remote API
=================================

`Wialon` - allows to perform any Wialon Remote API requests according to [documentation](http://sdk.wialon.com/wiki/en/sidebar/remoteapi/remoteapi). [cUrl](http://www.php.net/manual/en/intro.curl.php) required.

`WialonError` - simple convert Wialon error codes to text messages.

Usage
-----

```PHP
	include('wialon.php');
	$wialon_api = new Wialon();

	// old username and password login is deprecated, use token login
	$token = 'Your token here';
	$result = $wialon_api->login($token);
	$json = json_decode($result, true);
	if(!isset($json['error'])){
		echo $wialon_api->core_search_item('{"id":717359,"flags":0x1}');
		$wialon_api->logout();
	} else {
		echo WialonError::error($json['error']);
	}
```

Documentation
-----------------

[Wialon Remote Api documentation](http://sdk.wialon.com/wiki/en/sidebar/remoteapi/apiref/apiref "Remote Api")
[New authorization way](http://sdk.wialon.com/wiki/en/local/remoteapi/apiref/login/login)
