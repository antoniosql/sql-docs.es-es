---
title: "Contenedor Foreach Loop | Microsoft Docs"
ms.custom: 
  - "SQL2016_New_Updated"
ms.date: "03/14/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "integration-services"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "sql13.dts.designer.foreachloopcontainer.f1"
  - "sql13.dts.designer.foreachloopcontainer.general.f1"
  - "sql13.dts.designer.foreachloopcontainer.collection.f1"
  - "sql13.dts.designer.foreachloopcontainer.mapping.f1"
  - "sql13.dts.designer.schemarestrictions.f1"
  - "sql13.dts.designer.foreachitemcolumns.f1"
  - "sql13.dts.designer.selectsmoenumeration.f1"
helpviewer_keywords: 
  - "repetir flujo de control"
  - "Foreach, contenedores de bucles"
  - "Foreach, enumeradores [Integration Services]"
  - "contenedores [Integration Services], Bucle Foreach"
ms.assetid: dd6cc2ba-631f-4adf-89dc-29ef449c6933
caps.latest.revision: 73
author: "douglaslMS"
ms.author: "douglasl"
manager: "jhubbard"
caps.handback.revision: 72
---
# Contenedor Foreach Loop
  El contenedor de bucles Foreach define un flujo de control que se repite en un paquete. La implementación del bucle es similar a la estructura de bucle **Foreach** de los lenguajes de programación. En un paquete, los bucles se habilitan mediante un enumerador Foreach.  El contenedor de bucles Foreach repite el flujo de control para cada miembro de un enumerador especificado.  
  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] proporciona los siguientes tipos de enumerador:  
  
-   Enumerador de ADO para Foreach, para enumerar filas de tablas. Por ejemplo, puede obtener las filas de un conjunto de registros ADO.  
  
     El destino de conjunto de registros guarda los datos en memoria, en un conjunto de registros que se almacena en una variable de paquete del tipo de datos **Object** . Normalmente usa un contenedor de bucles Foreach con el enumerador Foreach ADO para procesar una fila del conjunto cada vez. La variable especificada para el enumerador Foreach ADO debe ser del tipo de datos Object. Para obtener más información acerca del destino de conjunto de registros, vea [Use a Recordset Destination](../../integration-services/data-flow/use-a-recordset-destination.md).  
  
-   Enumerador de conjunto de filas del esquema para Foreach de ADO.NET, para enumerar la información de esquema sobre un origen de datos. Por ejemplo, puede enumerar y obtener una lista de tablas de la base de datos [!INCLUDE[ssSampleDBnormal](../../includes/sssampledbnormal-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .  
  
-   Enumerador Foreach File para enumerar los archivos de una carpeta. El enumerador puede recorrer subcarpetas. Por ejemplo, puede leer todos los archivos de la carpeta y subcarpetas de Windows que tengan la extensión de nombre de archivo *.log.  
  
-   Enumerador de variable para Foreach, para enumerar el objeto enumerable contenido en una variable especificada. El objeto enumerable puede ser una matriz, una **DataTable** de ADO.NET, un enumerador de [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)], etc. Por ejemplo, puede enumerar los valores de una matriz que contenga los nombres de los servidores.  
  
-   Enumerador de elementos para Foreach para enumerar elementos que son colecciones. Por ejemplo, puede enumerar los nombres de los ejecutables y directorios de trabajo que utiliza una tarea Ejecutar proceso.  
  
-   Enumerador de lista de nodos para Foreach para enumerar el conjunto de resultados de una expresión del Lenguaje de rutas XML (XPath). Por ejemplo, esta expresión enumera y obtiene una lista de todos los autores de la época clásica: `/authors/author[@period='classical']`.  
  
-   Enumerador de SMO para Foreach para enumerar objetos de Objetos de administración de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)](SMO). Por ejemplo, puede enumerar y obtener una lista de vistas de una base de datos de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .  
  
-   Enumerador de archivos HDFS para Foreach para enumerar los archivos HDFS en la ubicación especificada de HDFS.  
  
-   Enumerador de blobs de Azure para Foreach usado para enumerar blobs en un contenedor de blobs en Almacenamiento de Azure.  
  
 El siguiente diagrama muestra un contenedor de bucles Foreach que tiene una tarea Sistema de archivos. El bucle Foreach utiliza el Enumerador de archivos para Foreach y la tarea Sistema de archivos está configurada para copiar un archivo. Si la carpeta especificada por el enumerador contiene cuatro archivos, el bucle se repetirá cuatro veces y copiará cuatro archivos.  
  
 ![Contenedor de bucles Foreach que enumera una carpeta](../../integration-services/control-flow/media/ssis-foreachloop.gif "Contenedor de bucles Foreach que enumera una carpeta")  
  
 Puede utilizar una combinación de variables y expresiones de propiedades para actualizar la propiedad del objeto de paquete con el valor de colección de enumerador. Primero debe asignar el valor de colección a una variable definida por el usuario y después debe implementar una expresión de propiedad en la propiedad que utiliza la variable. Por ejemplo, el valor de la colección del Enumerador de archivos para Foreach se asigna a una variable denominada **MyFile**, que se usa en la expresión de propiedad para la propiedad Subject de una tarea Enviar correo. Cuando se ejecuta el paquete, la propiedad Subject se actualiza con el nombre de un archivo cada vez que se repite el bucle. Para más información, vea [Usar expresiones de propiedad en paquetes](../../integration-services/expressions/use-property-expressions-in-packages.md).  
  
 Las variables asignadas al valor de colección del enumerador también se pueden usar en expresiones y en scripts.  
  
 Un contenedor de bucles Foreach puede incluir varias tareas y contenedores, pero solamente puede usar un tipo de enumerador. Si el contenedor de bucles Foreach incluye varias tareas, puede asignar el valor de colección del enumerador a varias propiedades de cada tarea.  
  
 Puede establecer un atributo de transacción en el contenedor de bucles Foreach para definir una transacción para un subconjunto del flujo de control del paquete. De esta manera, puede administrar las transacciones en el nivel del contenedor de bucles Foreach en lugar de hacerlo en el nivel de paquete. Por ejemplo, si un contenedor de bucles Foreach repite un flujo de control que actualiza las dimensiones y las tablas de hechos de un esquema de estrella, puede configurar una transacción para asegurarse de que o se actualizan todas las tablas de hechos correctamente o no se actualiza ninguna. Para más información, vea [Transacciones de Integration Services](../../integration-services/integration-services-transactions.md).  
  
