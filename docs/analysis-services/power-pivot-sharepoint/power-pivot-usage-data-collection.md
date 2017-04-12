---
title: "Recopilaci&#243;n de datos de uso de Power Pivot | Microsoft Docs"
ms.custom: ""
ms.date: "03/14/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "analysis-services"
  - "analysis-services/multidimensional-tabular"
  - "analysis-services/data-mining"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 9057cb89-fb17-466e-a1ce-192c8ca20692
caps.latest.revision: 10
author: "Minewiskan"
ms.author: "owend"
manager: "erikre"
caps.handback.revision: 8
---
# Recopilaci&#243;n de datos de uso de Power Pivot
  La recopilación de datos de uso es una característica propia de SharePoint para las granjas. [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] para SharePoint usa y extiende este sistema para proporcionar informes en el panel de administración de [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] que muestran cómo se usan los datos y servicios de [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] . Según cómo haya instalado SharePoint, la recopilación de datos de uso podría estar desactivada para la granja. El administrador de una granja debe habilitar el registro de uso para crear los datos de uso que aparecen en el panel de administración de [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] . Para obtener más información sobre cómo habilitar y configurar la recopilación de datos de uso para los eventos de [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)], vea [Configurar la recolección de datos de uso para Power Pivot para SharePoint](../../analysis-services/power-pivot-sharepoint/configure-usage-data-collection-for-power-pivot-for-sharepoint.md).  
  
 Para obtener información sobre los datos de uso en el Panel de administración de [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)], vea [Panel de administración de Power Pivot y datos de uso](../../analysis-services/power-pivot-sharepoint/power-pivot-management-dashboard-and-usage-data.md).  
  
 **En este tema:**  
  
 [Recopilación de datos de uso y arquitectura de los informes](#usagearch)  
  
 [Orígenes de datos de uso](#sources)  
  
 [Servicios y trabajos del temporizador](#servicesjobs)  
  
 [Informes sobre los datos de uso](#reporting)  
  
##  <a name="usagearch"></a> Recopilación de datos de uso y arquitectura de los informes  
 [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] se recopilan, almacenan y administran mediante una combinación de características de la infraestructura de SharePoint y de componentes de servidor de [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] . La infraestructura de SharePoint proporciona un servicio de uso centralizado y trabajos del temporizador integrados. [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] para SharePoint agrega un almacenamiento a mayor plazo para los datos de uso y los informes de [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] que se ven en la Administración central de SharePoint.  
  
 En el sistema de recopilación de datos de uso, la información de los eventos se introduce en el sistema de recopilación de datos de uso en el servidor de aplicaciones o front-end web. Los datos de uso se mueven a través del sistema como respuesta a los trabajos del temporizador que hacen que los datos se pasen de los archivos de datos temporales del servidor físico a un almacenamiento persistente en un servidor de bases de datos. El siguiente diagrama muestra los componentes y procesos que mueven los datos de uso a través del sistema de informes y recopilación de datos.  
  
 **Nota** : compruebe que la recopilación de datos de uso esté habilitada. Para ello, vaya a **Supervisión** en Administración central de SharePoint. Para obtener más información, vea [Configurar la recolección de datos de uso para Power Pivot para SharePoint](../../analysis-services/power-pivot-sharepoint/configure-usage-data-collection-for-power-pivot-for-sharepoint.md).  
  
 ![Componentes y procesos de la recopilación de datos de uso.](../../analysis-services/power-pivot-sharepoint/media/gmni-usagedata.gif "Componentes y procesos de la recopilación de datos de uso.")  
  
|Fase|Description|  
|-----------|-----------------|  
|1|La recopilación de datos de uso se desencadena mediante eventos generados por los componentes de [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] y los proveedores de [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] en las implementaciones de SharePoint. Entre los eventos configurables que se pueden activar o desactivar se encuentran las solicitudes de conexión, las solicitudes de carga y descarga y los eventos de sincronización en respuesta a las consultas que el servicio de [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] supervisa en el servidor de aplicaciones. Otros eventos son administrados solamente por el servidor y no se pueden desactivar. Por ejemplo, los de actualización de datos y los de estado del servidor.<br /><br /> Inicialmente, los datos de uso se recopilan y almacenan en archivos de registro locales mediante las características de recopilación de datos del sistema de SharePoint. Los archivos y su ubicación forman parte del sistema de recopilación de datos de uso estándar de SharePoint. La ubicación de los archivos es la misma en todos los servidores de la granja. Para ver o cambiar la ubicación del directorio de registro, vaya a **Supervisión** en Administración central de SharePoint y, a continuación, haga clic en **Configurar la recolección de datos de uso y estado**.|  
|2|En los intervalos programados (cada hora de forma predeterminada), el trabajo de temporizador Importación de datos de uso de Microsoft SharePoint Foundation mueve los datos de uso de los archivos locales a la base de datos de la aplicación de servicio de [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)]. Si tiene varias aplicaciones de servicio de [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] en una granja, cada una tendrá su propia base de datos. Los eventos incluyen información interna que identifica qué aplicación de servicio de [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] generó el evento. Los identificadores de la aplicación se aseguran de que los datos de uso se enlazan a la aplicación que los creó.|  
|3|Los datos se copian en una base de datos de informes interna que está disponible para el panel de administración de [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] en Administración central.|  
|4|El origen de datos es un libro de [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] al que puede tener acceso para crear informes personalizados en Excel. Solo hay una instancia del libro de origen. Todos los informes traducidos se basan en el mismo libro de origen.|  
|5|Los datos de uso se presentan en informes para los administradores de las aplicaciones de servicio de [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] que administran el rendimiento y la disponibilidad de los servidores. Se crean instancias localizadas de los libros para los idiomas admitidos de SharePoint.<br /><br /> Para obtener más información, vea [Informes sobre los datos de uso](#reporting) en este tema.|  
  
##  <a name="sources"></a> Orígenes de datos de uso  
 Cuando la recopilación de datos de uso está habilitada, se generan datos para los siguientes eventos de servidor.  
  
|Evento|Description|Configurable|  
|-----------|-----------------|------------------|  
|Conexiones|Conexiones de servidor realizadas en nombre de un usuario que consulta los datos de [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] en un libro de Excel. Los eventos de conexión identifican quién abrió una conexión a un libro de [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] . En los informes, esta información se usa para identificar a los usuarios más frecuentes, los orígenes de datos de [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] a los que tienen acceso los mismos usuarios y las tendencias en las conexiones a lo largo del tiempo.|Puede habilitar y deshabilitar [Configurar la recolección de datos de uso para Power Pivot para SharePoint](../../analysis-services/power-pivot-sharepoint/configure-usage-data-collection-for-power-pivot-for-sharepoint.md).|  
|Consulta de los tiempos de respuesta|Estadísticas de respuesta de las consultas que clasifican las consultas en función de cuánto tiempo tardan en completarse. Las estadísticas de respuestas de las consultan muestran patrones sobre cuánto tiempo tarda el servidor en responder a las solicitudes de consultas.|Puede habilitar y deshabilitar [Configurar la recolección de datos de uso para Power Pivot para SharePoint](../../analysis-services/power-pivot-sharepoint/configure-usage-data-collection-for-power-pivot-for-sharepoint.md).|  
|Carga de datos|Las operaciones de carga de datos del [!INCLUDE[ssGeminiSrv](../../includes/ssgeminisrv-md.md)]. Los eventos de carga de datos identifican qué orígenes de datos se usan con mayor frecuencia.|Puede habilitar y deshabilitar [Configurar la recolección de datos de uso para Power Pivot para SharePoint](../../analysis-services/power-pivot-sharepoint/configure-usage-data-collection-for-power-pivot-for-sharepoint.md).|  
|Descarga de datos|Operaciones de descarga de datos de las aplicaciones de servicio de [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] . Un [!INCLUDE[ssGeminiSrv](../../includes/ssgeminisrv-md.md)] descarga los orígenes de datos de [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] inactivos si no se usan o cuando el servidor está sufriendo presión de memoria o necesita memoria adicional para ejecutar los trabajos de actualización de datos.|Puede habilitar y deshabilitar [Configurar la recolección de datos de uso para Power Pivot para SharePoint](../../analysis-services/power-pivot-sharepoint/configure-usage-data-collection-for-power-pivot-for-sharepoint.md).|  
|Estado del servidor|Las operaciones de servidor que indican el estado del servidor, medidas en función de la utilización de la memoria y la CPU. Estos datos son históricos. No proporciona información de tiempo real acerca de la carga de procesamiento actual en el servidor.|No. Siempre se recopilan datos de uso para este evento.|  
|Actualización de datos|Operaciones de actualización de datos iniciadas por el servicio de [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] para las actualizaciones de datos programadas. El historial de uso para la actualización de datos se recopila en el nivel de aplicación para los informes de operaciones y se refleja en las páginas de Administrar actualización de datos para los libros individuales.<br /><br /> **Nota** : para [!INCLUDE[ssSQL11SP1](../../includes/sssql11sp1-md.md)] y las implementaciones de SharePoint 2013, la actualización de datos la administra Excel Services, no el servidor de Analysis Services.|No. Los datos de uso se recopilan siempre si habilita la actualización de datos para la aplicación de servicio de [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] .|  
  
##  <a name="servicesjobs"></a> Servicios y trabajos del temporizador  
 La siguiente tabla describe los servicios y los almacenes de recopilación de datos en el sistema de recopilación de datos de uso. Para obtener instrucciones sobre cómo invalidar las programaciones de trabajos de temporizador y forzar una actualización de datos del estado del servidor y de los datos de uso en los informes del panel de administración de [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] , vea [Actualización de datos de Power Pivot con SharePoint 2010](http://msdn.microsoft.com/es-es/01b54e6f-66e5-485c-acaa-3f9aa53119c9). Puede ver los trabajos de temporizador en Administración central de SharePoint. Vaya a **Supervisión**y haga clic en **Comprobar estado de trabajo**. Haga clic en **Revisar definiciones de trabajo**.  
  
|Componente|Programación predeterminada|Description|  
|---------------|----------------------|-----------------|  
|Temporizador de extensiones de SharePoint (SPTimerV4)||Este servicio de Windows se ejecuta localmente en cada equipo miembro de la granja y procesa todos los trabajos del temporizador que se definen en el nivel de granja.|  
|Importación de datos de uso de Microsoft SharePoint Foundation|Cada 30 minutos en SharePoint 2010. Cada 5 minutos en SharePoint 2013.|Este trabajo de temporizador se configura globalmente en el nivel de granja. Mueve los datos de uso de los archivos de registro de uso locales a la base de datos de recopilación de datos de uso central. Puede ejecutar manualmente este trabajo de temporizador para forzar una operación de importación de datos.|  
|Trabajo de temporizador de procesamiento de datos de uso de Microsoft SharePoint Foundation|Diariamente a las 3:00 a.m.|**(\*)** A partir de SQL Server 2012 [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] para SharePoint, se admite este trabajo de temporizador para escenarios de actualización o migración donde puede seguir teniendo datos de uso anteriores en las bases de datos de uso de SharePoint. A partir de SQL Server 2012 [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] para SharePoint, la base de datos de uso de SharePoint no se emplea para la recopilación de uso de [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] y el flujo de trabajo del panel de administración. Se puede ejecutar manualmente el trabajo de temporizador para mover los datos relacionados de [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] restantes de la base de datos de uso de SharePoint a las bases de datos de aplicación de servicio de [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] .<br /><br /> Este trabajo de temporizador se configura globalmente en el nivel de granja. Comprueba si hay datos de uso que hayan expirado en la base de datos de recopilación de datos de uso central (es decir, cualquier registro cuya fecha sea anterior a 30 días). Para los servidores de [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] en la granja, este trabajo del temporizador realiza una comprobación adicional para los datos de uso de [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] . Cuando se detectan los datos de uso de [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] , el trabajo del temporizador mueve los datos a una base de datos de aplicación del servicio usando un identificador de la aplicación para encontrar la base de datos correcta.<br /><br /> Puede ejecutar manualmente este trabajo de temporizador para forzar que se compruebe si los datos han expirado o para forzar la importación de los datos de uso de [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] a una base de datos de aplicación de servicio de [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] .|  
|[!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] Trabajo de temporizador de procesamiento del panel de administración|Diariamente a las 3:00 a.m.|Este trabajo de temporizador actualiza el libro de [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] interno que proporciona datos administrativos al panel de administración de [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] . Consigue información actualizada que administra SharePoint, como son nombres de servidor, nombres de usuario, nombres de aplicación y nombres de archivo que aparecen en los informes del panel o en los elementos web.|  
  
##  <a name="reporting"></a> Informes sobre los datos de uso  
 Para ver los datos de uso de [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)], puede ver los informes integrados en el panel de administración de [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)]. Los informes integrados consolidan los datos de uso que se recuperan de las estructuras de datos de informes en la base de datos de aplicación del servicio. Dado que los datos de informes subyacentes se actualizan diariamente, los informes de uso integrados solo mostrarán la información actualizada cuando el trabajo de temporizador de procesamiento de datos de uso de Microsoft SharePoint Foundation copie los datos en una base de datos de aplicación de servicio de [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)]. De forma predeterminada, esto se produce una vez al día.  
  
 Para obtener más información acerca de cómo ver los informes, vea [Power Pivot Management Dashboard and Usage Data](../../analysis-services/power-pivot-sharepoint/power-pivot-management-dashboard-and-usage-data.md).  
  
## Vea también  
 [Panel de administración de Power Pivot y datos de uso](../../analysis-services/power-pivot-sharepoint/power-pivot-management-dashboard-and-usage-data.md)   
 [Referencia de las opciones de configuración &#40;Power Pivot para SharePoint&#41;](../../analysis-services/power-pivot-sharepoint/configuration-setting-reference-power-pivot-for-sharepoint.md)   
 [Configurar la recolección de datos de uso para Power Pivot para SharePoint](../../analysis-services/power-pivot-sharepoint/configure-usage-data-collection-for-power-pivot-for-sharepoint.md)  
  
  