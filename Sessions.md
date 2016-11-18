**Create new sessions**

If you want to add the possibility to login with just one-click into Plesk you can create a session on Plesk.

**Example**

To use this option you can use the file 'examples/Session/create_session.php'

```<?php
require_once("../config.php");

$userIP = "127.0.0.1";
$params = array(
		"username"		=> "plesk_username",
		"user_ip"		=> $userIP,
		"source_server" => gethostbyaddr($userIP)
		
);

$request 	= new \pmill\Plesk\CreateSession($config, $params);
$info 		= $request->process();

if( $info == true )
{
	header("Location: {plesk_server}/rsession_init.php?PHPSESSID=" . $request->id);
	exit;
}
