---
title: "Supervisar el rendimiento del servidor de informes | Microsoft Docs"
ms.custom: ""
ms.date: "03/14/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "reporting-services-sharepoint"
  - "reporting-services-native"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "contadores de rendimiento [Reporting Services]"
  - "servidores de informes [Reporting Services], rendimiento"
  - "contadores [Reporting Services]"
  - "supervisar el rendimiento [Reporting Services]"
  - "SQL Server Reporting Services, rendimiento"
  - "rendimiento [Reporting Services]"
  - "Reporting Services, rendimiento"
ms.assetid: c1bc13d4-8297-4daf-bb19-4c1e5ba292a6
caps.latest.revision: 64
author: "guyinacube"
ms.author: "asaxton"
manager: "erikre"
caps.handback.revision: 64
---
# Supervisar el rendimiento del servidor de informes
  Utilice las herramientas de supervisión del rendimiento para supervisar el rendimiento del servidor de informes a fin de evaluar la actividad del servidor, observar tendencias, diagnosticar cuellos de botella del sistema y recopilar datos que pueden ayudar a determinar si la configuración actual del sistema es suficiente. Para optimizar el rendimiento del servidor, puede especificar la frecuencia con que se recicla el dominio de aplicación del servidor de informes. Para obtener más información, vea [Configurar la memoria disponible para las aplicaciones del servidor de informes](../../reporting-services/report-server/configure-available-memory-for-report-server-applications.md).  
  
## Orígenes de datos de rendimiento  
 Utilice una combinación de tecnología y herramientas para obtener información completa sobre el rendimiento del sistema. [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows Server proporcionan información de rendimiento mediante las siguientes herramientas:  
  
-   Administrador de tareas  
  
-   Visor de eventos  
  
-   Consola Rendimiento  
  
 El Administrador de tareas brinda información sobre los programas y los procesos que se ejecutan en el equipo. Puede utilizar el Administrador de tareas para supervisar indicadores clave del rendimiento del servidor de informes. También puede evaluar la actividad de ejecutar procesos y visualizar gráficos y datos con relación al uso de la CPU y de la memoria. Para obtener información sobre cómo utilizar el Administrador de tareas, vea la documentación del producto de [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows.  
  
 Puede utilizar la consola Rendimiento y el Visor de eventos para crear registros y alertas sobre el procesamiento de informes y la utilización de recursos. Para obtener información sobre los eventos de Windows generados por [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)], vea [Registro de aplicación Windows](../../reporting-services/report-server/windows-application-log.md). Para obtener información sobre la consola Rendimiento, vea "Contadores de rendimiento de Windows" más adelante en este tema.  
  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] también proporcionan información acerca de la base de datos del servidor de informes y las bases de datos temporales que se usan para la administración de sesiones y el almacenamiento en caché.  
  
## Contadores de rendimiento de Windows  
 La supervisión de determinados contadores de rendimiento permite:  
  
-   Calcular los requisitos del sistema necesarios para admitir una carga de trabajo prevista.  
  
-   Crear una línea base de rendimiento para medir el efecto de los cambios de configuración o las actualizaciones de aplicaciones.  
  
-   Supervisar el rendimiento de la aplicación en determinadas cargas, independientemente de que éstas se hayan generado de forma real o artificial.  
  
-   Comprobar que las actualizaciones de hardware producen el efecto deseado en el rendimiento.  
  
-   Validar que los cambios realizados en la configuración del sistema producen el efecto deseado en el rendimiento.  
  
## Objetos de rendimiento en Reporting Services  
 [!INCLUDE[ssRSCurrent](../../includes/ssrscurrent-md.md)] incluye los objetos de rendimiento siguientes:  
  
-   **MSRS 2011 Web Service** y **MSRS 2011 SharePoint Mode Web Service** para supervisar el rendimiento del servidor de informes. Estos objetos de rendimiento incluyen una colección de contadores que se usan para realizar el seguimiento del procesamiento del servidor de informes que se suele iniciar mediante operaciones interactivas de visualización de informes. Estos contadores se restablecen siempre que [!INCLUDE[vstecasp](../../includes/vstecasp-md.md)] detiene el servicio web del servidor de informes.  
  
