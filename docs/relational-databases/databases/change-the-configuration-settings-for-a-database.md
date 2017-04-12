---
title: "Cambiar los valores de configuraci&#243;n de una base de datos | Microsoft Docs"
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
  - "configuración de base de datos [SQL Server]"
  - "opciones de configuración [SQL Server], bases de datos"
  - "modificar valores de configuración de base de datos"
ms.assetid: c29c3385-5043-400f-bb4e-044a4c9a9a4b
caps.latest.revision: 29
author: "BYHAM"
ms.author: "rickbyh"
manager: "jhubbard"
caps.handback.revision: 29
---
# Cambiar los valores de configuraci&#243;n de una base de datos
  En este tema se describe cómo cambiar las opciones de nivel de base de datos en [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] mediante [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] o [!INCLUDE[tsql](../../includes/tsql-md.md)]. Las opciones son únicas para cada base de datos y no afectan a otras bases de datos.  
  
 **En este tema**  
  
-   **Antes de empezar:**  
  
     [Limitaciones y restricciones](#Restrictions)  
  
     [Seguridad](#Security)  
  
-   **Para cambiar la configuración de las opciones de una base de datos, use:**  
  
     [SQL Server Management Studio](#SSMSProcedure)  
  
     [Transact-SQL](#TsqlProcedure)  
  
##  <a name="BeforeYouBegin"></a> Antes de comenzar  
  
###  <a name="Restrictions"></a> Limitaciones y restricciones  
  
-   Solo el administrador del sistema o los propietarios de la base de datos, los miembros de los roles fijos de servidor **sysadmin** y **dbcreator** y de los roles fijos de base de datos **db_owner** pueden modificar estas opciones.  
  
###  <a name="Security"></a> Seguridad  
  
####  <a name="Permissions"></a> Permisos  
 Requiere el permiso ALTER en la base de datos.  
  
##  <a name="SSMSProcedure"></a> Usar SQL Server Management Studio  
  
#### Para cambiar la configuración de las opciones de una base de datos  
  
1.  En el Explorador de objetos, conéctese a una instancia del [!INCLUDE[ssDE](../../includes/ssde-md.md)], expanda el servidor, expanda **Bases de datos**, haga clic con el botón derecho en una base de datos y, después, haga clic en **Propiedades**.  
  
2.  En el cuadro de diálogo **Propiedades de la base de datos** , haga clic en **Opciones** para obtener acceso a la mayoría de los valores de configuración. Las configuraciones de archivo y grupo de archivos, la creación de reflejos y el trasvase de registros se encuentran en sus páginas correspondientes.  
  
##  <a name="TsqlProcedure"></a> Usar Transact-SQL  
  
#### Para cambiar la configuración de las opciones de una base de datos  
  
1.  Conéctese con el [!INCLUDE[ssDE](../../includes/ssde-md.md)].  
  
2.  En la barra Estándar, haga clic en **Nueva consulta**.  
  
3.  Copie y pegue el siguiente ejemplo en la ventana de consulta y haga clic en **Ejecutar**. En este ejemplo se establece el modelo de recuperación y las opciones de comprobación de páginas de datos para la base de datos de ejemplo [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)].  
  
 [!code-sql[DatabaseDDL#AlterDatabase7](../../relational-databases/databases/codesnippet/tsql/change-the-configuration_1.sql)]  
  
 Para ver más ejemplos, vea [ALTER DATABASE SET Options &#40;Transact-SQL&#41;](../Topic/ALTER%20DATABASE%20SET%20Options%20\(Transact-SQL\).md).  
  
## Vea también  
 [Nivel de compatibilidad de ALTER DATABASE &#40;Transact-SQL&#41;](../Topic/ALTER%20DATABASE%20Compatibility%20Level%20\(Transact-SQL\).md)   
 [Reflejo de la base de datos ALTER DATABASE &#40;Transact-SQL&#41;](../Topic/ALTER%20DATABASE%20Database%20Mirroring%20\(Transact-SQL\).md)   
 [ALTER DATABASE SET HADR &#40;Transact-SQL&#41;](../Topic/ALTER%20DATABASE%20SET%20HADR%20\(Transact-SQL\).md)   
 [Cambiar el nombre de una base de datos](../../relational-databases/databases/rename-a-database.md)   
 [Reducir una base de datos](../../relational-databases/databases/shrink-a-database.md)  
  
  