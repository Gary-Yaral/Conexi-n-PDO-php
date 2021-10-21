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

    function _construct() {
      $this->host = HOST;
      $this->user = USER;
      $this->pass = PASSWORD;
      $this->db = DATABASE;
    }
  }
?>
```
