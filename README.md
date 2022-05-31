# AL104_hash
AL104 hash API documentation
## AL104 hash php API login [ Dictionary method ]
```php
<?php 
$users = {
	'ninja':'a[n-innAa][|[in]',# ninja : 1234
	'admin':'aN|iN[akiiNNa]k]' # admin : admin
	}

$url = "https://anikin-api.herokuapp.com/AL104_hash/al104_hash_api.php";

function Login($username, $password){
	if($users[$username]){
		$data = "?string=$password&$hash=".$users[$username];
		$url = $url.$data;
		$get_req = file_get_contents($url);
		if($get_req=='true'){
			echo "Login Success!";
		}
		else{
			echo "Login Failed!";
		}
	}
}

$username = isset($_POST['username']);
$password = isset($_POST['password']);

if(!empty($username) and !empty($password)){
	$username = $_POST['username'];
	$password = $_POST['password'];
	Login();
}


?>
```
