---
title: "Propiedades de Protocolos de MSSQLSERVER (pesta&#241;a Marcas) | Microsoft Docs"
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
  - "MSSQLSERVER, propiedades de protocolos"
ms.assetid: 4d38e6e9-f95f-4e79-ae45-89f631037528
caps.latest.revision: 32
author: "BYHAM"
ms.author: "rickbyh"
manager: "jhubbard"
caps.handback.revision: 32
---
# Propiedades de Protocolos de MSSQLSERVER (pesta&#241;a Marcas)
  Al instalar un certificado en el servidor, use la pestaña **Marcas** del cuadro de diálogo **Propiedades de Protocolos de MSSQLSERVER** para ver o especificar las opciones de cifrado de protocolo y ocultar instancia. [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] se debe reiniciar **ForceEncryption** .  
  
 Para cifrar conexiones, debe proporcionar a [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] un certificado. Si no se instala ningún certificado, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] generará un certificado autofirmado al iniciar la instancia. Este certificado autofirmado se puede usar en lugar de un certificado de una entidad emisora de certificados de confianza, pero no proporciona la autenticación ni el no rechazo.  
  
> [!CAUTION]  
>  Las conexiones SSL (capa de sockets seguros) cifradas con un certificado autofirmado no proporcionan una seguridad elevada. Son susceptibles de ataques de tipo "Man-in-the-middle". No debe confiar en la SSL con certificados autofirmados en un entorno de producción ni en servidores conectados a Internet.  
  
 Para obtener más información sobre el cifrado, vea el tema sobre cómo cifrar conexiones en [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]en los Libros en pantalla de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .  
  
 El proceso de inicio de sesión siempre está cifrado. Si **ForceEncryption** se establece en **Yes**, se cifrarán todas las comunicaciones entre el cliente y el servidor, y los clientes que se conecten a [!INCLUDE[ssDE](../../includes/ssde-md.md)] necesitan estar configurados para confiar en la entidad de certificación raíz del certificado de servidor. Para más información, vea "Cómo habilitar conexiones cifradas en el motor de base de datos [!INCLUDE[ssDE](../../includes/ssde-md.md)] (Administrador de configuración de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)])" en los Libros en pantalla de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
## Servidores de clúster  
 Si desea utilizar el cifrado con clúster de conmutación por error, debe instalar el certificado del servidor con el nombre DNS completo del servidor virtual en todos los nodos del clúster de conmutación por error. Por ejemplo, si tiene un clúster de dos nodos cuyos nombres son "test1.*\<su compañía>*.com" y "test2.*\<su compañía>*.com" y un servidor virtual llamado "virtsql", tendrá que instalar un certificado para "virtsql.*\<su compañía>*.com" en los dos nodos. A continuación, puede activar la casilla **ForceEncryption** en el **Administrador de configuración de SQL Server** para configurar el cifrado del clúster de conmutación por error.  
  
## Opciones  
 **ForceEncryption**  
 Fuerce el cifrado de protocolos. El cifrado es un método para mantener la confidencialidad de la información reservada y consiste en alterar los datos para darles un formato ilegible. El cifrado asegura que los datos permanecen seguros, incluso si se ven los paquetes durante el proceso de transmisión. Para utilizar el enlace del canal, active **Forzar cifrado** en **Activado** y configure **Protección ampliada** en la pestaña **Opciones avanzadas** .  
  
 **HideInstance**  
 Permite impedir que el servicio [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Browser exponga esta instancia de [!INCLUDE[ssDE](../../includes/ssde-md.md)] a los equipos cliente que intenten buscarla con el botón **Examinar**. En el caso de instancias con nombre en el servidor, para conectar, las aplicaciones cliente deben especificar la información de extremo de protocolo. Por ejemplo, el número de puerto o el nombre de canalización con nombre, como **tcp:server,5000**. Para más información, consulte [Logging In to SQL Server](../../database-engine/configure-windows/logging-in-to-sql-server.md).  
  
 Para obtener más información, vea "Cómo habilitar conexiones cifradas en el motor de base de datos (Administrador de configuración de SQL Server)" en los Libros en pantalla.  
  
  