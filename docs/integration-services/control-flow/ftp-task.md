---
title: "Tarea FTP | Microsoft Docs"
ms.custom: ""
ms.date: "03/01/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "integration-services"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "sql13.dts.designer.ftptask.f1"
helpviewer_keywords: 
  - "FTP, tarea [Integration Services]"
ms.assetid: 41c3f2c4-ee04-460a-9822-bb9ae4036c2e
caps.latest.revision: 52
author: "douglaslMS"
ms.author: "douglasl"
manager: "jhubbard"
caps.handback.revision: 52
---
# Tarea FTP
  La tarea FTP descarga y carga archivos de datos, y administra directorios en servidores. Por ejemplo, un paquete puede descargar archivos de datos de un servidor remoto o de una ubicación de Internet como parte de un flujo de trabajo de paquete de [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] . Puede usar la tarea FTP para los siguientes fines:  
  
-   Copiar directorios y archivos de datos de un directorio a otro, antes o después de mover datos, y aplicar transformaciones a los datos.  
  
-   Iniciar una sesión en una ubicación FTP de origen y copiar archivos o paquetes en un directorio de destino.  
  
-   Descargar archivos desde una ubicación FTP y aplicar transformaciones a datos de la columna antes de cargar datos en una base de datos.  
  
 En tiempo de ejecución, la tarea FTP se conecta con un servidor mediante un administrador de conexiones FTP. El administrador de conexiones FTP se configura por separado de la tarea FTP y después se hace referencia al mismo en la tarea FTP. Dicho administrador incluye la configuración del servidor, las credenciales de acceso al servidor FTP y opciones como el tiempo de espera y el número de reintentos de conexión con el servidor. Para obtener más información, vea [Administrador de conexiones FTP](../../integration-services/connection-manager/ftp-connection-manager.md).  
  
> [!IMPORTANT]  
>  El administrador de conexiones FTP solo admite la autenticación anónima y la autenticación básica. No es compatible con la autenticación de Windows.  
  
 Al tener acceso a un archivo local o un directorio local, la tarea FTP utiliza un administrador de conexiones de archivos o información de ruta de acceso almacenada en una variable. En contraste, al tener acceso a un archivo remoto o un directorio remoto, la tarea FTP utiliza una ruta especificada directamente en el servidor remoto, como se especifica en el administrador de conexiones FTP, o información de ruta almacenada en una variable. Para obtener más información, vea [Administrador de conexiones de archivos](../../integration-services/connection-manager/file-connection-manager.md) e [Variables de Integration Services &#40;SSIS&#41;](../../integration-services/integration-services-ssis-variables.md).  
  
 Esto significa que la tarea FTP puede recibir varios archivos y eliminar varios archivos remotos, pero si utiliza un administrador de conexiones, solo puede enviar un archivo y eliminar únicamente un archivo local, porque un administrador de conexiones de archivos solo puede tener acceso a un único archivo. Para tener acceso a varios archivos locales, la tarea FTP debe utilizar una variable para proporcionar la información de ruta. Por ejemplo, una variable que contiene "C:\Prueba\\*.txt" proporciona una ruta que permite eliminar o enviar todos los archivos del directorio Prueba que tienen una extensión .txt.  
  
 Para enviar varios archivos y tener acceso a varios archivos y directorios locales, también puede ejecutar la tarea FTP varias veces incluyéndola en un contenedor de bucles Foreach. El contenedor de bucles Foreach puede recorrer los archivos de un directorio mediante el enumerador Foreach File. Para más información, consulte [Foreach Loop Container](../../integration-services/control-flow/foreach-loop-container.md).  
  
 La tarea FTP admite los caracteres comodín *?* y *\** en las rutas. Esto permite que la tarea tenga acceso a varios archivos. Sin embargo, solo puede usar caracteres comodín en la parte de la ruta de acceso que especifica el nombre de archivo. Por ejemplo, C:\MiDirectorio\\*.txt es una ruta válida, pero C:\\\**\MiTexto.txt no.  
  
 Es posible configurar las operaciones de FTP para detener la tarea Sistema de archivos cuando la operación no se realice correctamente o para transferir archivos en modo ASCII. Las operaciones que envían y reciben archivos pueden configurarse para sobrescribir los archivos y directorios de destino.  
  
## Operaciones FTP predefinidas  
 La tarea FTP incluye un conjunto predefinido de operaciones. Estas operaciones se describen en la siguiente tabla.  
  
|Operación|Description|  
|---------------|-----------------|  
|Enviar archivos|Envía un archivo desde el equipo local al servidor FTP.|  
|Recibir archivos|Guarda un archivo del servidor FTP en el equipo local.|  
|Crear directorio local|Crea una carpeta en el equipo local.|  
|Crear directorio remoto|Crea una carpeta en el servidor FTP.|  
|Quitar directorio local|Elimina una carpeta del equipo local.|  
|Quitar directorio remoto|Elimina una carpeta del servidor FTP.|  
|Eliminar archivos locales|Elimina un archivo del equipo local.|  
|Eliminar archivos remotos|Elimina un archivo del servidor FTP.|  
  
## Entradas del registro personalizadas disponibles en la tarea FTP  
 La siguiente tabla contiene las entradas del registro personalizadas para la tarea FTP. Para obtener más información, vea [Registro de Integration Services &#40;SSIS&#41;](../../integration-services/performance/integration-services-ssis-logging.md) y [Mensajes personalizados para registro](../../integration-services/performance/custom-messages-for-logging.md).  
  
|Entrada del registro|Description|  
|---------------|-----------------|  
|**FTPConnectingToServer**|Indica que la tarea inició una conexión con el servidor FTP.|  
|**FTPOperation**|Informa del comienzo y del tipo de operación de FTP que realiza la tarea.|  
  
## Tareas relacionadas  
 Puede establecer propiedades a través del Diseñador de [!INCLUDE[ssIS](../../includes/ssis-md.md)] o mediante programación.  
  
 Para obtener información sobre cómo establecer estas propiedades en el Diseñador de [!INCLUDE[ssIS](../../includes/ssis-md.md)], vea [Establecer las propiedades de tareas o contenedores](../Topic/Set%20the%20Properties%20of%20a%20Task%20or%20Container.md).  
  
 Para obtener más información sobre la configuración mediante programación de estas propiedades, vea <xref:Microsoft.SqlServer.Dts.Tasks.FtpTask.FtpTask>.  
  
## Vea también  
 [Editor de la tarea FTP &#40;página General&#41;](../../integration-services/control-flow/ftp-task-editor-general-page.md)   
 [Editor de la tarea FTP &#40;página Transferencia de archivos&#41;](../../integration-services/control-flow/ftp-task-editor-file-transfer-page.md)   
 [Tareas de Integration Services](../../integration-services/control-flow/integration-services-tasks.md)   
 [Flujo de control](../../integration-services/control-flow/control-flow.md)  
  
  