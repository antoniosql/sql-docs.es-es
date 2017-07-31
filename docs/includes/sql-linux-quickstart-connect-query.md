## <a name="connect-locally"></a>Conexión local

En los pasos siguientes se usa **sqlcmd** para conectarse localmente a la nueva instancia de SQL Server.

1. Ejecute **sqlcmd** con parámetros para el nombre de SQL Server (-S), el nombre de usuario (-U) y la contraseña (-P). En este tutorial se conecta de forma local, por lo que el nombre del servidor es `localhost`. El nombre de usuario es `SA` y la contraseña es la que proporcionó para la cuenta SA durante la configuración.

   ```bash
   sqlcmd -S localhost -U SA -P '<YourPassword>'
   ```

   > [!TIP]
   > Puede omitir la contraseña en la línea de comandos para que se le solicite escribirla.

   > [!TIP]
   > Si más adelante decide conectarse de forma remota, especifique el nombre de la máquina o la dirección IP del parámetro **-S** y asegúrese de que el puerto 1433 esté abierto en el firewall.

1. Si se realiza correctamente, debe ver un símbolo de sistema de **sqlcmd**: `1>`.

1. Si recibe un error de conexión, intente primero diagnosticar el problema a partir del mensaje de error. Luego revise las [recomendaciones para solucionar problemas de conexión](../linux/sql-server-linux-troubleshooting-guide.md#connection).

## <a name="create-and-query-data"></a>Creación y consulta de datos
Las secciones siguientes le guían en el uso de **sqlcmd** y Transact-SQL para crear una base de datos, agregar datos y ejecutar una consulta simple.

### <a name="create-a-new-database"></a>Creación de una base de datos

En los pasos siguientes se crea una base de datos denominada `TestDB`.

1. En el símbolo del sistema de **sqlcmd**, pegue el comando Transact-SQL siguiente para crear una base de datos de prueba:

   ```sql
   CREATE DATABASE TestDB
   ```

1. En la línea siguiente, escriba una consulta para devolver el nombre de todas las bases de datos del servidor:

   ```sql
   SELECT Name from sys.Databases
   ```

1. Los dos comandos anteriores no se ejecutaron de inmediato. Debe escribir `GO` en una línea nueva para ejecutar los comandos anteriores:

   ```sql
   GO
   ```

### <a name="insert-data"></a>Inserción de datos

Luego cree una tabla, `Inventory`, e inserte dos filas nuevas.

1. En el símbolo del sistema de **sqlcmd**, cambie el contexto a la nueva base de datos `TestDB`:

   ```sql
   USE TestDB
   ```

1. Cree una tabla llamada `Inventory`:

   ```sql
   CREATE TABLE Inventory (id INT, name NVARCHAR(50), quantity INT)
   ```

1. Inserte datos en la nueva tabla:

   ```sql
   INSERT INTO Inventory VALUES (1, 'banana', 150); INSERT INTO Inventory VALUES (2, 'orange', 154);
   ```

1. Escriba `GO` para ejecutar los comandos anteriores:

   ```sql
   GO
   ```

### <a name="select-data"></a>Selección de datos

Ahora ejecute una consulta para devolver datos desde la tabla `Inventory`.

1. En el símbolo del sistema **sqlcmd**, escriba una consulta que devuelva filas desde la tabla `Inventory` donde la cantidad sea mayor que 152:

   ```sql
   SELECT * FROM Inventory WHERE quantity > 152;
   ```

1. Ejecute el comando:

   ```sql
   GO
   ```

### <a name="exit-the-sqlcmd-command-prompt"></a>Salida del símbolo del sistema de sqlcmd

Para finalizar la sesión de **sqlcmd**, escriba `QUIT`:

```sql
QUIT
```

## <a name="connect-from-windows"></a>Conexión desde Windows

Es importante tener en cuenta que las herramientas de SQL Server en Windows se conecten a instancias de SQL Server en Linux del mismo modo en que se conectarían a cualquier instancia remota de SQL Server.

Si tiene una máquina Windows que se puede conectar a la máquina Linux, pruebe con los mismos pasos de este tema desde un símbolo del sistema Windows mediante la ejecución de **sqlcmd**. Simplemente compruebe que usa el nombre o la dirección IP de la máquina Linux de destino en lugar del host local y asegúrese de que el puerto TCP 1433 esté abierto. Si tiene problemas para conectarse desde Windows, consulte las [recomendaciones para solucionar problemas de conexión](../linux/sql-server-linux-troubleshooting-guide.md#connection).

Para las otras herramientas que se ejecutan en Windows pero se conectan a SQL Server en Linux, consulte:

- [SQL Server Management Studio (SSMS)](../linux/sql-server-linux-develop-use-ssms.md)
- [Windows PowerShell](../linux/sql-server-linux-manage-powershell.md)
- [SQL Server Data Tools (SSDT)](../linux/sql-server-linux-develop-use-ssdt.md)

## <a name="next-steps"></a>Pasos siguientes

Si no conoce T-SQL, consulte [Tutorial: Escribir instrucciones Transact-SQL](../t-sql/tutorial-writing-transact-sql-statements.md) y [Referencia de Transact-SQL (motor de base de datos)](../t-sql/language-reference.md).

Para explorar otras formas de conectar y administrar SQL Server, consulte [Visual Studio Code](../linux/sql-server-linux-develop-use-vscode.md) y [SQL Server Management Studio](../linux/sql-server-linux-develop-use-ssms.md).