## Tipos de enumerador  
 Los enumeradores son configurables. Deberá proporcionar información diferente en función del enumerador.  
  
 En la tabla siguiente se resume la información requerida por cada tipo de enumerador.  
  
|Enumerador|Requisitos de configuración|  
|----------------|--------------------------------|  
|ADO para Foreach|Especifique la variable de origen del objeto ADO y el modo de enumerador. La variable debe ser del tipo de datos Object.|  
|Conjunto de filas del esquema para Foreach de ADO.NET|Especifique la conexión a una base de datos y el esquema que se va a enumerar.|  
|Archivos para Foreach|Especifique una carpeta y los archivos que se van a enumerar, el formato de nombre de archivo de los archivos recuperados y si hay que recorrer las subcarpetas.|  
|Variable para Foreach|Especifique la variable que contiene los objetos que se van a enumerar.|  
|Foreach Item|Defina los elementos de la colección Foreach Item, incluidas las columnas y los tipos de datos de columna.|  
|Lista de nodos para Foreach|Especifique el origen del documento XML y configure la operación de XPath.|  
|SMO para Foreach|Especifique la conexión a una base de datos y los objetos SMO que se van a enumerar.|  
|Enumerador de archivos HDFS para Foreach|Especifique una carpeta y los archivos que se van a enumerar, el formato de nombre de archivo de los archivos recuperados y si hay que recorrer las subcarpetas.|  
|Por cada blob de Azure|Deberá especificar el contenedor de blobs de Azure que contendrá los blobs que se van a enumerar.|  
  
## Expresiones de propiedad en contenedores de bucles Foreach  
 Se puede configurar que los paquetes ejecuten varios ejecutables simultáneamente. Esta configuración se debe utilizar con precaución cuando el paquete incluye un contenedor de bucles Foreach que implementa expresiones de propiedad.  
  
 Con frecuencia, es útil implementar una expresión de propiedad para establecer el valor de la propiedad ConnectionString de los administradores de conexiones que usan los enumeradores de bucle Foreach. La expresión de propiedad de ConnectionString se establece con una variable que se asigna al valor de la colección del enumerador y se actualiza en cada iteración del bucle.  
  
 Para evitar consecuencias negativas de tiempos no determinativos en la ejecución paralela de tareas en el bucle, se debe configurar el paquete para que ejecute solamente un ejecutable a la vez. Por ejemplo, si un paquete puede ejecutar varias tareas simultáneamente, un contenedor de bucles Foreach que enumera archivos en la carpeta, recupera los nombres de los archivos y luego utiliza una tarea Ejecutar SQL para insertar los nombres de archivos en una tabla puede incurrir en conflictos de escritura cuando dos instancias de la tarea Ejecutar SQL intentan escribir al mismo tiempo. Para más información, vea [Usar expresiones de propiedad en paquetes](../../integration-services/expressions/use-property-expressions-in-packages.md).  
  
## Tareas relacionadas  
 Puede establecer propiedades a través del Diseñador de [!INCLUDE[ssIS](../../includes/ssis-md.md)] o mediante programación.  
  
 Para obtener información detallada sobre cómo establecer estas propiedades en el Diseñador [!INCLUDE[ssIS](../../includes/ssis-md.md)] , haga clic en uno de los temas siguientes:  
  
-   [configurar un contenedor de bucles Foreach](../Topic/Configure%20a%20Foreach%20Loop%20Container.md)  
  
-   [Establecer las propiedades de tareas o contenedores](../Topic/Set%20the%20Properties%20of%20a%20Task%20or%20Container.md)  
  
 Para obtener información detallada sobre cómo establecer estas propiedades mediante programación, haga clic en el tema siguiente:  
  
-   <xref:Microsoft.SqlServer.Dts.Runtime.ForEachLoop>  
  
## Contenido relacionado  
 Entrada de blog, sobre [SSIS para cada enumerador de lista de nodo](http://go.microsoft.com/fwlink/?LinkId=220671), en bidn.com.  
  
## Vea también  
 [Flujo de control](../../integration-services/control-flow/control-flow.md)   
 [Contenedores de Integration Services](../../integration-services/control-flow/integration-services-containers.md)  
  
  