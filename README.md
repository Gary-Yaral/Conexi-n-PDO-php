# Conexión PDO php y msql
Para realizar una conexión a base de datos por medio de PDO vas a necesitar estos tres elementos:
- Base de datos
- Archivo config.php
- Archivo Connection.php

## Código que contendrá cada archivo
**No olvides:** Debes crear los archivos con los nombres y con los códigos que te muestro a continuación.
### config.php

``` php
<?php
  define('HOST', 'localhost');
  define('USER', 'root');
  define('PASSWORD', '');
  define('DATABASE', 'tu_base_de_datos');
?>
```

### Connection.php
Asegurate de que el archivo y la clase se llamen igual, en este ejemplo se llamarán **Connection**. 
``` php
<?php
  class Connection {
    private $host;
    private $user;
    private $pass;
    private $db;

    public function _construct() {
      $this->host = HOST;
      $this->user = USER;
      $this->pass = PASSWORD;
      $this->db = DATABASE;
    }

    public function connect() {
      try {
        $connection = 'msql:host'.$this->host.';dbname:'.$this->db.';charset:utf8';
        $attributes = [PDO::ATTR_ERRMODE=> PDO::ERRMODE_EXCEPTION];
        $pdo = new PDO($connection, $this->user, $this->pass, $attributes);
        echo 'Connection successfully'; 
        return $pdo;

      } catch(PDOException $error) {
        die('Error message: '.$error->getMessage);
      }
    }
  }
?>
```
**Nota: ** Para probar si la conexión se dió exitosamente, puedes crear un archivo adicional como el que te dejo en la parte inferior.

### getConnection.php

``` php
<?php
  require_once('Connection.php');

  $connection = new Connection();
  $connection->connect();
?>
  
