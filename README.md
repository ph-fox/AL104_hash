# AL104_hash
AL104 hash API documentation
## AL104 hash PHP API login [ Dictionary as creds method ]
```php
<?php 

$users = array(
	'ninja'=>'a[n-innAa][|[in]',# ninja : 1234
	'admin'=>'aN|iN[akiiNNa]k]' # admin : admin
	);

$url = "https://anikin-api.herokuapp.com/AL104_hash/al104_hash_api.php"; # <-- API url

function Login($url, $users, $username, $password){
	foreach($users as $user){
		$data = "?string=$password&hash=".$user;
		$url = $url.$data;
		$get_req = file_get_contents($url);
		if($get_req=='true'){
			return true;
		}
	}
}


if(isset($_GET['user']) and isset($_GET['pass'])){
	$username = $_GET['user'];
	$password = $_GET['pass'];
	$status = Login($url, $users, $username, $password);
	if($status){
		echo "Login Success!";
	}else{
		echo "Login Failed!";
	}
}

?>
```
## AL104 hash PHP API [Variable as creds Method]
```php
<?php 

$usr_username = 'ninja';
$usr_password = 'a[n-innAa][|[in]'; # <-- AL104 hash which holds '1234' as its value.
$url = "https://anikin-api.herokuapp.com/AL104_hash/al104_hash_api.php"; # <-- API url

function Login($url, $hash_password, $password){
	$data = "?string=$password&hash=$hash_password";
	$url = $url.$data;
	$get_req = file_get_contents($url);
	if($get_req=='true'){
		return true;
	}
}


if(isset($_GET['user']) and isset($_GET['pass'])){
	$input_usr = $_GET['user'];
	$input_pss = $_GET['pass'];
	$status = Login($url,$usr_password, $input_pss);
	if($status and $usr_username==$input_usr){
		echo "Login Success!";
	}
	else{
		echo "Login Failed!";
	}
}

?>
```
