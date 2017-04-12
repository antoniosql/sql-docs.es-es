---
title: "Importar informaci&#243;n de servidores registrados (SQL Server Management Studio) | Microsoft Docs"
ms.custom: ""
ms.date: "03/14/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "database-engine"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "sql13.swb.importregisteredservers.f1"
helpviewer_keywords: 
  - "transferir información de servidores registrados"
  - "servidores registrados [SQL Server], importar"
  - "importar información de servidores registrados"
ms.assetid: cc497a14-1360-4887-b70c-002f042823b6
caps.latest.revision: 28
author: "JennieHubbard"
ms.author: "jhubbard"
manager: "jhubbard"
caps.handback.revision: 28
---
# Importar informaci&#243;n de servidores registrados (SQL Server Management Studio)
  En este tema se describe cómo importar información guardada de servidores registrados en [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]. La exportación e importación de archivos de un servidor registrado permite configurar fácilmente varios equipos con los mismos servidores en Servidores registrados. Esto resulta útil cuando se administra un gran número de servidores desde equipos en distintas ubicaciones, o cuando desea establecer la configuración de conexión básica para un usuario menos experimentado.  
  
> [!NOTE]  
>  No puede importar información de servidores registrados en [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] desde versiones anteriores de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
##  <a name="SSMSProcedure"></a>  
  
#### Para importar información de servidores registrados  
  
1.  En Servidores registrados, haga clic en el tipo de servidor en la barra de herramientas Servidores registrados. El tipo de servidor debe ser el mismo que el tipo de archivo de exportación de servidores registrados. Por ejemplo, si ha exportado la información de un servidor registrado de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , debe hacer clic en **SQL Server** en la barra de herramientas Servidores registrados.  
  
2.  Haga clic con el botón derecho en un grupo de servidores y seleccione **Importar**.  
  
3.  En el cuadro de diálogo **Importar servidores registrados** , seleccione el archivo de servidores registrados que desea importar y, a continuación, haga clic en **Aceptar**.  
  
     **Importar archivo**  
     Escriba el nombre del archivo de importación en el cuadro de texto o haga clic en el botón Explorar (**...**) para localizar el archivo en el equipo cliente. Si selecciona un archivo existente, la información del servidor registrado se anexa al archivo. El archivo de importación solo puede ser un archivo de servidor registrado exportado previamente. Los archivos de servidor registrado tienen una extensión .regsrvr.  
  
     **Seleccionar el grupo de servidores de destino de la importación**  
     Seleccione el nodo raíz o un grupo de servidores específico al que se importarán las entradas del servidor registrado del archivo. Puede importar al archivo de exportación todos los servidores registrados, los servidores registrados de un grupo de servidores específico o un único servidor registrado. La funcionalidad de importación es recursiva; por ejemplo, si un grupo de servidores A contiene un grupo de servidores B, y un grupo de servidores B contiene grupos de servidores C y D; la importación del grupo de servidores A exporta todas las entradas de A, B, C y D.  
  
     El grupo de servidores muestra solo los grupos del actual árbol de servidores registrados.  
  
     Si selecciona un grupo de servidores o un servidor para la importación, un mensaje confirmará que desea sobrescribir el grupo de servidores o el servidor existente.  
  
 Los registros de servidor que usan la autenticación de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] almacenan las contraseñas por usuario. Después de importar los registros de servidor, los usuarios deben escribir la contraseña para cada servidor la primera vez que se conectan, y almacenar así las contraseñas en las listas de los servidores registrados. Esto no es necesario en los servidores registrados mediante la autenticación de Windows.  
  
## Vea también  
 [Cambiar el registro de un servidor &#40;SQL Server Management Studio&#41;](../../tools/sql-server-management-studio/change-a-server-s-registration-sql-server-management-studio.md)   
 [Exportar información de servidores registrados &#40;SQL Server Management Studio&#41;](../../tools/sql-server-management-studio/export-registered-server-information-sql-server-management-studio.md)   
 [Crear un servidor registrado &#40;SQL Server Management Studio&#41;](../../tools/sql-server-management-studio/create-a-new-registered-server-sql-server-management-studio.md)  
  
  