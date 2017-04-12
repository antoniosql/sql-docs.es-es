---
title: "tablediff (utilidad) | Microsoft Docs"
ms.custom: ""
ms.date: "03/14/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "database-engine"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "comparar datos"
  - "tablediff, utilidad"
  - "tablas [replicación de SQL Server]"
  - "comparaciones de tablas [SQL Server]"
  - "utilidades del símbolo del sistema [SQL Server], tablediff"
  - "solucionar problemas [replicación de SQL Server], no convergencia"
  - "no convergencia [SQL Server]"
ms.assetid: 3c3cb865-7a4d-4d66-98f2-5935e28929fc
caps.latest.revision: 30
author: "BYHAM"
ms.author: "rickbyh"
manager: "jhubbard"
caps.handback.revision: 30
---
# tablediff (utilidad)
  La utilidad **tablediff** se usa para comparar los datos de dos tablas para determinar la no convergencia y es especialmente útil para solucionar problemas de no convergencia en una topología de replicación. Esta utilidad se puede usar desde el símbolo del sistema o en un archivo por lotes para realizar las siguientes tareas:  
  
-   Una comparación fila a fila entre una tabla de origen de una instancia de [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] que actúa como publicador de replicación y la tabla de destino de una o más instancias de [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] que actúan como suscriptores de replicación.  
  
-   Realiza una comparación rápida comparando solo el número de filas y el esquema.  
  
-   Realizar comparaciones de nivel de columna.  
  
-   Generar un script [!INCLUDE[tsql](../includes/tsql-md.md)] para solucionar discrepancias en el servidor de destino y hacer que las tablas de destino y de origen converjan.  
  
-   Registrar resultados en un archivo de salida o en una tabla de la base de datos de destino.  
  
## Sintaxis  
  
```  
  
tablediff   
[ -? ] |   
{  
        -sourceserver source_server_name[\instance_name]  
        -sourcedatabase source_database  
        -sourcetable source_table_name   
    [ -sourceschema source_schema_name ]  
    [ -sourcepassword source_password ]  
    [ -sourceuser source_login ]  
    [ -sourcelocked ]  
        -destinationserver destination_server_name[\instance_name]  
        -destinationdatabase subscription_database   
        -destinationtable destination_table   
    [ -destinationschema destination_schema_name ]  
    [ -destinationpassword destination_password ]  
    [ -destinationuser destination_login ]  
    [ -destinationlocked ]  
    [ -b large_object_bytes ]   
    [ -bf number_of_statements ]   
    [ -c ]   
    [ -dt ]   
    [ -et table_name ]   
    [ -f [ file_name ] ]   
    [ -o output_file_name ]   
    [ -q ]   
    [ -rc number_of_retries ]   
    [ -ri retry_interval ]   
    [ -strict ]  
    [ -t connection_timeouts ]   
}  
```  
  
## Argumentos  
 [ **-?** ]  
 Devuelve la lista de parámetros admitidos.  
  
 **-sourceserver** *source_server_name*[**\\***instance_name*]  
 Es el nombre del servidor de origen. Especifique *source_server_name* para la instancia predeterminada de [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]. Especifique *source_server_name***\\***instance_name* para una instancia con nombre de [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)].  
  
 **-sourcedatabase** *source_database*  
 Es el nombre de la base de datos de origen.  
  
 **-sourcetable** *source_table_name*  
 Es el nombre de la tabla de origen que se está comprobando.  
  
 **-sourceschema** *source_schema_name*  
 Es el propietario del esquema de la tabla de origen. De forma predeterminada, se asume que el propietario de la tabla es dbo.  
  
 **-sourcepassword** *source_password*  
 Es la contraseña para el inicio de sesión que se usa para conectar con el servidor de origen mediante autenticación de [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)].  
  
> [!IMPORTANT]  
>  Cuando sea posible, proporcione credenciales de seguridad en tiempo de ejecución. Si debe almacenar credenciales en un archivo de script, debe proteger el archivo para impedir el acceso no autorizado.  
  
 **-sourceuser** *source_login*  
 Es el inicio de sesión que se usa para conectar con el servidor de origen mediante autenticación de [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]. Si no se proporciona *source_login*, se usa autenticación de Windows para conectar con el servidor de origen. [!INCLUDE[ssNoteWinAuthentication](../includes/ssnotewinauthentication-md.md)]  
  
 **-sourcelocked**  
 La tabla de origen se bloquea durante la comparación con las sugerencias de tabla TABLOCK y HOLDLOCK.  
  
 **-destinationserver** *destination_server_name*[**\\***instance_name*]  
 Es el nombre del servidor de destino. Especifique *destination_server_name* para la instancia predeterminada de [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]. Especifique *destination_server_name***\\***instance_name* para una instancia con nombre de [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)].  
  
 **-destinationdatabase** *subscription_database*  
 Es el nombre de la base de datos de destino.  
  
 **-destinationtable** *destination_table*  
 Es el nombre de la tabla de destino.  
  
 **-destinationschema** *destination_schema_name*  
 Es el propietario del esquema de la tabla de destino. De forma predeterminada, se asume que el propietario de la tabla es dbo.  
  
 **-destinationpassword** *destination_password*  
 Es la contraseña para el inicio de sesión que se usa para conectar con el servidor de destino mediante autenticación de [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)].  
  
