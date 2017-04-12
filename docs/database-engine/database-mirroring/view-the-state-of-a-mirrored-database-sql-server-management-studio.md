---
title: "Ver el estado de una base de datos reflejada (SQL Server Management Studio) | Microsoft Docs"
ms.custom: ""
ms.date: "03/01/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dbe-high-availability"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "estados [SQL Server], creación de reflejo de la base de datos"
  - "creación de reflejo de la base de datos (SQL Server), estados"
ms.assetid: 544f4194-253e-4c57-96ca-31c16301434f
caps.latest.revision: 25
author: "MikeRayMSFT"
ms.author: "mikeray"
manager: "jhubbard"
caps.handback.revision: 25
---
# Ver el estado de una base de datos reflejada (SQL Server Management Studio)
  Durante una sesión de creación de reflejo de la base de datos, puede ver el estado en la página **Creación de reflejos** del cuadro de diálogo **Propiedades de la base de datos** .  
  
### Para ver el estado de una sesión de creación de reflejo de la base de datos  
  
1.  Después de conectarse a la instancia del servidor principal, en el Explorador de objetos, haga clic en el nombre del servidor para expandir el árbol del servidor.  
  
2.  Expanda **Bases de datos**y seleccione la base de datos que se va a reflejar.  
  
3.  Haga clic con el botón derecho en la base de datos, seleccione **Tareas**y, luego, haga clic en**Reflejado**. Así se abre la página **Creación de reflejo** del cuadro de diálogo **Propiedades de la base de datos** .  
  
4.  Una vez que se inicie la creación de reflejo, en el panel **Estado** se muestra el estado de la sesión de creación de reflejo de la base de datos a partir del momento en que seleccionó la página **Creación de reflejos** o hizo clic en el botón **Actualizar** . Los posibles estados son los siguientes:  
  
    |Estados|Explicación|  
    |------------|-----------------|  
    |\<en blanco>|No existe ninguna sesión de creación de reflejo de la base de datos y no hay actividad de la que informar en la página **Creación de reflejo** .|  
    |En pausa|La base de datos principal está en ejecución pero no envía ningún registro al servidor reflejado. La copia reflejada de la base de datos no está disponible.|  
    |Sin conexión|La instancia de servidor principal no puede conectar con su asociado o con la instancia de servidor testigo (si la hay) |  
    |Sincronizando|El contenido de la base de datos reflejada va por detrás del contenido de la base de datos principal. La instancia de servidor principal envía las entradas de registro a la instancia del servidor reflejado, que aplica los cambios en la base de datos reflejada para confirmarla.<br /><br /> Al inicio de una sesión de creación de reflejo de la base de datos, las bases de datos reflejada y principal se encuentran en el estado de sincronización.|  
    |Conmutación por error|En la instancia de servidor principal se ha iniciado una conmutación por error manual (intercambio de roles) pero el servidor reflejado todavía no la ha aceptado.|  
    |Sincronizado|La base de datos reflejada contiene los mismos datos que la base de datos principal. La conmutación por error manual y automática es posible *solo* en el estado sincronizado.|  
  
## Vea también  
 [Estados de creación de reflejo &#40;SQL Server&#41;](../../database-engine/database-mirroring/mirroring-states-sql-server.md)  
  
  