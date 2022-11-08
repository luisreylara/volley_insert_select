# volley_insert_select

## consultar.php

```
<?php
header('Content-Type: application/json');
//$datos = json_decode(file_get_contents("php://input"),true);

require("conexion.php");

$conn = retornarConexion();

$sql = "SELECT codigo,descripcion,precio FROM articulos where codigo = $_GET[codigo]";
$result = $conn->query($sql);
$miresult=mysqli_fetch_all($result,MYSQLI_ASSOC);
echo json_encode($miresult);

$conn->close();

?>
```

## conexion.php
```

<?php

function retornarConexion(){
	$servername = ".tk";
	$username = "";
	$password = "";
	$dbname = "¡";

	// Create connection
	$conn = new mysqli($servername, $username, $password, $dbname);
	// Check connection
	if ($conn->connect_error) {
	  die("Connection failed: " . $conn->connect_error);
	}
	return $conn;
}

?>
```

## borrar.php
```
<?php
header('Content-Type: application/json');
$datos = json_decode(file_get_contents("php://input"),true);

require("conexion.php");

$conn = retornarConexion();


$sql = "Delete FROM articulos where codigo = $datos[codigo]";
//echo $sql;

if ($conn->query($sql) ) {
  echo '{"resultado":"1"}';
} else {
  echo '{"resultado":"0"}';
}

$conn->close();
?>
```
## borrar2.php
```
<?php
header('Content-Type: application/json');
$datos = json_decode(file_get_contents("php://input"),true);

require("conexion.php");

$conn = retornarConexion();


$sql = "Delete FROM articulos where codigo = $datos[codigo]";
//echo $sql;

mysqli_query($conn,$sql);

$cant=mysqli_affected_rows($conn);

if ($cant==1) {
  echo '{"resultado":"1"}';
} else {
  echo '{"resultado":"0"}';
}


$conn->close();

?>
```