> [!IMPORTANT]  
>  Cuando sea posible, proporcione credenciales de seguridad en tiempo de ejecución. Si debe almacenar credenciales en un archivo de script, debe proteger el archivo para impedir el acceso no autorizado.  
  
 **-destinationuser** *destination_login*  
 Es el inicio de sesión que se usa para conectar con el servidor de destino mediante autenticación de [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]. Si no se proporciona *destination_login*, se usa autenticación de Windows para conectar con el servidor. [!INCLUDE[ssNoteWinAuthentication](../includes/ssnotewinauthentication-md.md)]  
  
 **-destinationlocked**  
 La tabla de destino se bloquea durante la comparación con las sugerencias de tabla TABLOCK y HOLDLOCK.  
  
 **-b** *large_object_bytes*  
 Es el número de bytes que se va a comparar en las columnas de tipo de datos de objetos grandes, lo que incluye: **text**, **ntext**, **image**, **varchar(max)**, **nvarchar(max)** y **varbinary(max)**. *large_object_bytes* toma como valor predeterminado el tamaño de la columna. Los datos que superen *large_object_bytes* no se compararán.  
  
 **-bf** *number_of_statements*  
 Es el número de instrucciones [!INCLUDE[tsql](../includes/tsql-md.md)] que se va a escribir en el archivo de script actual [!INCLUDE[tsql](../includes/tsql-md.md)] cuando se usa la opción**-f**. Cuando el número de instrucciones [!INCLUDE[tsql](../includes/tsql-md.md)] supera el valor de *number_of_statements*, se crea un nuevo archivo de script [!INCLUDE[tsql](../includes/tsql-md.md)].  
  
 **-c**  
 Compara diferencias de nivel de columna.  
  
 **-dt**  
 Quita la tabla de resultados especificada por *table_name* si la tabla ya existe.  
  
 **-et** *table_name*  
 Especifica el nombre de la tabla de resultados que se desea crear. Si ya existe esta tabla, debe usarse **-DT** o la operación no se realizará correctamente.  
  
 **-f** [ *file_name* ]  
 Genera un script de [!INCLUDE[tsql](../includes/tsql-md.md)] para hacer que la tabla del servidor de destino converja con la tabla del servidor de origen. Tiene la opción de especificar un nombre y una ruta de acceso para el archivo de script [!INCLUDE[tsql](../includes/tsql-md.md)] generado. Si no se especifica *file_name*, el archivo de script [!INCLUDE[tsql](../includes/tsql-md.md)] se genera en el directorio en el que se ejecuta la utilidad.  
  
 **-o** *output_file_name*  
 Es la ruta y el nombre completo del archivo de salida.  
  
 **-q**  
 Realiza una comparación rápida comparando solo el número de filas y el esquema.  
  
 **-rc** *number_of_retries*  
 Número de reintentos de la utilidad para operaciones con errores.  
  
 **-ri** *retry_interval*  
 Intervalo (en segundos) entre los reintentos.  
  
 **-strict**  
 El esquema de origen y de destino se comparan de forma estricta.  
  
 **-t** *connection_timeouts*  
 Establece el período de tiempo de espera de la conexión, en segundos, para las conexiones con el servidor de origen y el servidor de destino.  
  
## Valor devuelto  
  
|Valor|Descripción|  
|-----------|-----------------|  
|**0**|Success|  
|**1**|Error grave|  
|**2**|Diferencias entre tablas|  
  
## Comentarios  
 La utilidad **tablediff** no se puede usar con servidores que no son [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)].  
  
 No se admiten tablas que contengan columnas con el tipo de datos **sql_variant**.  
  
 De forma predeterminada, la utilidad **tablediff** admite las siguientes asignaciones de tipos de datos entre las columnas de origen y de destino.  
  
|Tipo de datos de origen|Tipo de datos de destino|  
|----------------------|---------------------------|  
|**tinyint**|**smallint**, **int** o **bigint**|  
|**smallint**|**int** o **bigint**|  
|**int**|**bigint**|  
|**timestamp**|**varbinary**|  
|**varchar(max)**|**texto**|  
|**nvarchar(max)**|**ntext**|  
|**varbinary(max)**|**imagen**|  
|**texto**|**varchar(max)**|  
|**ntext**|**nvarchar(max)**|  
|**imagen**|**varbinary(max)**|  
  
 Use la opción **-strict** para no permitir estas asignaciones y llevar a cabo una validación estricta.  
  
 La tabla de origen de la comparación debe contener como mínimo una columna de clave principal, de identidad o ROWGUID. Cuando se emplea la opción **-strict**, la tabla de destino también debe tener una columna de clave principal, de identidad o ROWGUID.  
  
 El script [!INCLUDE[tsql](../includes/tsql-md.md)] generado para hacer que la tabla de destino converja no incluye los siguientes tipos de datos:  
  
-   **varchar(max)**  
  
-   **nvarchar(max)**  
  
-   **varbinary(max)**  
  
-   **timestamp**  
  
-   **xml**  
  
-   **texto**  
  
-   **ntext**  
  
-   **imagen**  
  
## Permisos  
 Para comparar tablas, necesita los permisos SELECT ALL en los objetos de la tabla que se están comparando.  
  
 Para usar la opción **-et**, debe ser miembro del rol fijo de base de datos db_owner o, como mínimo, tener el permiso CREATE TABLE en la base de datos de suscripciones y el permiso ALTER en el esquema del propietario de destino del servidor de destino.  
  
 Para usar la opción **-dt**, debe ser miembro del rol fijo de base de datos db_owner o, como mínimo, tener el permiso ALTER en el esquema del propietario de destino del servidor de destino.  
  
 Para usar las opciones **-o** o **-f**, debe tener permisos de escritura en la ubicación del directorio de archivos especificada.  
  
## Vea también  
 [Comparar tablas replicadas para buscar diferencias &#40;programación de la replicación&#41;](../relational-databases/replication/administration/compare-replicated-tables-for-differences-replication-programming.md)  
  
  