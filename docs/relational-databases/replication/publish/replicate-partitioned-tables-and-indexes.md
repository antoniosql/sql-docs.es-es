---
title: "Replicar tablas e &#237;ndices con particiones | Microsoft Docs"
ms.custom: ""
ms.date: "09/10/2015"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "replication"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "índices con particiones [SQL Server], replicar"
  - "tablas con particiones [SQL Server], replicar"
  - "replicación [SQL Server], tablas con particiones"
  - "publicar [replicación de SQL Server], tablas con particiones"
  - "replicación transaccional, tablas con particiones"
ms.assetid: c9fa81b1-6c81-4c11-927b-fab16301a8f5
caps.latest.revision: 20
author: "BYHAM"
ms.author: "rickbyh"
manager: "jhubbard"
caps.handback.revision: 20
---
# Replicar tablas e &#237;ndices con particiones
  La creación de particiones facilita el uso de tablas o índices grandes, ya que permite administrar y tener acceso a subconjuntos de datos de forma rápida y eficaz, y mantener la integridad de una recopilación de datos al mismo tiempo. Para obtener más información, vea [Partitioned Tables and Indexes](../../../relational-databases/partitions/partitioned-tables-and-indexes.md). La replicación es compatible con la creación de particiones al proporcionar un conjunto de propiedades que especifican cómo se deben tratar las tablas y los índices con particiones.  
  
## Propiedades de artículos para replicación transaccional y de mezcla  
 En la tabla siguiente se enumeran los objetos que se utilizan para la partición de datos.  
  
|Object|Se crea utilizando|  
|------------|----------------------|  
|Tabla o índice con particiones|CREATE TABLE o CREATE INDEX|  
|Función de partición|CREATE PARTITION FUNCTION|  
|Esquema de partición|CREATE PARTITION SCHEME|  
  
 El primer conjunto de propiedades relacionadas con la creación de particiones son las opciones de esquema de artículo que determinan si las particiones de los objetos se deben copiar en el suscriptor. Estas opciones de esquema se pueden establecer de varias maneras:  
  
-   En la página **Propiedades del artículo** del Asistente para nueva publicación o en el cuadro de diálogo Propiedades de la publicación. Para copiar los objetos enumerados en la tabla anterior, especifique el valor **true** para las propiedades **Copiar esquemas de particionamiento de tabla** y **Crear esquemas de particionamiento de índice**. Para obtener información sobre cómo tener acceso a la **Propiedades del artículo** página, consulte [Ver y modificar propiedades de publicación](../../../relational-databases/replication/publish/view-and-modify-publication-properties.md).  
  
-   Mediante el uso de la *schema_option* parámetro de uno de los siguientes procedimientos almacenados:  
  
    -   [sp_addarticle](../../../relational-databases/system-stored-procedures/sp-addarticle-transact-sql.md) o [sp_changearticle](../../../relational-databases/system-stored-procedures/sp-changearticle-transact-sql.md) para la replicación transaccional  
  
    -   [sp_addmergearticle](../../../relational-databases/system-stored-procedures/sp-addmergearticle-transact-sql.md) o [sp_changemergearticle](../../../relational-databases/system-stored-procedures/sp-changemergearticle-transact-sql.md) para la replicación de mezcla  
  
     Para copiar los objetos enumerados en la tabla anterior, especifique los valores de opciones de esquema adecuados. Para obtener información sobre cómo especificar opciones de esquema, vea [Specify Schema Options](../../../relational-databases/replication/publish/specify-schema-options.md).  
  
 La replicación copia los objetos en el suscriptor durante la sincronización inicial. Si el esquema de partición utiliza grupos de archivos distintos del archivo de grupos PRIMARY, esos grupos de archivos deben existir en el suscriptor antes de la sincronización inicial.  
  
 Una vez inicializado el suscriptor, los cambios de los datos se propagan al suscriptor y se aplican a las particiones adecuadas. Sin embargo, no se admiten cambios en el esquema de partición. Las replicaciones transaccional y de mezcla no admiten la replicación de los comandos siguientes: ALTER PARTITION FUNCTION, ALTER PARTITION SCHEME, ni la instrucción REBUILD WITH PARTITION de ALTER INDEX. Los cambios asociados a ellos no se replicarán automáticamente al suscriptor. Es responsabilidad del usuario realizar modificaciones similares en el suscriptor de forma manual.  
  
