---
title: "Transformaci&#243;n Auditar | Microsoft Docs"
ms.custom: ""
ms.date: "03/14/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "integration-services"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "sql13.dts.designer.audittrans.f1"
helpviewer_keywords: 
  - "datos de entorno en paquetes [Integration Services]"
  - "Auditar, transformación"
ms.assetid: 8c143682-9c81-4150-83d6-1d9678151d37
caps.latest.revision: 46
author: "douglaslMS"
ms.author: "douglasl"
manager: "jhubbard"
caps.handback.revision: 46
---
# Transformaci&#243;n Auditar
  La transformación Auditar habilita el flujo de datos en un paquete para incluir datos sobre el entorno en el que se ejecuta el paquete. Por ejemplo, el nombre del paquete, el equipo y el operador se pueden agregar al flujo de datos. [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] incluye variables del sistema que proporcionan esta información.  
  
## Variables del sistema  
 En la tabla siguiente se describen las variables del sistema que la transformación Auditar puede usar.  
  
|Variable del sistema|Índice|Description|  
|---------------------|-----------|-----------------|  
|**ExecutionInstanceGUID**|0|El GUID que identifica la instancia de ejecución del paquete.|  
|**PackageID**|1|Identificador único del paquete.|  
|**PackageName**|2|Nombre del paquete.|  
|**VersionID**|3|La versión del paquete.|  
|**ExecutionStartTime**|4|La hora a la que se inició la ejecución del paquete.|  
|**MachineName**|5|El nombre del equipo.|  
|**UserName**|6|El nombre de inicio de sesión de la persona que inició el paquete.|  
|**TaskName**|7|El nombre de la tarea Flujos de datos a la que está asociada la transformación Auditar.|  
|**TaskId**|8|El identificador único de la tarea Flujo de datos.|  
  
## Configuración de la transformación Auditar  
 Para configurar la transformación Auditar debe proporcionar el nombre de una nueva columna de salida que se agregará a la salida de transformación y después asignar la variable del sistema a la columna de salida. Puede asignar una sola variable del sistema a varias columnas.  
  
 Esta transformación tiene una entrada y una salida. No admite una salida de error.  
  
 Puede establecer propiedades a través del Diseñador de [!INCLUDE[ssIS](../../../includes/ssis-md.md)] o mediante programación.  
  
 Para obtener más información acerca de las propiedades que puede establecer en el cuadro de diálogo **Editor de transformación Auditar** , vea [Audit Transformation Editor](../../../integration-services/data-flow/transformations/audit-transformation-editor.md).  
  
 El cuadro de diálogo **Editor avanzado** indica las propiedades que se pueden establecer mediante programación. Para obtener más información acerca de las propiedades que puede establecer a través del cuadro de diálogo **Editor avanzado** o mediante programación, haga clic en uno de los temas siguientes:  
  
-   [Propiedades comunes](../Topic/Common%20Properties.md)  
  
-   [Propiedades personalizadas de transformación](../../../integration-services/data-flow/transformations/transformation-custom-properties.md)  
  
 Para obtener más información sobre cómo establecer propiedades, vea [Establecer las propiedades de un componente de flujo de datos](../../../integration-services/data-flow/set-the-properties-of-a-data-flow-component.md).  
  
  