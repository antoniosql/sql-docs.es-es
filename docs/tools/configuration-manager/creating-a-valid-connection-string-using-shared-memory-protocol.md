---
title: "Crear una cadena de conexi&#243;n v&#225;lida con el protocolo de memoria compartida | Microsoft Docs"
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
  - "cadenas de conexión [motor de base de datos], memoria compartida"
  - "alias [SQL Server], memoria compartida"
ms.assetid: 5fff42e8-377f-4b40-b0c8-b02393f8a1af
caps.latest.revision: 25
author: "BYHAM"
ms.author: "rickbyh"
manager: "jhubbard"
caps.handback.revision: 25
---
# Crear una cadena de conexi&#243;n v&#225;lida con el protocolo de memoria compartida
  Las conexiones a [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] desde un cliente que se ejecuta en el mismo equipo utilizan el protocolo de memoria compartida. La memoria compartida no tiene propiedades que se puedan configurar. Memoria compartida es el protocolo que se intenta utilizar en primer lugar y no se puede desplazar de la posición prioritaria de la lista **Protocolos habilitados** de la lista **Propiedades de los protocolos de cliente** . El protocolo de memoria compartida se puede deshabilitar, lo que resulta útil para solucionar problemas con los demás protocolos.  
  
 No es posible crear un alias con el protocolo de memoria compartida, pero si el protocolo está habilitado, al conectarse al [!INCLUDE[ssDE](../../includes/ssde-md.md)] por nombre se crea una conexión de memoria compartida. Una cadena de conexión de memoria compartida usa el formato `lpc:<servername>[\instancename]`.  
  
## Conectarse al servidor local  
 Al conectarse a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] cuando se ejecuta en el mismo equipo que el cliente, puede usar **(local)** como nombre de servidor. Esta posibilidad no se recomienda ya que genera ambigüedad, pero puede ser útil cuando se sabe que el cliente se ejecuta en el equipo de destino. Por ejemplo, al crear una aplicación para usuarios desconectados móviles, como puede ser el personal de ventas, en la que [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] se ejecutará en equipos portátiles y se almacenarán datos de proyectos, un cliente que se conecte a **(local)** siempre se conectará al servidor [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] que se ejecuta en el equipo portátil. En lugar de **(local)**, se puede usar la palabra **localhost** o un punto (**.**).  
  
## Comprobar el protocolo de conexión  
 La siguiente consulta devolverá el protocolo utilizado para la conexión actual.  
  
```  
SELECT net_transport   
FROM sys.dm_exec_connections   
WHERE session_id = @@SPID;  
  
```  
  
## Ejemplos:  
 Los siguientes nombres se conectarán al equipo local con el protocolo de memoria compartida si está habilitado:  
  
 `<servername>`  
  
 `<servername>\<instancename>`  
  
 `(local)`  
  
 `localhost`  
  
 No se puede crear un alias para una conexión de memoria compartida.  
  
> [!NOTE]  
>  Si se especifica una dirección IP en el cuadro **Servidor**, se establecerá una conexión TCP/IP.  
  
## Vea también  
 [Crear una cadena de conexión válida con TCP/IP](../../tools/configuration-manager/creating-a-valid-connection-string-using-tcp-ip.md)   
 [Crear una cadena de conexión válida con canalizaciones con nombre](../Topic/Creating%20a%20Valid%20Connection%20String%20Using%20Named%20Pipes.md)   
 [Elegir un protocolo de red](../Topic/Choosing%20a%20Network%20Protocol.md)  
  
  