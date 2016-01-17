# SO
sistem operasi
<?php
function ipnya(){
$ipaddress="";
if(getenv('HTTP_CLIENT_IP'))
$ipaddress=
getenv('HTTP_CLIENT_IP');
else
if(getenv('HTTP_X_FORWARDED_FOR'))
$ipaddress=
getenv('HTTP_X_FORWARDED_FOR');
else
if(getenv('HTTP_X_FORWARDED'))
$ipaddress=
getenv('HTTP_X_FORWARDED');
else
if(getenv('HTTP_FORWARDED_FOR'))
$ipaddress=
getenv('HTTP_FORWARDED_FOR');
else if(getenv('HTTP_FORWARDED'))
$ipaddress=
getenv('HTTP_FORWARDED');
else if(getenv('REMOTE_ADDR'))
$ipaddress=
getenv('REMOTE_ADDR');
else
$ipaddress='IP tidak dikenali';
return $ipaddress;
}
$user_agent=
$_SERVER['HTTP_USER_AGENT'];
function getOS(){
global $user_agent;
$os_platform="Unknown OS Platform";
$os_array=array( '/windows nt 10/i' => 'Windows 10', '/windows nt 6.3/i'
=> 'Windows 8.1', '/windows nt 6.2/i' => 'Windows 8', 'windows nt 6.1/i'
=> 'Windows 7', '/linux/i' => 'Linux', '/ubuntu/i'=>'Ubuntu',);
foreach($os_array as $regex => $value){
if(preg_match($regex, 
$user_agent)){
$os_platform = $value;
}
}
return $os_platform;
}
function getBrowser(){
global $user_agent;
$browser = "Unknown Browser";
$browser_array=array('/firefox/i' => 'Firefox', '/safari/i' => 'Safari',
'/chrome/i'=>'Chrome', '/opera/i' =>'Opera',);
foreach($browser_array as $regex => $value){
if(preg_match($regex, $user_agent)){
$browser=$value;
}
}
return $browser;
}
$user_os = getOS();
$user_browser = getBrowser();
$user_ip=ipnya();
if($user_ip==""){
echo $user_ip;
}else{
$country="Indonesia";
echo $country;
}
?>
<html>
<head>
<title>sistem operasi dari client</title>
<style type="text/css">
html{
font-family:"times new roman";
}
table{
border-collapse:collapse;
margin-right: auto;
margin-left: auto;
}
table, th, td{
padding: 10px;
}
th{
background-color:red;
}
tr:nth-child(even){
background-color:blue;
}
tr:ntd-child(even){
background-color:red;
}
h1{
margin-bottom:5;
}
</style>
<link rel="shortcut icon"
href="/favicon.png">
</head>
<body>
<table>
<tr align="center">
<th colspan="3">
<h1>MENAMPILKAN SISTEM OPERASI DARI CLIENT</h1></th>
</tr>
<tr>
<td><b>NIM<b></td>
<td>:</td>
<td>EGI MAULANA A.</td>
</tr>
<tr>
<td><b>Kelas</b></td>
<td>:</td>
<td>Teknik Informatika A 2014</td>
</tr>
<tr>
<td><b>Sistem Operasi</b></td>
<td>:</td>
<td><?php echo $user_os;?>
</td>
</tr>
<tr>
<td><b>BROWSER</b></td>
<td>:</td>
<td><?php echo $user_browser;?></td>
</tr>
<tr>
<td><b>IP</b></td>
<td>:</td>
<td><?php echo $user_ip;?>
</td>
</tr>
<tr>
<td><b>NEGARA</b></td>
<td>:</td>
<td><?php echo $country;?>
</td>
</tr>
<tr>
<td><b>LENGKAPNYA</b></td>
<td>:</td>
<td><?php echo $_SERVER['HTTP_USER_AGENT'];?>
</td>
</tr>
</table>
</body>
</html>
