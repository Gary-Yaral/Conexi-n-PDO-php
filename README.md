# Conexión PDO con PHP y MYSQL
Para realizar una conexión a base de datos por medio de PDO vas a necesitar estos tres elementos:
- Base de datos
- Archivo config.php
- Archivo Connection.php

## Crea tu base de datos MSQL
Antes de realizar la conexión debes haber creado previamente tu base de datos en algún gestor de base de datos, ya sea en **xampp**, **wampserver**, **sqlserver**, **etc**.
## Código que contendrá cada archivo
**No olvides:** Debes crear los archivos con los nombres y códigos que te muestro a continuación.
### config.php

``` php
<?php
  // No olvides cambiar los datos por los de tu conexión
  define('HOST', 'localhost');
  define('USER', 'root');
  define('PASSWORD', '');
  define('DATABASE', 'my_db');
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

    public function __construct() {
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
**Nota:**
  Para probar si la conexión se dió exitosamente, puedes crear un archivo adicional como el que te dejo en la parte inferior.

### testConnection.php

``` php
<?php
  require_once('Connection.php');

  $connection = new Connection();
  $connection->connect();
?>
  
