---
title: "Origen de archivo sin formato | Microsoft Docs"
ms.custom: ""
ms.date: "03/01/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "integration-services"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "sql13.dts.designer.rawfilesource.f1"
helpviewer_keywords: 
  - "orígenes [Integration Services], archivo sin formato"
  - "datos sin procesar [Integration Services]"
  - "archivo sin formato, origen"
ms.assetid: 5b4daea5-7f76-4674-aa77-0a79f9f97f7d
caps.latest.revision: 43
author: "douglaslMS"
ms.author: "douglasl"
manager: "jhubbard"
caps.handback.revision: 43
---
# Origen de archivo sin formato
  El origen de archivo sin formato lee datos sin formato de un archivo. Como la representación de los datos es la nativa del origen, no es necesario traducir los datos y prácticamente no es necesario analizar el archivo. Esto significa que el origen de archivo sin formato puede leer datos más rápidamente que otros orígenes, como el origen de archivo plano o el origen de OLE DB.  
  
 El origen de archivo sin formato se usa para recuperar datos sin formato escritos previamente por el destino de archivo sin formato. También puede señalar el origen de archivo sin formato para un archivo sin formato vacío que contenga solo las columnas (archivo solo de metadatos). El destino de archivo sin formato se usa para generar el archivo de solo metadatos sin tener que ejecutar el paquete. Para más información, consulte [Raw File Destination](../../integration-services/data-flow/raw-file-destination.md).  
  
 El archivo sin formato contiene información sobre el orden. El destino de archivo sin formato guarda toda la información sobre el orden incluidas las marcas de comparación para las columnas de cadena. El origen de archivo sin formato lee y respeta la información sobre el orden. Tiene la opción de configurar el origen de archivo sin formato para omitir los marcas de orden en el archivo; para ello use el Editor avanzado. Para obtener más información acerca de las marcas de comparación, vea [Comparing String Data](../../integration-services/data-flow/comparing-string-data.md).  
  
 Para configurar el archivo sin formato, especifique el nombre del archivo leído por el origen de archivo sin formato.  
  
> [!NOTE]  
>  Este origen no usa un administrador de conexiones.  
  
 Este origen tiene una salida. No admite una salida de error.  
  
## Configuración del origen de archivo sin formato  
 Puede establecer propiedades a través del Diseñador de [!INCLUDE[ssIS](../../includes/ssis-md.md)] o mediante programación.  
  
 El cuadro de diálogo **Editor avanzado** indica las propiedades que se pueden establecer mediante programación. Para obtener más información acerca de las propiedades que puede establecer a través del cuadro de diálogo **Editor avanzado** o mediante programación, haga clic en uno de los temas siguientes:  
  
-   [Propiedades comunes](../Topic/Common%20Properties.md)  
  
-   [Propiedades personalizadas de archivo sin formato](../../integration-services/data-flow/raw-file-custom-properties.md)  
  
## Tareas relacionadas  
 Para más información sobre cómo establecer las propiedades del componente, vea [Establecer las propiedades de un componente de flujo de datos](../../integration-services/data-flow/set-the-properties-of-a-data-flow-component.md).  
  
## Contenido relacionado  
  
-   Entrada del blog [Raw Files Are Awesome](http://www.sqlservercentral.com/blogs/stratesql/archive/2011/1/1/31-days-of-ssis-_1320_-raw-files-are-awesome-_2800_1_2F00_31_2900_.aspx), en sqlservercentral.com  
  
## Vea también  
 [Destino de archivo sin formato](../../integration-services/data-flow/raw-file-destination.md)   
 [Flujo de datos](../../integration-services/data-flow/data-flow.md)  
  
  