---
title: "Acceso a datos para las operaciones de DQS | Microsoft Docs"
ms.custom: ""
ms.date: "03/01/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "data-quality-services"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 88dfb9ea-6321-4eaf-b9e4-45d36ef048f6
caps.latest.revision: 15
author: "JennieHubbard"
ms.author: "jhubbard"
manager: "jhubbard"
caps.handback.revision: 15
---
# Acceso a datos para las operaciones de DQS
  Para usar los datos de origen para las operaciones del [!INCLUDE[ssDQSnoversion](../../includes/ssdqsnoversion-md.md)] (DQS) y exportar los datos procesados, puede realizar una de las acciones siguientes:  
  
-   Copie los datos de origen en una tabla o una vista en la base de datos DQS_STAGING_DATA y utilícelos posteriormente en las operaciones de DQS. También puede exportar los datos procesados a una nueva tabla de la base de datos DQS_STAGING_DATA. Para ello, se debe conceder acceso de lectura y escritura a su cuenta de usuario de Windows en la base de datos DQS_STAGING_DATA.  
  
-   Use su propia base de datos como datos de origen para las operaciones de DQS y como destino para exportar los datos procesados. Para ello, asegúrese de que la base de datos está en la misma instancia de SQL Server que las bases de datos de Data Quality Server. De lo contrario, la base de datos no estará disponible en Data Quality Client para las operaciones de DQS. Además, se debe conceder acceso a la cuenta de usuario de Windows en la base de datos DQS_STAGING_DATA para exportar los resultados coincidentes, ya que estos se exportan en dos fases: primero, los resultados coincidentes se exportan a las tablas temporales de la base de datos DQS_STAGING_DATA y, después, se mueven a la tabla de la base de datos de destino.  
  
## Requisitos previos  
  
-   Debe haber completado la instalación del [!INCLUDE[ssDQSServer](../../includes/ssdqsserver-md.md)] ejecutando el archivo DQSInstaller.exe. Para obtener más información, vea [Ejecutar DQSInstaller.exe para completar la instalación del servidor de calidad de datos](../../data-quality-services/install-windows/run-dqsinstaller-exe-to-complete-data-quality-server-installation.md).  
  
-   La cuenta de usuario de Windows debe ser miembro del rol fijo de servidor apropiado (como securityadmin, serveradmin o sysadmin) en la instancia del motor de base de datos para conceder o modificar el acceso al inicio de sesión de SQL en las bases de datos.  
  
### Para conceder acceso de lectura y escritura a un usuario en la base de datos DQS_STAGING_DATA  
  
1.  Inicie Microsoft SQL Server Management Studio.  
  
2.  En Microsoft SQL Server Management Studio, expanda la instancia de SQL Server y, a continuación, expanda **Seguridad**e **Inicios de sesión**.  
  
3.  Haga clic con el botón derecho en el inicio de sesión de SQL y haga clic en **Propiedades**.  
  
4.  En el cuadro de diálogo **Propiedades de inicio de sesión** , haga clic en la página **Asignación de usuarios** en el panel izquierdo.  
  
5.  En el panel derecho, seleccione la casilla en la columna **Asignar** para la base de datos **DQS_STAGING_DATA** y, después, seleccione los siguientes roles en el panel **Pertenencia al rol de base de datos para: DQS_STAGING_DATA**:  
  
    -   **db_datareader**: leer datos de las tablas y de las vistas.  
  
    -   **db_datawriter**: agregar, eliminar o cambiar los datos de las tablas.  
  
    -   **db_ddladmin**: crear, modificar o eliminar las tablas o vistas.  
  
6.  En el cuadro de diálogo **Propiedades de inicio de sesión** , haga clic en **Aceptar** para aplicar los cambios.  
  
## Pasos siguientes  
 Intente realizar operaciones de DQS que obtengan acceso a la base de datos como origen de datos para la operación de DQS, y después exporte los datos procesados a la base de datos.  
  
## Vea también  
 [Instalar Data Quality Services](../../data-quality-services/install-windows/install-data-quality-services.md)  
  
  