-   **MSRS 2011 Windows Service** y **MSRS 2011 Windows Service SharePoint Mode** para supervisar las operaciones programadas y la entrega de informes. Estos objetos de rendimiento incluyen una colección de contadores que se usan para realizar el seguimiento del procesamiento de informes que se inicia mediante operaciones programadas. Entre las operaciones programadas se incluyen la suscripción y la entrega, las instantáneas de ejecución de informes y el historial del informe.  
  
-   **ReportServer:Service** y **ReportServerSharePoint:Service** para supervisar los eventos relacionados con HTTP y la administración de memoria. Estos contadores son específicos de [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] y realizan el seguimiento de los eventos relacionados con HTTP para el servidor de informes, como solicitudes, conexiones e intentos de inicio de sesión. Este objeto de rendimiento también incluye contadores relacionados con la administración de memoria.  
  
 Si tiene varias instancias de servidor de informes en un solo equipo, puede supervisarlas conjuntamente o por separado. Elija las instancias que desea incluir al agregar un contador. Para obtener más información sobre cómo usar la Consola de rendimiento (perfmon.msc) y agregar contadores, vea la documentación del producto de [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows.  
  
## Otros contadores de rendimiento  
 Los contadores de rendimiento personalizados de [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] se proporcionan solo para el **Servicio web de MSRS 2008**, el **Servicio Windows de MSRS 2008** y **ReportServer:Service**. Los objetos de rendimiento siguientes proporcionan datos adicionales de supervisión de rendimiento para el servidor de informes.  
  
|Objeto de rendimiento|Notas|  
|------------------------|-----------|  
|**.NET CLR Data** y **.NET CLR Memory**|El Administrador de informes utiliza los contadores de rendimiento de [!INCLUDE[vstecasp](../../includes/vstecasp-md.md)] . Para obtener más información, vea la página sobre cómo mejorar el rendimiento y la escalabilidad de aplicaciones de .NET en MSDN.|  
|**Procesar**|Agregue los contadores de rendimiento **Elapsed Time** y **ID Process** para que una instancia de ReportingServicesService realice el seguimiento del tiempo de funcionamiento de un proceso mediante el identificador del proceso.|  
  
## Eventos de SharePoint  
 Además de los objetos de rendimiento de [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] , también puede configurar eventos de SharePoint si está ejecutando un servidor de informes en modo integrado de SharePoint y ha configurado el entorno de informes para utilizar un producto de SharePoint. En esta sección, utilice Eventos para un servidor de informes en modo integrado de SharePoint para revisar los eventos de diagnóstico que pueden proporcionar información útil si el entorno de informes está integrado en SharePoint.  
  
## En esta sección  
 [Contadores de rendimiento para los objetos de rendimiento de MSRS 2011 Web Service y MSRS 2011 Windows Service &#40;modo nativo&#41;](../../reporting-services/report-server/performance counters msrs 2011 web service, performance objects.md)  
 Describe los contadores de rendimiento que utiliza el servicio web del servidor de informes.  
  
 [Contadores de rendimiento para los objetos de rendimiento en modo SharePoint de MSRS 2011 Web Service y SharePoint de MSRS 2011 Windows Service &#40;modo SharePoint&#41;](../../reporting-services/report-server/performance counters msrs 2011 sharepoint mode performance objects.md)  
 Describe los contadores de rendimiento que utiliza el servicio de Windows del servidor de informes.  
  
 [Contadores de rendimiento de los objetos ReportServer:Service y ReportServerSharePoint:Service](../../reporting-services/report-server/performance counters - reportserver service, performance objects.md)  
 Describe los contadores de rendimiento de eventos relacionados con HTTP y la administración de memoria en [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)].  
  
 Eventos para un servidor de informes en modo integrado de SharePoint  
 Describe los útiles eventos de diagnóstico que se registran cuando se ejecuta un entorno de informes con un producto de SharePoint.  
  
## Vea también  
 [Configurar la memoria disponible para las aplicaciones del servidor de informes](../../reporting-services/report-server/configure-available-memory-for-report-server-applications.md)   
 [Servidor de informes de Reporting Services &#40;modo nativo&#41;](../../reporting-services/report-server/reporting-services-report-server-native-mode.md)   
 [Herramientas de Reporting Services](../../reporting-services/tools/reporting-services-tools.md)  
  
  