## Compatibilidad de la replicación con la modificación de particiones  
 Una de las ventajas principales de crear particiones en una tabla es la posibilidad de mover rápida y eficazmente subconjuntos de datos entre particiones. Los datos se mueven utilizando el comando SWITCH PARTITION. De forma predeterminada, cuando en una tabla se habilita la replicación, las operaciones SWITCH PARTITION se bloquean por las razones siguientes:  
  
-   Si los datos se mueven a una tabla o fuera de una tabla que existe en el publicador pero que no existe en el suscriptor, ambos pueden llegar a ser incoherentes entre sí. Este problema se produce normalmente cuando los datos se mueven a o fuera de una tabla de ensayo.  
  
-   Si el suscriptor tiene para la tabla con particiones una definición diferente de la del publicador, se producirá un error en el Agente de distribución cuando intente aplicar los cambios en el suscriptor.  
  
 A pesar de estos posibles problemas, la modificación de particiones puede habilitarse en la replicación transaccional. Antes de habilitar la modificación de particiones, asegúrese de que todas las tablas implicadas en ella existen en el publicador y en el suscriptor, y de que la tabla y las definiciones de partición son las mismas.  
  
 Cuando las particiones tienen el mismo esquema de partición exactos en los publicadores y suscriptores puede activar *allow_partition_switch* junto con *replication_partition_switch* que solo replicará la instrucción switch de partición en el suscriptor. También puede activar *allow_partition_switch* sin replicación de DDL. Esto resulta útil en el caso en que desee distribuir los meses anteriores de la partición pero mantener la partición replicada para otro año a efectos de copia de seguridad en el suscriptor.  
  
 Si habilita la conmutación de particiones en SQL Server 2008 R2 a través de la versión actual, puede que también necesite las operaciones de división y combinación más adelante. Antes de ejecutar una operación de división o combinación en una tabla replicada, asegúrese de que la partición en cuestión no tenga ningún comando replicado pendiente. También debe asegurarse de que no se ejecuten operaciones DML en la partición durante las operaciones de división y combinación. Si hay transacciones que no ha procesado el lector del registro o si se realizan operaciones de DML en una partición de una tabla replicada mientras se ejecuta una operación de división o combinación (que implica la misma partición), se podría producir un error de procesamiento con el agente de registro del LOG. Para corregir el error, puede solicitar que se vuelva a inicializar la suscripción.  
  
> [!WARNING]  
>  No debe habilitar la modificación de particiones para las publicaciones punto a punto, debido a la columna oculta que se usa para detectar y solucionar conflictos.  
  
### Habilitar la modificación de particiones  
 Las propiedades siguientes de las publicaciones transaccionales permiten a los usuarios controlar el comportamiento de la modificación de particiones en un entorno replicado:  
  
-   **@allow_partition_switch**, cuando se establece en **true**, SWITCH PARTITION se puede ejecutar en la base de datos de publicación.  
  
-   **@replicate_partition_switch** determina si se debe replicar la instrucción SWITCH PARTITION de DDL para los suscriptores. Esta opción sólo es válida cuando **@allow_partition_switch** está establecido en **true**.  
  
 Puede establecer estas propiedades mediante [sp_addpublication](../../../relational-databases/system-stored-procedures/sp-addpublication-transact-sql.md) cuando se crea la publicación o mediante [sp_changepublication](../../../relational-databases/system-stored-procedures/sp-changepublication-transact-sql.md) después de crear la publicación. Según se indicaba anteriormente, la replicación de mezcla no admite la modificación de particiones. Para ejecutar SWITCH PARTITION en una tabla en la que está habilitada la replicación de mezcla, quite la tabla de la publicación.  
  
## Vea también  
 [Publicar datos y objetos de base de datos](../../../relational-databases/replication/publish/publish-data-and-database-objects.md)  
  
  