---
title: "Tarea Reducir base de datos | Microsoft Docs"
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
  - "sql13.dts.designer.shrinkdatabasetask.f1"
helpviewer_keywords: 
  - "Reducir base de datos, tarea"
  - "base de datos, reducción [Integration Services]"
  - "reducir bases de datos"
ms.assetid: e66286f8-97b1-4e5a-86b4-e56f1932b7d5
caps.latest.revision: 42
author: "douglaslMS"
ms.author: "douglasl"
manager: "jhubbard"
caps.handback.revision: 42
---
# Tarea Reducir base de datos
  La tarea Reducir base de datos reduce el tamaño de los datos y los archivos de registro de bases de datos de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .  
  
 Un paquete puede utilizar la tarea Reducir base de datos para reducir los archivos de una o varias bases de datos.  
  
 La reducción de los archivos de datos permite recuperar espacio moviendo páginas de datos del final del archivo a espacio desocupado próximo al principio del archivo. Cuando se crea suficiente espacio disponible al final del archivo, las páginas de datos situadas al final del mismo se pueden desasignar y devolver al sistema de archivos.  
  
> [!WARNING]  
>  Los datos que se mueven para reducir un archivo se pueden dispersar en cualquier ubicación disponible en el archivo. Esto produce la fragmentación de índices y puede reducir el rendimiento de las consultas que buscan un intervalo del índice. Para eliminar la fragmentación, considere la posibilidad de volver a generar los índices en el archivo después de la reducción.  
  
## Comandos  
 La tarea Reducir base de datos encapsula un comando DBCC SHRINKDATABASE, que incluye los siguientes argumentos y opciones:  
  
-   *database_name*  
  
-   *target_percent*  
  
-   NOTRUNCATE o TRUNCATEONLY.  
  
 Si la tarea Reducir base de datos reduce varias bases de datos, la tarea ejecuta varios comandos SHRINKDATABASE, uno para cada una de las bases de datos. Todas las instancias del comando SHRINKDATABASE usan los mismos valores para los argumentos, excepto para el argumento *database_name*. Para obtener más información, vea [DBCC SHRINKDATABASE &#40;Transact-SQL&#41;](../../t-sql/database-console-commands/dbcc-shrinkdatabase-transact-sql.md).  
  
## Configuración de la tarea Reducir base de datos  
 Puede establecer propiedades a través del Diseñador [!INCLUDE[ssIS](../../includes/ssis-md.md)] . Esta tarea se encuentra en la sección **Tareas del plan de mantenimiento** del **Cuadro de herramientas** , en el Diseñador [!INCLUDE[ssIS](../../includes/ssis-md.md)] .  
  
 Para obtener más información acerca de las propiedades que puede establecer en el Diseñador [!INCLUDE[ssIS](../../includes/ssis-md.md)] , haga clic en el tema siguiente:  
  
-   [Tarea Reducir base de datos &#40;Plan de mantenimiento&#41;](../../relational-databases/maintenance-plans/shrink-database-task-maintenance-plan.md)  
  
 Para obtener más información sobre cómo configurar estas propiedades en el Diseñador [!INCLUDE[ssIS](../../includes/ssis-md.md)] , haga clic en el tema siguiente:  
  
-   [Establecer las propiedades de tareas o contenedores](../Topic/Set%20the%20Properties%20of%20a%20Task%20or%20Container.md)  
  
  