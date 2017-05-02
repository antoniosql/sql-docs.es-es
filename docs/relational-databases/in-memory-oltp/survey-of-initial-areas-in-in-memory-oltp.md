---
title: "Inicio rápido 1: Tecnologías de OLTP en memoria para acelerar el rendimiento de Transact-SQL | Microsoft Docs"
ms.custom: 
ms.date: 12/02/2016
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine-imoltp
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 1c25a164-547d-43c4-8484-6b5ee3cbaf3a
caps.latest.revision: 31
author: MightyPen
ms.author: genemi
manager: jhubbard
translationtype: Human Translation
ms.sourcegitcommit: 2edcce51c6822a89151c3c3c76fbaacb5edd54f4
ms.openlocfilehash: 82286b0d52ff37697ad9197b88c45935137a8dae
ms.lasthandoff: 04/11/2017

---
# <a name="survey-of-initial-areas-in-in-memory-oltp"></a>Encuesta de áreas iniciales de OLTP en memoria
[!INCLUDE[tsql-appliesto-ss2014-asdb-xxxx-xxx_md](../../includes/tsql-appliesto-ss2014-asdb-xxxx-xxx-md.md)]

  
Este artículo está destinado a los desarrolladores que necesitan aprender rápidamente los conceptos básicos de las características de rendimiento de OLTP en memoria de Microsoft SQL Server y Base de datos SQL de Azure.  
  
Para OLTP en memoria, este artículo incluye lo siguiente:  
  
- Breves explicaciones de las características.  
- Ejemplos de código principal que implementan las características.  
  
  
SQL Server y Base de datos SQL presentan solo pequeñas variaciones en su compatibilidad con tecnologías en memoria.  
  
  
En su ámbito, algunos blogueros hacen referencia a las características de OLTP en memoria como *Hekaton*.  
  
  
<a name="benefits-of-in-memory-features-21a"></a>  
  
## <a name="benefits-of-in-memory-features"></a>Ventajas de las características en memoria  
  
SQL Server proporciona características en memoria que pueden mejorar considerablemente el rendimiento de muchos sistemas de aplicaciones. En esta sección se describen las consideraciones más sencillas.  
  
  
### <a name="features-for-oltp-online-transactional-processing"></a>Características de OLTP (procesamiento de transacciones en línea)  
  
  
Los sistemas que deben procesar simultáneamente grandes cantidades de instrucciones INSERT de SQL son los candidatos perfectos para las características de OLTP.  
  
- Nuestras pruebas comparativas muestran que la velocidad se puede multiplicar entre 5 y 20 veces con la adopción de las características en memoria.  
  
  
Los sistemas que procesan cálculos intensivos en Transact-SQL son candidatos ideales.  
  
- Un procedimiento almacenado que se dedica a cálculos intensivos se puede ejecutar hasta 99 veces más rápido.  
  
  
Más tarde tal vez le interese visitar los siguientes artículos, que ofrecen demostraciones de las mejoras de rendimiento de OLTP en memoria:  
  
- [Demostración: mejora de rendimiento de OLTP en memoria](../../relational-databases/in-memory-oltp/demonstration-performance-improvement-of-in-memory-oltp.md) ofrece una demostración a pequeña escala de las posibles mejoras de rendimiento más grandes.  
- [Sample Database for In-Memory OLTP (Base de datos de ejemplo para OLTP en memoria)](../../relational-databases/in-memory-oltp/sample-database-for-in-memory-oltp.md) ofrece una demostración de escala mayor.  
  
  
  
### <a name="features-for-operational-analytics"></a>Características de análisis operativo  
  
El análisis en memoria hace referencia a instrucciones SELECT de SQL que agregan datos transaccionales, normalmente mediante la inclusión de una cláusula GROUP BY. El tipo de índice denominado *columnstore* es fundamental para el análisis operativo.  
  
Hay dos escenarios principales:  
  
