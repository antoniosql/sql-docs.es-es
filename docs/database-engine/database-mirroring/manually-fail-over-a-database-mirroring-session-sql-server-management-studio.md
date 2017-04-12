---
title: "Realizar manualmente la conmutaci&#243;n por error de una sesi&#243;n de creaci&#243;n de reflejo de la base de datos (SQL Server Management Studio) | Microsoft Docs"
ms.custom: ""
ms.date: "03/14/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dbe-high-availability"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "conmutación por error [SQL Server], creación de reflejo de la base de datos"
  - "conmutación por error manual [SQL Server]"
  - "creación de reflejo de la base de datos [SQL Server], conmutación por error"
ms.assetid: 4ecf9c63-b3a4-4c54-b553-5bc37973232b
caps.latest.revision: 32
author: "MikeRayMSFT"
ms.author: "mikeray"
manager: "jhubbard"
caps.handback.revision: 32
---
# Realizar manualmente la conmutaci&#243;n por error de una sesi&#243;n de creaci&#243;n de reflejo de la base de datos (SQL Server Management Studio)
  Cuando la base de datos reflejada se sincroniza (es decir, cuando el estado de la base de datos es SYNCHRONIZED), el propietario de la base de datos puede iniciar una conmutación por error manual en el servidor reflejado.  
  
 Durante una conmutación por error manual, los roles de servidor principal y reflejado se intercambian en la base de datos en la que se produce la conmutación por error. La base de datos reflejada se convierte en la base de datos principal, y la base de datos principal se convierte en la reflejada. Por ejemplo, en la siguiente tabla se muestra cómo una conmutación por error manual intercambia los roles de dos asociados de creación de reflejo: `SQLDBENGINE0_1` y `SQLDBENGINE0_2`.  
  
|Server|Antes de la conmutación por error|Después de la conmutación por error|  
|------------|---------------------|--------------------|  
|`SQLDBENGINE0_1`|PRINCIPAL|MIRROR|  
|`SQLDBENGINE0_2`|MIRROR|PRINCIPAL|  
  
 Observe que los roles de servidor de las demás sesiones de creación de reflejo de la base de datos no se ven afectados. Para obtener más información, vea [Conmutación de roles durante una sesión de creación de reflejo de la base de datos &#40;SQL Server&#41;](../../database-engine/database-mirroring/role-switching-during-a-database-mirroring-session-sql-server.md).  
  
### Para realizar manualmente una conmutación por error de la creación de reflejo de la base de datos  
  
1.  Conéctese a la instancia de servidor principal y, en el panel **Explorador de objetos** , haga clic en el nombre del servidor para expandir el árbol de servidores.  
  
2.  Expanda **Bases de datos**y seleccione la base de datos de la que se va a realizar la conmutación por error.  
  
3.  Haga clic con el botón derecho en la base de datos, seleccione **Tareas**y, luego, haga clic en**Reflejado**. Así se abre la página **Creación de reflejo** del cuadro de diálogo **Propiedades de la base de datos** .  
  
4.  Haga clic en **Conmutación por error**.  
  
     Aparece un cuadro de confirmación.  El servidor principal intenta conectarse al servidor reflejado mediante la Autenticación de Windows. Si la Autenticación de Windows no funciona, el servidor principal muestra el cuadro de diálogo **Conectar con el servidor** . Si el servidor reflejado usa la Autenticación de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , seleccione **Autenticación de SQL Server** en el cuadro **Autenticación** . En el cuadro de texto **Inicio de sesión** , especifique la cuenta de inicio de sesión para conectar con el servidor reflejado, y en el cuadro de texto **Contraseña** , especifique la contraseña correspondiente a la cuenta.  
  
     Si la conmutación por error se realiza correctamente, se cierra el cuadro de diálogo **Propiedades de la base de datos** . La base de datos reflejada se convierte en la base de datos principal, y la base de datos principal se convierte en la reflejada.  
  
     Si no se puede efectuar la conmutación por error, aparece un mensaje de error y el cuadro de diálogo permanece abierto.  
  
    > [!IMPORTANT]  
    >  Si ha modificado alguna propiedad desde que se abrió la página **Creación de reflejos**, estos cambios no se guardarán.  
  
     El cuadro de diálogo se cierra automáticamente.  
  
## Vea también  
 [Propiedades de la base de datos &#40;página Creación de reflejo&#41;](../../relational-databases/databases/database-properties-mirroring-page.md)   
 [Creación de reflejo de la base de datos &#40;SQL Server&#41;](../../database-engine/database-mirroring/database-mirroring-sql-server.md)   
 [Realizar una conmutación por error manualmente de una sesión de creación de reflejo de la base de datos &#40;Transact-SQL&#41;](../../database-engine/database-mirroring/manually-fail-over-a-database-mirroring-session-transact-sql.md)   
 [Pausar o reanudar una sesión de creación de reflejo de la base de datos &#40;SQL Server&#41;](../../database-engine/database-mirroring/pause-or-resume-a-database-mirroring-session-sql-server.md)   
 [Quitar la creación de reflejo de la base de datos &#40;SQL Server&#41;](../../database-engine/database-mirroring/remove-database-mirroring-sql-server.md)  
  
  