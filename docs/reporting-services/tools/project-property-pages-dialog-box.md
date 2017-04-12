---
title: "P&#225;ginas de propiedades del proyecto (cuadro de di&#225;logo) | Microsoft Docs"
ms.custom: ""
ms.date: "05/31/2016"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "reporting-services-sharepoint"
  - "reporting-services-native"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "sql13.rpt.rptdesigner.projectpropertypages.general.f1"
helpviewer_keywords: 
  - "Páginas de propiedades del proyecto (cuadro de diálogo)"
ms.assetid: 209d9e22-37fc-418f-8739-83adcf447d3f
caps.latest.revision: 35
author: "guyinacube"
ms.author: "asaxton"
manager: "erikre"
caps.handback.revision: 35
---
# P&#225;ginas de propiedades del proyecto (cuadro de di&#225;logo)
  Utilice las páginas de propiedades del proyecto para configurar las propiedades de implementación de un proyecto del servidor de informes. Para abrir este cuadro de diálogo, en el menú **Proyecto**, haga clic en *\<Nombre del proyecto de informe>***Propiedades**.  
  
 Después de definir las propiedades de configuración, puede seleccionar una configuración en la lista desplegable **Configuraciones de soluciones** de la barra de herramientas.  

![ssrs_project_properties](../../reporting-services/reports/media/ssrs-project-properties.png)
  
## Opciones  
 **Configuración**  
 Seleccione la configuración que desee editar. Inicialmente, están disponibles las configuraciones siguientes: **Debug**, **DebugLocal**y **Release**. La configuración activa aparece en primer lugar (por ejemplo, **Active(Debug)**).  
  
 Para ver propiedades para más de una configuración al mismo tiempo, seleccione **Todas las config.** o **Varias configuraciones**.  
  
 Para crear más configuraciones, haga clic en **Administrador de configuración** en la barra de herramientas.  
  
 **Administrador de configuración**  
 Administre las configuraciones de toda la solución o agregue más configuraciones. Para obtener más información, vea la documentación de [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] .  
  
 **OutputPath**  
 Escriba o pegue la ruta de acceso para almacenar la definición de informe utilizada en la comprobación de la compilación, implementación y vista previa de los informes. La ruta de acceso debe ser diferente de la que se utiliza para el proyecto y una ruta de acceso relativa que sea una carpeta secundaria bajo la ruta de acceso del proyecto.  
  
> [!NOTE]  
>  Puede utilizar varias configuraciones para intercambiar entre las rutas de acceso en función de la tarea que realice.  
  
 **ErrorLevel**  
 Escriba la gravedad de los problemas de compilación que se notifican como errores. Los problemas con un nivel de gravedad menor o igual que el valor de **ErrorLevel** se notifican como errores; de lo contrario, se notifican como advertencias. Cualquier error hará que la tarea de compilación dé un error. Los niveles de gravedad válidos abarcan de 0 a 4, ambos incluidos. El valor predeterminado es 2.  
  
 **StartItem**  
 Seleccione el informe que se muestra en el explorador web después de publicar el informe en el servidor de informes o en la ventana de vista previa cuando el proyecto se ejecuta en modo local. Es necesario un elemento de inicio para las configuraciones que generan el proyecto (pero no implementan) y para usar el comando **Debug** (**F5**). Es necesario para las configuraciones que implementan el proyecto.  
  
 **OverwriteDataSources**  
 Seleccione **True** para sobrescribir el origen de datos del servidor con el origen de datos del proyecto cuando se publiquen los informes. Seleccione **False** para dejar el origen de datos existente en el servidor.  
  
 **TargetServerVersion**  
 Seleccione la versión adecuada de [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)], o bien seleccione **Detectar versión** para determinar automáticamente la versión instalada en el servidor identificado por la propiedad **TargetServer URL**. El valor predeterminado es **[!INCLUDE[ssCurrent_md](../../includes/sscurrent-md.md)]**.  
  
 **TargetDataSourceFolder**  
 Nombre de la carpeta donde se almacenarán los orígenes de datos publicados. Si no especifica una carpeta, el origen de datos se publica en la misma carpeta que el informe. Si la carpeta no existe en el servidor de informes, el Diseñador de informes la crea cuando los informes se publiquen.  
  
 Al publicar en un servidor de informes que se ejecute en modo nativo, especifique la ruta de acceso completa de la jerarquía de carpetas comenzado por la raíz. Por ejemplo, Carpeta1/Carpeta2/Carpeta3.  
  
 Al publicar en un servidor de informes que se ejecute en el modo integrado de SharePoint, use una dirección URL a la biblioteca de SharePoint. Por ejemplo, `http:\\<servername>\<site>\Documents\MyFolder`.  
  
 **TargetReportFolder**  
 Nombre de la carpeta donde se almacenarán los informes publicados. De forma predeterminada, éste es el nombre del proyecto de informe. Si la carpeta no existe en el servidor de informes, el Diseñador de informes la crea cuando los informes se publiquen.  
  
 Al publicar en un servidor de informes que se ejecute en modo nativo, especifique la ruta de acceso completa de la jerarquía de carpetas comenzado por la raíz. Si una carpeta se encuentra dentro de otra carpeta, incluya una ruta de acceso a la carpeta que empieza en la raíz, como Carpeta1/Carpeta2/Carpeta3.  
  
 Al publicar en un servidor de informes que se ejecute en el modo integrado de SharePoint, use una dirección URL a la biblioteca de SharePoint. Por ejemplo, `http:\\<servername>\\<site>\Documents\MyFolder`.  
  
 **TargetServerURL**  
 Dirección URL del servidor de informes de destino. Antes de publicar un informe, establezca esta propiedad en la dirección URL de un servidor de informes válido.  
  
 Al publicar en un servidor de informes que se ejecute en modo nativo, utilice la dirección URL del directorio virtual del servidor de informes. Por ejemplo, `http:\\<server>\reportserver`. Se trata del directorio virtual del servidor de informes, y no del Administrador de informes. De manera predeterminada, el servidor de informes se instala en un directorio virtual denominado "reportserver".  
  
 Al publicar en un servidor de informes que se ejecute en el modo integrado de SharePoint, use una dirección URL a un sitio de nivel superior o un subsitio de SharePoint. Si no especifica ningún sitio, se usa el sitio de nivel superior predeterminado. Por ejemplo: 
+ `http:\\<servername>`, 
+ `http:\\<servername\<site>` 
+ `http:\\<servername>\<site>\<subsite>`.  
  
## Vea también  
 [Publicar informes](../Topic/Publish%20Reports.md)   
 [Publicar un informe en una biblioteca de SharePoint](../../reporting-services/reports/publish-a-report-to-a-sharepoint-library.md)   
 [Establecer propiedades de implementación &#40;Reporting Services&#41;](../../reporting-services/tools/set-deployment-properties-reporting-services.md)   
 [Diseñador de informes (Ayuda F1)](../../reporting-services/tools/report-designer-f1-help.md)  
  
  