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
	$servername = "datamoviles.tk";
	$username = "admin_alumnos";
	$password = "2022";
	$dbname = "admin_default";

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
