---
title: "Columna de evento de seguimiento ObjectType | Microsoft Docs"
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
  - "clases de eventos de SQL Server, valores de columna de Object Type"
  - "eventos [SQL Server], valores de columna de Object Type"
  - "clases de eventos [SQL Server], valores de columna de Object Type"
  - "Object Type, valores de la columna [SQL Server]"
ms.assetid: 42f85c50-34c9-49ca-955f-af9595e2707f
caps.latest.revision: 17
author: "JennieHubbard"
ms.author: "jhubbard"
manager: "jhubbard"
caps.handback.revision: 17
---
# Columna de evento de seguimiento ObjectType
  La columna de evento de seguimiento Object Type se utiliza en una variedad de eventos de seguimiento. En este tema se describen los valores posibles de esta columna y sus definiciones asociadas.  
  
## Valores de la columna Object Type  
  
|Valor|Definición|  
|-----------|----------------|  
|8259|Restricción CHECK|  
|8260|Valor predeterminado (restricción o independiente) |  
|8262|Restricción FOREIGN KEY|  
|8272|Procedimiento almacenado|  
|8274|Regla|  
|8275|Tabla del sistema|  
|8276|Desencadenador en servidor|  
|8277|Tabla (definida por el usuario)|  
|8278|Ver|  
|8280|Procedimiento almacenado extendido|  
|16724|Desencadenador CLR |  
|16964|Base de datos|  
|16975|Object|  
|17222|Catálogo de texto|  
|17232|Procedimiento almacenado de CLR|  
|17235|Esquema|  
|17475|Credencial|  
|17491|Evento de DDL |  
|17741|Evento de administración|  
|17747|Evento de seguridad|  
|17749|Evento de usuario|  
|17985|Función de agregado CLR|  
|17993|Función SQL con valores de tabla insertados|  
|18000|Función de partición|  
|18002|Procedimiento de filtro de replicación|  
|18004|Función SQL con valores de tabla|  
|18259|Rol del servidor|  
|18263|[!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows|  
|19265|Clave asimétrica|  
|19277|Clave maestra |  
|19280|Clave principal|  
|19283|ObfusKey |  
|19521|Inicio de sesión de clave asimétrica |  
|19523|Inicio de sesión de certificado|  
|19538|Rol|  
|19539|Inicio de sesión de SQL |  
|19543|Inicio de sesión de Windows|  
|20034|Enlace de servicio remoto|  
|20036|Notificación de evento en base de datos|  
|20037|Notificación de evento|  
|20038|Función SQL escalar |  
|20047|Notificación de evento en objeto|  
|20051|Synonym (Sinónimo)|  
|20307|Secuencia|  
|20549|Extremo|  
|20801|Consultas ad hoc que pueden almacenarse en la memoria caché|  
|20816|Consultas preparadas que pueden almacenarse en la caché|  
|20819|Cola de servicio de Service Broker|  
|20821|Restricción única|  
|21057|Rol de aplicación|  
|21059|Certificado|  
|21075|Server|  
|21076|Desencadenador de Transact-SQL|  
|21313|Ensamblado|  
|21318|Función escalar de CLR|  
|21321|Función escalar SQL insertada|  
|21328|Esquema de partición|  
|21333|Usuario|  
|21571|Contrato de servicio de Service Broker|  
|21572|Desencadenador en base de datos|  
|21574|Función con valores de tabla CLR|  
|21577|Tabla interna (por ejemplo, tabla de nodos XML, tabla de cola)|  
|21581|Tipo de mensaje de Service Broker|  
|21586|Ruta de Service Broker|  
|21587|Estadísticas|  
|21825<br /><br /> 21827<br /><br /> 21831<br /><br /> 21843<br /><br /> 21847|Usuario|  
|22099|Servicio de Service Broker|  
|22601|Índice|  
|22604|Inicio de sesión de certificado|  
|22611|XMLSchema|  
|22868|Tipo|  
  
## Vea también  
 [sp_trace_setevent &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-trace-setevent-transact-sql.md)  
  
  