- El*análisis operativo por lotes* hace referencia a los procesos de agregación que se ejecutan cuando finaliza el horario laboral o bien en hardware secundario que tiene copias de los datos transaccionales.  
  - El[Almacenamiento de datos SQL de Azure](https://azure.microsoft.com/documentation/articles/sql-data-warehouse-overview-what-is/) también está relacionado con el análisis operativo por lotes.  
- El*análisis operativo en tiempo real* hace referencia a los procesos de agregación que se ejecutan en horario laboral y en el hardware principal que se usa para cargas de trabajo transaccionales.  
  
  
El presente artículo se centra en OLTP y no en el análisis. Para obtener información sobre cómo los índices de almacén de columnas llevan el análisis a SQL, vea:  
  
- [Introducción al almacén de columnas para análisis operativos en tiempo real](../../relational-databases/indexes/get-started-with-columnstore-for-real-time-operational-analytics.md)  
- [Guía de índices de almacén de columnas](../../relational-databases/indexes/columnstore-indexes-overview.md)  
  
  
> [!NOTE]
> Hay disponible un vídeo de dos minutos sobre las características en memoria en [Azure SQL Database - In-Memory Technologies (Base de datos SQL de Azure: tecnologías en memoria)](http://channel9.msdn.com/Blogs/Windows-Azure/Azure-SQL-Database-In-Memory-Technologies). El vídeo tiene fecha de diciembre de 2015.  


### <a name="columnstore"></a>columnstore

Una secuencia de entradas de blog excelentes explica de manera elegante los índices de almacén de columnas desde varias perspectivas. En la mayoría de las publicaciones se describe más el concepto de análisis operacional en tiempo real, que es compatible con el almacén de columnas.  Sunil Agarwal, director de programas en Microsoft, creó estas entradas en marzo de 2016.

#### <a name="real-time-operational-analytics"></a>análisis operativo en tiempo real

1. [Análisis operativos en tiempo real mediante la tecnología In-Memory](https://blogs.technet.microsoft.com/dataplatforminsider/2015/12/09/real-time-operational-analytics-using-in-memory-technology/)
2. [Análisis operativos en tiempo real: información general del índice de almacén de columnas no agrupado (NCCI)](https://blogs.msdn.microsoft.com/sqlserverstorageengine/2016/02/29/real-time-operational-analytics-using-nonclustered-columnstore-index/)
3. [Análisis operativos en tiempo real: ejemplo sencillo usando un índice de almacén de columnas no agrupado (NCCI) en SQL Server 2016](https://blogs.msdn.microsoft.com/sqlserverstorageengine/2016/02/29/real-time-operational-analytics-simple-example-using-nonclustered-clustered-columnstore-index-ncci/)
4. [Análisis operativos en tiempo real: las operaciones DML y el índice de almacén de columnas no agrupado (NCCI) en SQL Server 2016](https://blogs.msdn.microsoft.com/sqlserverstorageengine/2016/03/04/real-time-operational-analytics-dml-operations-and-nonclustered-columnstore-index-ncci-in-sql-server-2016/)
5. [Análisis operativos en tiempo real: índice de almacén de columnas no agrupado filtrado (NCCI)](https://blogs.msdn.microsoft.com/sqlserverstorageengine/2016/03/06/real-time-operational-analytics-filtered-nonclustered-columnstore-index-ncci/)
6. [Análisis operativos en tiempo real: opción de retraso de compresión del índice de almacén de columnas no agrupado (NCCI)](https://blogs.msdn.microsoft.com/sqlserverstorageengine/2016/03/06/real-time-operational-analytics-compression-delay-option-for-nonclustered-columnstore-index-ncci/)
7. [Análisis operativos en tiempo real: opción de retraso de compresión con NCCI y el rendimiento](https://blogs.msdn.microsoft.com/sqlserverstorageengine/2016/03/06/real-time-operational-analytics-compression-delay-option-with-ncci-and-the-performance/)
8. [Análisis operativos en tiempo real: tablas con optimización para memoria e índice de almacén de columnas](https://blogs.msdn.microsoft.com/sqlserverstorageengine/2016/03/07/real-time-operational-analytics-memory-optimized-table-and-columnstore-index/)

#### <a name="defragment-a-columnstore-index"></a>Desfragmentar un índice de almacén de columnas.

1. [Desfragmentación del índice de almacén de columnas mediante el comando REORGANIZE](https://blogs.msdn.microsoft.com/sqlserverstorageengine/2016/03/07/columnstore-index-defragmentation-using-reorganize-command/)
2. [Directiva de combinación del índice de almacén de columnas para REORGANIZE](https://blogs.msdn.microsoft.com/sqlserverstorageengine/2016/03/08/columnstore-index-merge-policy-for-reorganize/)

#### <a name="bulk-importation-of-data"></a>Importación masiva de datos

1. [Almacén de columnas agrupadas: carga masiva](https://blogs.msdn.microsoft.com/sqlserverstorageengine/2014/07/27/clustered-column-store-index-bulk-loading-the-data/)
2. [Índice de almacén de columnas agrupado: optimizaciones de carga de datos: registro mínimo](https://blogs.msdn.microsoft.com/sqlserverstorageengine/2016/01/10/clustered-columnstore-index-data-load-optimizations-minimal-logging/)
3. [Índice de almacén de columnas agrupado: optimizaciones de carga de datos: importación masiva en paralelo](https://blogs.msdn.microsoft.com/sqlserverstorageengine/2016/02/28/clustered-columnstore-index-parallel-bulk-import/)





<a name="features-on-in-memory-oltp-13b"></a>  
  
## <a name="features-of-in-memory-oltp"></a>Característica de OLTP en memoria  
  
Veamos las características principales de OLTP en memoria.  
  
  
#### <a name="memory-optimized-tables"></a>Tablas con optimización para memoria  
  
La palabra clave MEMORY_OPTIMIZED de T-SQL, en la instrucción CREATE TABLE, indica que se crea una tabla en la memoria activa, en lugar de en disco.  
  
  
Las [tablas con optimización para memoria](../../relational-databases/in-memory-oltp/memory-optimized-tables.md) tienen una representación de sí mismas en la memoria activa y una copia secundaria en el disco.  
  
- La copia del disco es para recuperación rutinaria después de un cierre y reinicio del servidor o de la base de datos. Esta dualidad de disco más memoria está oculta automáticamente y no se ve en el código.  
  
  
#### <a name="natively-compiled-modules"></a>Módulos compilados de forma nativa  
  
La palabra clave NATIVE_COMPILATION de T-SQL, en la instrucción CREATE PROCEDURE, indica que se crea un proceso nativo. Las instrucciones de T-SQL se compilan en el código máquina la primera vez que se usa el procedimiento nativo cada vez que la base de datos se recorre en línea. Las instrucciones de T-SQL ya no aguantan la interpretación lenta de cada instrucción.  
  
- Hemos visto el resultado de compilación nativa en duraciones de 1/100 de la duración interpretada.  
  
  
Un módulo nativo solamente puede hacer referencia a tablas con optimización para memoria, y no a tablas basadas en disco.  
  
Hay tres tipos de módulos compilados de forma nativa:  
  
- [Procedimientos almacenados compilados de forma nativa](../../relational-databases/in-memory-oltp/natively-compiled-stored-procedures.md).  
- Funciones definidas por el usuario (UDF) compiladas de forma nativa, que son escalares.  
- Desencadenadores compilados de forma nativa.  
  
  
#### <a name="availability-in-azure-sql-database"></a>Disponibilidad en Base de datos SQL de Azure  
  
OLTP en memoria y Almacén de columnas están disponibles en Azure SQL Database. Para detalles, consulte [Optimize Performance using In-Memory Technologies in SQL Database](https://docs.microsoft.com/azure/sql-database/sql-database-in-memory) (Optimizar el rendimiento con las tecnologías In-Memory en SQL Database).
  
  
<a name="ensure-compatibility-level-gteq-130-99c"></a>  
  
## <a name="1-ensure-compatibility-level--130"></a>1. Garantizar un compatibilidad >= 130  
  
  
Esta sección es la primera de una serie de secciones numeradas que muestran la sintaxis de Transact-SQL que puede usar para implementar características de OLTP en memoria.  
  
  
En primer lugar, es importante que la base de datos se establezca en un nivel de compatibilidad de al menos 130. A continuación figura el código de T-SQL para ver el nivel de compatibilidad actual en el que está establecida la base de datos actual.  
  
  
  
  
  
    SELECT d.compatibility_level  
        FROM sys.databases as d  
        WHERE d.name = Db_Name();  
  
  
  
  
A continuación figura el código de T-SQL para actualizar el nivel, si es necesario.  
  
  
  
  
    ALTER DATABASE CURRENT  
        SET COMPATIBILITY_LEVEL = 130;  
  
  
  
  
<a name="elevate-to-snapshot-26n"></a>  
  
## <a name="2-elevate-to-snapshot"></a>2. Elevar a SNAPSHOT  
  
  
Cuando una transacción implica una tabla basada en disco y una tabla con optimización para memoria, la llamamos *transacción entre contenedores*. En una transacción de este tipo es esencial que la parte con optimización para memoria de la transacción funcione en el nivel de aislamiento de la transacción llamado SNAPSHOT.  
  
Para exigir de forma confiable este nivel para tablas con optimización para memoria en una transacción entre contenedores, [modifique la configuración de la base de datos](../../t-sql/statements/alter-database-transact-sql-set-options.md) ejecutando el siguiente código T-SQL.  
  
  
  
  
    ALTER DATABASE CURRENT  
        SET MEMORY_OPTIMIZED_ELEVATE_TO_SNAPSHOT = ON;  
  
  
  
  
<a name="create-an-optimized-filegroup-24r"></a>  
  
## <a name="3-create-an-optimized-filegroup"></a>3. Crear un grupo de archivos optimizado  
  
  
En Microsoft SQL Server, antes de poder crear una tabla con optimización para memoria debe crear un grupo de archivos que declara CONTAINS MEMORY_OPTIMIZED_DATA. El grupo de archivos se asigna a la base de datos. Para obtener detalles, vea:  
  
- [FILEGROUP con optimización para memoria](../../relational-databases/in-memory-oltp/the-memory-optimized-filegroup.md)  
  
  
En Base de datos SQL de Azure, no es necesario y no se puede crear tal grupo de archivos.  

El siguiente ejemplo de script T-SQL habilita una base de datos para OLTP en memoria y configura todos los ajustes recomendados. Funciona con SQL Server y Azure SQL Database: [enable-in-memory-oltp.sql](https://raw.githubusercontent.com/Microsoft/sql-server-samples/master/samples/features/in-memory/t-sql-scripts/enable-in-memory-oltp.sql).
  
  
<a name="create-a-memory-optimized-table-26y"></a>  
  
## <a name="4-create-a-memory-optimized-table"></a>4. Crear una tabla con optimización para memoria  
  
  
  
  
La palabra clave de Transact-SQL fundamental es la palabra clave MEMORY_OPTIMIZED.  
  
  
  
  
    CREATE TABLE dbo.SalesOrder  
    (  
        SalesOrderId   integer        not null  IDENTITY  
            PRIMARY KEY NONCLUSTERED,  
        CustomerId     integer        not null,  
        OrderDate      datetime       not null  
    )  
        WITH  
            (MEMORY_OPTIMIZED = ON,  
            DURABILITY = SCHEMA_AND_DATA);  
  
  
  
  
Las instrucciones INSERT y SELECT de Transact-SQL en una tabla con optimización para memoria son las mismos que para una tabla normal.  
  
#### <a name="alter-table-for-memory-optimized-tables"></a>ALTER TABLE para tablas con optimización para memoria  
  
ALTER TABLE... ADD/DROP puede agregar o quitar una columna de una tabla con optimización para memoria o un índice.  
  
- CREATE INDEX y DROP INDEX no se pueden ejecutar en una tabla con optimización para memoria, use ALTER TABLE ... ADD/DROP INDEX en su lugar.  
- Para obtener detalles, vea [Modificar tablas con optimización para memoria](../../relational-databases/in-memory-oltp/altering-memory-optimized-tables.md).  
  
  
#### <a name="plan-your-memory-optimized-tables-and-indexes"></a>Planear sus índices y tablas con optimización para memoria  
  
  
- [Índices de tablas con optimización para memoria](../../relational-databases/in-memory-oltp/indexes-for-memory-optimized-tables.md)  
- [Construcciones Transact-SQL no admitidas por OLTP en memoria](../../relational-databases/in-memory-oltp/transact-sql-constructs-not-supported-by-in-memory-oltp.md)  
  
  
  
<a name="create-a-natively-compiled-stored-procedure-native-proc-29u"></a>  
  
## <a name="5-create-a-natively-compiled-stored-procedure-native-proc"></a>5. Crear un procedimiento almacenado compilado de forma nativa (procedimiento nativo)  
  
  
La palabra clave fundamental es NATIVE_COMPILATION.  
  
  
  
  
    CREATE PROCEDURE ncspRetrieveLatestSalesOrderIdForCustomerId  
        @_CustomerId   INT  
        WITH  
            NATIVE_COMPILATION,  
            SCHEMABINDING  
    AS  
    BEGIN ATOMIC  
        WITH  
            (TRANSACTION ISOLATION LEVEL = SNAPSHOT,  
            LANGUAGE = N'us_english')  
      
        DECLARE @SalesOrderId int, @OrderDate datetime;  
      
        SELECT TOP 1  
                @SalesOrderId = s.SalesOrderId,  
                @OrderDate    = s.OrderDate  
            FROM dbo.SalesOrder AS s  
            WHERE s.CustomerId = @_CustomerId  
            ORDER BY s.OrderDate DESC;  
      
        RETURN @SalesOrderId;  
    END;  
  
  
  
  
La palabra clave SCHEMABINDING significa que las tablas a las que se hace referencia en el procedimiento nativo no se puede quitar a menos que dicho procedimiento se quite primero. Para obtener detalles, vea [Crear procedimientos almacenados compilados de forma nativa](../../relational-databases/in-memory-oltp/creating-natively-compiled-stored-procedures.md).  
  
  
<a name="execute-the-native-proc-31e"></a>  
  
## <a name="6-execute-the-native-proc"></a>6. Ejecutar el procedimiento nativo  
  
  
Rellene la tabla con dos filas de datos.  
  
  
  
  
    INSERT into dbo.SalesOrder  
            ( CustomerId, OrderDate )  
        VALUES  
            ( 42, '2013-01-13 03:35:59' ),  
            ( 42, '2015-01-15 15:35:59' );  
  
  
  
  
Después seguirá una llamada EXECUTE al procedimiento almacenado compilado de forma nativa.  
  
  
  
  
    DECLARE @LatestSalesOrderId int, @mesg nvarchar(128);  
      
    EXECUTE @LatestSalesOrderId =  
        ncspRetrieveLatestSalesOrderIdForCustomerId 42;  
      
    SET @mesg = CONCAT(@LatestSalesOrderId,  
        ' = Latest SalesOrderId, for CustomerId = ', 42);  
    PRINT @mesg;  
      
    -- Here is the actual PRINT output:  
    -- 2 = Latest SalesOrderId, for CustomerId = 42  
  
  
  
  
<a name="guide-to-the-documentation-and-next-steps-32w"></a>  
  
### <a name="guide-to-the-documentation-and-next-steps"></a>Guía de la documentación y pasos siguientes  
  
  
Los ejemplos anteriores sin formato constituyen una base para aprender las características más avanzadas de OLTP en memoria. Las secciones siguientes constituyen una guía a las consideraciones especiales que convendría conocer y dónde puede encontrar los detalles sobre cada una de ellas.  
  
  
  
<a name="how-do-in-memory-oltp-features-work-so-much-faster-33v"></a>  
  
## <a name="how-in-memory-oltp-features-work-so-much-faster"></a>¿Cómo funcionan las características de OLTP en memoria tan rápido?  
  
  
Las siguientes subsecciones describen brevemente cómo funcionan las características de OLTP en memoria internamente para proporcionar un rendimiento mejorado.  
  
  
<a name="how-do-memory-optimized-tables-perform-faster-34q"></a>  
  
### <a name="how-memory-optimized-tables-perform-faster"></a>¿Cómo funcionan las tablas con optimización para memoria más rápido?  
  
  
**Doble naturaleza:** Una tabla con optimización para memoria tiene una doble naturaleza: una representación en memoria activa y la otra en el disco duro. Cada transacción se confirma con ambas representaciones de la tabla. Las transacciones funcionan en la representación memoria activa mucho más rápida. Las tablas con optimización para memoria se benefician de la mayor velocidad de la memoria activa en comparación con el disco. Además, la mayor agilidad de la memoria activa hace práctica una estructura de tabla más avanzada que se optimiza para velocidad. La estructura avanzada tampoco tiene páginas, por lo que evita la sobrecarga y la contención de bloqueos temporales y bloqueos por subproceso.  
  
  
**No hay bloqueos:** La tabla con optimización para memoria se basa en un enfoque *optimista* de los objetivos de la competencia de integridad de datos frente a la simultaneidad y el alto rendimiento. Durante la transacción, la tabla no coloca bloqueos en ninguna versión de las filas de datos actualizadas. Esto puede reducir considerablemente la contención en algunos sistemas de gran volumen.  
  
  
**Versiones de fila:** En lugar de bloqueos, la tabla con optimización para memoria agrega una nueva versión de una fila actualizada en la propia tabla, no en tempdb. La fila original se mantiene hasta que se confirma la transacción. Durante la transacción, otros procesos pueden leer la versión original de la fila.  
  
- Cuando se crean varias versiones de una fila para una tabla basada en disco, las versiones de fila se almacenan temporalmente en tempdb.  
  
  
**Menos tareas de registro:** Las versiones anterior y posterior de las filas actualizadas se mantienen en la tabla con optimización para memoria. El par de filas proporciona gran parte de la información que tradicionalmente se escribe en el archivo de registro. Esto permite al sistema escribir menos información y con menos frecuencia en el registro. Aún así, la integridad transaccional está garantizada.  
  
  
<a name="how-do-native-procs-perform-faster-35x"></a>  
  
### <a name="how-native-procs-perform-faster"></a>¿Cómo funcionan los procedimientos nativos más rápido?  
  
Convertir un procedimiento almacenado interpretado normal en un procedimiento almacenado compilado de forma nativa, reduce considerablemente el número de instrucciones que se ejecutan en tiempo de ejecución.  
  
  
<a name="trade-offs-of-in-memory-features-36j"></a>  
  
## <a name="trade-offs-of-in-memory-features"></a>Ventajas e inconvenientes de las características en memoria  
  
  
Como es habitual en informática, las mejoras de rendimiento que ofrecen las características en memoria son una solución de compromiso. Las mejores características ofrecen beneficios que son más valiosos que los costos adicionales de la característica. Puede encontrar instrucciones completas sobre los compromisos en:

- [Planear la adopción de características de OLTP en memoria en SQL Server](../../relational-databases/in-memory-oltp/plan-your-adoption-of-in-memory-oltp-features-in-sql-server.md)

En el resto de esta sección se enumeran algunas de las consideraciones principales de planeación y compromiso.
  
<a name="trade-offs-of-memory-optimized-tables-37d"></a>  
  
### <a name="trade-offs-of-memory-optimized-tables"></a>Ventajas e inconvenientes de las tablas con optimización para memoria  
  
  
**Calcular la memoria:** Debe calcular la cantidad de memoria activa que consumirá la tabla con optimización para memoria. El equipo debe tener la capacidad de memoria suficiente para hospedar una tabla con optimización para memoria. Para obtener detalles, vea:  
  
- [Supervisar y solucionar problemas de uso de memoria](../../relational-databases/in-memory-oltp/monitor-and-troubleshoot-memory-usage.md)  
- [Estimar los requisitos de memoria para las tablas con optimización para memoria](../../relational-databases/in-memory-oltp/estimate-memory-requirements-for-memory-optimized-tables.md)  
- [Tamaño de tabla y fila de las tablas con optimización para memoria](../../relational-databases/in-memory-oltp/table-and-row-size-in-memory-optimized-tables.md)  
  
  
**Dividir la tabla grande:** Una manera de satisfacer la demanda de grandes cantidades de memoria activa es dividir la tabla grande en partes en memoria que almacenen filas de datos *recientes calientes* frente a otras partes en el disco que almacenen filas *heredadas frías* (por ejemplo, pedidos de ventas que se han enviado y completado totalmente). Esta división es un proceso manual de diseño e implementación. Vea:  
  
- [Creación de particiones en el nivel de aplicación](../../relational-databases/in-memory-oltp/application-level-partitioning.md)  
- [Patrón de aplicación para crear particiones de tablas con optimización para memoria](../../relational-databases/in-memory-oltp/application-pattern-for-partitioning-memory-optimized-tables.md)  
  
  
<a name="trade-offs-of-native-procs-38p"></a>  
  
### <a name="trade-offs-of-native-procs"></a>Ventajas e inconvenientes de los procedimientos nativos  
  
  
- Un procedimiento almacenado compilado de forma nativa no puede acceder a una tabla basada en disco. Un procedimiento nativo solo puede acceder a tablas optimizadas en memoria.  
- Cuando se ejecuta un procedimiento nativo por primera vez después de que el servidor o base de datos vuelve a estar en línea, el procedimiento nativo se debe compilar de nuevo una vez. Esto provoca un retraso antes de que el procedimiento nativo empieza a ejecutarse.  
  
  
<a name="advanced-considerations-for-memory-optimized-tables-39n"></a>  
  
## <a name="advanced-considerations-for-memory-optimized-tables"></a>Consideraciones avanzadas sobre tablas con optimización para memoria  
  
  
Los[índices de tablas con optimización para memoria](../../relational-databases/in-memory-oltp/indexes-for-memory-optimized-tables.md) difieren en algunos aspectos de los índices de las tablas en disco tradicionales.  
  
- Los[índices de hash](../../relational-databases/in-memory-oltp/hash-indexes-for-memory-optimized-tables.md) solo están disponibles en las tablas con optimización para memoria.  
  
  
Debe tener un plan para asegurarse de que haya suficiente memoria activa para la tabla con optimización para memoria planeada y sus índices. Vea:  
  
- [Crear y administrar el almacenamiento de objetos con optimización para memoria](../../relational-databases/in-memory-oltp/creating-and-managing-storage-for-memory-optimized-objects.md)  
  
  
Es posible declarar una tabla con optimización para memoria con DURABILITY = SCHEMA_ONLY:  
  
- Esta sintaxis indica al sistema que descarte todos los datos de la tabla con optimización para memoria cuando la base de datos se desconecta. Solo se conserva la definición de tabla.  
- Cuando la base de datos vuelva a estar en línea, la tabla con optimización para memoria se vuelve a cargar en la memoria activa, vacía de datos.  
- Las tablas SCHEMA_ONLY pueden ser una mejor [alternativa a las tablas temporales](../../relational-databases/in-memory-oltp/faster-temp-table-and-table-variable-by-using-memory-optimization.md) en tempdb, cuando hay implicados varios miles de filas.  
  
  
Las variables de tabla también pueden declararse con optimización para memoria. Vea:  
  
- [Tabla temporal y variable de tabla más rápidas con optimización para memoria](../../relational-databases/in-memory-oltp/faster-temp-table-and-table-variable-by-using-memory-optimization.md)  
  
  
  
<a name="advanced-considerations-for-natively-compiled-modules-40k"></a>  
  
## <a name="advanced-considerations-for-natively-compiled-modules"></a>Consideraciones avanzadas para módulos compilados de forma nativa  
  
  
Los tipos de módulos compilados de forma nativa disponibles a través de Transact-SQL son:  
  
- Procedimientos almacenados compilados de forma nativa (procedimientos nativos).  
- [Funciones escalares definidas por el usuario](../../relational-databases/in-memory-oltp/scalar-user-defined-functions-for-in-memory-oltp.md)compiladas de forma nativa.  
- Desencadenadores compilados de forma nativa (desencadenadores nativos).  
  - Solo los desencadenadores compilados de forma nativa se permiten en tablas con optimización para memoria.  
- [Funciones con valores de tabla](../../relational-databases/user-defined-functions/create-user-defined-functions-database-engine.md)compiladas de forma nativa.  
  - [Mejora del rendimiento de la tabla temporal y de variable de tabla mediante optimización de memoria](https://blogs.msdn.microsoft.com/sqlserverstorageengine/2016/03/21/improving-temp-table-and-table-variable-performance-using-memory-optimization/)  
  
  
Una función definida por el usuario (UDF) compilada de forma nativa se ejecuta más rápido que una UDF interpretada. Debe tener en cuenta lo siguiente con respecto a las UDF:  
  
- Cuando una instrucción SELECT de T-SQL usa una UDF, siempre se llama una vez a la UDF por cada fila devuelta.  
  - Las UDF nunca se ejecutan en línea, sino que siempre se llaman.  
  - La distinción compilada es menos significativa de lo que es la sobrecarga de llamadas repetidas que es inherente a todas las UDF.  
  - A pesar de ello, la sobrecarga de llamadas a UDF suele ser aceptable en la práctica.  
  
Para obtener datos de prueba y una explicación del rendimiento de UDF nativas, vea:  
  
  - [Suavizar el impacto de RBAR con UDF compiladas de forma nativa en SQL Server 2016](https://blogs.msdn.microsoft.com/sqlcat/2016/02/17/soften-the-rbar-impact-with-native-compiled-udfs-in-sql-server-2016/)  
  - La [excelente entrada de blog escrita por Gail Shaw](http://sqlinthewild.co.za/index.php/2016/01/12/natively-compiled-user-defined-functions/), con fecha de enero de 2016.  
  
  
<a name="documentation-guide-for-memory-optimized-tables-41z"></a>  
  
## <a name="documentation-guide-for-memory-optimized-tables"></a>Guía de documentación para tablas con optimización para memoria  
  
  
Estos son vínculos a otros artículos que tratan consideraciones especiales para tablas con optimización para memoria:  
  
- [Migrar a OLTP en memoria](../../relational-databases/in-memory-oltp/migrating-to-in-memory-oltp.md)  
  - [Determinar si una tabla o un procedimiento almacenado se debe pasar a OLTP en memoria](../../relational-databases/in-memory-oltp/determining-if-a-table-or-stored-procedure-should-be-ported-to-in-memory-oltp.md)  
  - El informe de análisis rendimiento de transacciones de SQL Server Management Studio ayuda a evaluar si OLTP en memoria mejorará el rendimiento de la aplicación de base de datos.  
  - Utilice el [Asesor de optimización de memoria](../../relational-databases/in-memory-oltp/memory-optimization-advisor.md) que le ayudarán a migrar la tabla de base de datos basada en disco a OLTP en memoria.   
- [Hacer copia de seguridad, restaurar y recuperar tablas con optimización para memoria](http://msdn.microsoft.com/library/3f083347-0fbb-4b19-a6fb-1818d545e281)  
  - El almacenamiento usado por las tablas con optimización para memoria puede ser mucho mayor que el tamaño de la memoria y eso afecta al tamaño de la copia de seguridad de la base de datos.  
- [Transacciones con tablas con optimización para memoria](../../relational-databases/in-memory-oltp/transactions-with-memory-optimized-tables.md)  
  - Incluye información sobre la lógica de reintento en T-SQL para las transacciones en tablas con optimización para memoria.  
- [Compatibilidad de Transact-SQL con OLTP en memoria](../../relational-databases/in-memory-oltp/transact-sql-support-for-in-memory-oltp.md)  
  - Los tipos de datos y T-SQL admitidos y no admitidos, para tablas con optimización para memoria y procedimientos nativos.  
- [Enlazar una base de datos con tablas con optimización para memoria a un grupo de recursos de servidor](../../relational-databases/in-memory-oltp/bind-a-database-with-memory-optimized-tables-to-a-resource-pool.md), que analiza una consideración avanzada opcional.  
  
  
  
<a name="documentation-guide-for-native-procs-42b"></a>  
  
## <a name="documentation-guide-for-native-procs"></a>Guía de documentación para procedimientos nativos  
  
  
  
<a name="related-links-43f"></a>  
  
## <a name="related-links"></a>Vínculos relacionados  
  
- Artículo inicial: [OLTP en memoria (optimización en memoria)](../../relational-databases/in-memory-oltp/in-memory-oltp-in-memory-optimization.md)  
  
  
Los artículos siguientes incluyen código para demostrar las mejoras de rendimiento que se pueden lograr con el uso de OLTP en memoria:  
  
- [Demostración: mejora de rendimiento de OLTP en memoria](../../relational-databases/in-memory-oltp/demonstration-performance-improvement-of-in-memory-oltp.md) ofrece una demostración a pequeña escala de las posibles mejoras de rendimiento más grandes.  
- [Sample Database for In-Memory OLTP (Base de datos de ejemplo para OLTP en memoria)](../../relational-databases/in-memory-oltp/sample-database-for-in-memory-oltp.md) ofrece una demostración de escala mayor.  
  
  
  
\<!--  
  
e1328615-6b59-4473-8a8d-4f360f73187d, dn817827.aspx,  "Introducción al almacén de columnas para análisis operativos en tiempo real"  
  
f98af4a5-4523-43b1-be8d-1b03c3217839, gg492088.aspx, "Guía de índices de almacén de columnas"  
  
14dddf81-b502-49dc-a6b6-d18b1ae32d2b, dn133165.aspx, "Tablas con optimización para memoria"  
  
d5ed432c-10c5-4e4f-883c-ef4d1fa32366, dn133184.aspx, "Procedimientos almacenados compilados de forma nativa"  
  
14106cc9-816b-493a-bcb9-fe66a1cd4630, dn639109.aspx, "El grupo de archivos con optimización para memoria"  
  
f222b1d5-d2fa-4269-8294-4575a0e78636, dn465873.aspx, "Enlazar una base de datos con tablas con optimización para memoria a un grupo de recursos de servidor"  
  
86805eeb-6972-45d8-8369-16ededc535c7, dn511012.aspx, "Índices de las tablas con optimización para memoria"  
  
16ef63a4-367a-46ac-917d-9eebc81ab29b, dn133166.aspx, "Directrices para usar índices en las tablas con optimización para memoria"  
  
e3f8009c-319d-4d7b-8993-828e55ccde11, dn246937.aspx, "Construcciones Transact-SQL no admitidas por OLTP en memoria"  
  
2cd07d26-a1f1-4034-8d6f-f196eed1b763, dn133169.aspx, "Transacciones en tablas con optimización para memoria"  
NOTA: VEA mt668425.aspx "Comportamientos y directrices para las transacciones con tablas con optimización para memoria", se reemplazará en breve.  
f2a35c37-4449-49ee-8bba-928028f1de66, dn169141.aspx, "Instrucciones para la lógica de reintento de transacciones en tablas con optimización para memoria"  
  
7a458b9c-3423-4e24-823d-99573544c877, dn465869.aspx, "Supervisar y solucionar problemas de uso de memoria"  
  
5c5cc1fc-1fdf-4562-9443-272ad9ab5ba8, dn282389.aspx, "Estimar los requisitos de memoria para las tablas con optimización para memoria"  
  
b0a248a4-4488-4cc8-89fc-46906a8c24a1, dn205318.aspx, "Tamaño de tabla y fila de las tablas con optimización para memoria"  
  
162d1392-39d2-4436-a4d9-ee5c47864c5a, dn296452.aspx, "Creación de particiones en el nivel de aplicación"  
  
3f867763-a8e6-413a-b015-20e9672cc4d1, dn133171.aspx, "Patrón de aplicación para crear particiones de tablas con optimización para memoria"  
  
86805eeb-6972-45d8-8369-16ededc535c7, dn511012.aspx, "Índices de las tablas con optimización para memoria"  
  
d82f21fa-6be1-4723-a72e-f2526fafd1b6, dn465872.aspx, "Administración de memoria para OLTP con optimización para memoria"  
  
622aabe6-95c7-42cc-8768-ac2e679c5089, dn133174.aspx, "Crear y administrar el almacenamiento de objetos con optimización para memoria"  
  
bd102e95-53e2-4da6-9b8b-0e4f02d286d3, dn535766.aspx, "Variables de tabla con optimización para memoria"; "Variable de tabla de una tabla con optimización para memoria"  
OBSOLETO. En su lugar, vea 38512a22-7e63-436f-9c13-dde7cf5c2202, mt718711.aspx, "Tabla temporal y variable de tabla más rápidas con optimización para memoria"  
  
  
f0d5dd10-73fd-4e05-9177-07f56552bdf7, ms191320.aspx, "Crear funciones definidas por el usuario (motor de base de datos)"; "Funciones con valores de tabla"  
  
d2546e40-fdfc-414b-8196-76ed1f124bf5, dn935012.aspx, "Funciones escalares definidas por el usuario para OLTP en memoria"; "Funciones escalares definidas por el usuario"  
  
405cdac5-a0d4-47a4-9180-82876b773b82, dn247639.aspx, "Migrar a OLTP en memoria"  
  
3f083347-0fbb-4b19-a6fb-1818d545e281, dn624160.aspx, "Hacer copia de seguridad, restaurar y recuperar tablas con optimización para memoria"  
  
690b70b7-5be1-4014-af97-54e531997839, dn269114.aspx, "Modificar tablas con optimización para memoria"  
  
  
b1cc7c30-1747-4c21-88ac-e95a5e58baac, dn133080.aspx, "Propiedades, vistas del sistema, procedimientos almacenados, tipos de espera y DMV nuevos y actualizados para OLTP en memoria"  
. . . . .  
TAMBIÉN: "Compatibilidad de Transact-SQL con OLTP en memoria"  
  
  
c1ef96f1-290d-4952-8369-2f49f27afee2, dn205133.aspx, "Determinar si una tabla o un procedimiento almacenado se debe pasar a OLTP en memoria"  
  
181989c2-9636-415a-bd1d-d304fc920b8a, dn284308.aspx, "Asesor de optimización de memoria"  
  
55548cb2-77a8-4953-8b5a-f2778a4f13cf, dn452282.aspx, "Supervisar el rendimiento de los procedimientos almacenados compilados de forma nativa"  
  
d3898a47-2985-4a08-bc70-fd8331a01b7b, dn358355.aspx, "Asistente de compilación nativa"  
  
f43faad4-2182-4b43-a76a-0e3b405816d1, dn296678.aspx, "Problemas de migración para los procedimientos almacenados compilados de forma nativa"  
  
e1d03d74-2572-4a55-afd6-7edf0bc28bdb, dn133186.aspx, "OLTP en memoria (optimización en memoria)"  
  
c6def45d-d2d4-4d24-8068-fab4cd94d8cc, dn530757.aspx, "Demostración: mejora de rendimiento de OLTP en memoria"  
  
405cdac5-a0d4-47a4-9180-82876b773b82, dn247639.aspx, "Migrar a OLTP en memoria"  
  
f76fbd84-df59-4404-806b-8ecb4497c9cc, bb522682.aspx, "Opciones de ALTER DATABASE SET (Transact-SQL)"  
  
e6b34010-cf62-4f65-bbdf-117f291cde7b, dn452286.aspx, "Crear procedimientos almacenados compilados de forma nativa"  
  
df347f9b-b950-4e3a-85f4-b9f21735eae3, mt465764.aspx, "Base de datos de ejemplo para OLTP en memoria"  
  
38512a22-7e63-436f-9c13-dde7cf5c2202, mt718711.aspx, "Tabla temporal y variable de tabla más rápidas con optimización para memoria"  
  
38512a22-7e63-436f-9c13-dde7cf5c2202, mt718711.aspx, "Tabla temporal y variable de tabla más rápidas con optimización para memoria"  
  
  
  
  
H1 # Inicio rápido 1: Tecnologías en memoria para acelerar cargas de trabajo transaccionales  
{1c25a164-547d-43c4-8484-6b5ee3cbaf3a} en MAYÚSCULAS  
mt718711.aspx en MSDN  
  
GeneMi, 2016-05-07 00:07 a.m.  
-->  
  
  
  

