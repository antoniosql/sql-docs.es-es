---
title: "Tarea Limpieza de historial | Microsoft Docs"
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
  - "sql13.dts.designer.historycleanuptask.f1"
helpviewer_keywords: 
  - "tablas de historial [SQL Server]"
  - "Limpieza de historial, tarea [Integration Services]"
ms.assetid: 5defc5b9-dfd3-4859-a7fe-ac8c2b5480f8
caps.latest.revision: 43
author: "douglaslMS"
ms.author: "douglasl"
manager: "jhubbard"
caps.handback.revision: 43
---
# Tarea Limpieza de historial
  La tarea Limpieza de historial elimina entradas de las siguientes tablas de historial de la base de datos msdb de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
-   backupfile  
  
-   backupfilegroup  
  
-   backupmediafamily  
  
-   backupmediaset  
  
-   backupset  
  
-   restorefile  
  
-   restorefilegroup  
  
-   restorehistory  
  
 Un paquete puede utilizar la tarea Limpieza del historial para eliminar datos históricos relacionados con las actividades de copias de seguridad y restauración, trabajos del Agente [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] y planes de mantenimiento de bases de datos.  
  
 Esta tarea encapsula el procedimiento almacenado del sistema sp_delete_backuphistory y pasa la fecha especificada al procedimiento como un argumento. Para más información, vea [sp_delete_backuphistory &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-delete-backuphistory-transact-sql.md).  
  
## Configuración de la tarea Limpieza de historial  
 La tarea incluye una propiedad para especificar la fecha más antigua de los datos almacenados en las tablas de historial. Puede indicar la fecha mediante el número de días, semanas, meses o años del día actual, y la tarea traducirá automáticamente el intervalo a una fecha.  
  
 Puede establecer propiedades a través del Diseñador [!INCLUDE[ssIS](../../includes/ssis-md.md)] . Esta tarea se encuentra en la sección **Tareas del plan de mantenimiento** del **Cuadro de herramientas** , en el Diseñador [!INCLUDE[ssIS](../../includes/ssis-md.md)] .  
  
 Para obtener más información acerca de las propiedades que puede establecer en el Diseñador [!INCLUDE[ssIS](../../includes/ssis-md.md)] , haga clic en el tema siguiente:  
  
-   [Tarea Limpieza de historial &#40;Plan de mantenimiento&#41;](../../relational-databases/maintenance-plans/history-cleanup-task-maintenance-plan.md)  
  
 Para obtener más información sobre cómo establecer estas propiedades en el Diseñador [!INCLUDE[ssIS](../../includes/ssis-md.md)] , haga clic en el siguiente tema:  
  
-   [Establecer las propiedades de tareas o contenedores](../Topic/Set%20the%20Properties%20of%20a%20Task%20or%20Container.md)  
  
## Vea también  
 [Tareas de Integration Services](../../integration-services/control-flow/integration-services-tasks.md)   
 [Flujo de control](../../integration-services/control-flow/control-flow.md)  
  
  