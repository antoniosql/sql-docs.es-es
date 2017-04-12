---
title: "Publicar informes en un servidor de informes | Microsoft Docs"
ms.custom: ""
ms.date: "06/01/2016"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "reporting-services-sharepoint"
  - "reporting-services-native"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "entornos de producción [Reporting Services]"
  - "proyectos de informe [Reporting Services]"
  - "configuración de depuración [Reporting Services]"
  - "publicación de informes [Reporting Services]"
  - "publicar informes [Reporting Services]"
  - "propiedades de informe [Reporting Services]"
  - "Diseñador de informes [Reporting Services], implementar informes"
  - "configuración de producción [Reporting Services]"
  - "publicar informes [Reporting Services], entornos de producción"
  - "configuración de depuración local [Reporting Services]"
  - "implementar [Reporting Services], informes"
  - "Diseñador de informes [Reporting Services], publicar informes"
ms.assetid: bd7aa5e0-61ce-43fd-8f74-5d1aeed078bb
caps.latest.revision: 47
author: "guyinacube"
ms.author: "asaxton"
manager: "erikre"
caps.handback.revision: 47
---
# Publicar informes en un servidor de informes
  Después de diseñar y probar un informe o un conjunto de informes, puede usar las características de implementación integradas en [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] para publicar los informes en un servidor de informes. Puede publicar informes individuales en un proyecto del servidor de informes que puede incluir varios informes y orígenes de datos. Publicar un proyecto del servidor de informes es la manera más fácil de publicar varios informes. [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] usa el término *implementación* en lugar del término *publicación*. Las dos condiciones son intercambiables.  
  
 [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] proporciona las configuraciones de proyecto para administrar la publicación de informes. La configuración especifica la ubicación del servidor de informes, la versión de SQL Server Reporting Services instalada en el servidor de informes, si los orígenes de datos publicados en el servidor de informes se sobrescriben y otras opciones. Por ejemplo, la configuración "Debug" puede publicar en un servidor distinto de la configuración de "lanzamiento". Además de utilizar las configuraciones que [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] proporciona, puede crear otras adicionales.  
 
## Requisitos para publicar
El permiso se determina a través de la seguridad basada en roles que define el administrador del servidor de informes. Normalmente, las operaciones de publicación se conceden a través del **rol Publicador**.  
  
## Configuraciones del proyecto  
 El entorno de informes podría tener varios servidores de informes y versiones diferentes de [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] instaladas. Puede crear varias configuraciones y, a continuación, utilizar una diferente según el escenario de implementación. Las configuraciones de proyecto incluyen propiedades para generar los informes, como la carpeta en la que almacenar temporalmente los informes integrados y cómo administrar los problemas de generación. Las configuraciones también tienen las propiedades que se utilizan para especificar la ubicación, la versión y las carpetas del servidor de informes.  
  
 De forma predeterminada, [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] proporciona tres configuraciones de proyecto: **DebugLocal**, **Debug** y **Release**. La configuración predeterminada es de depuración local. Normalmente, se utiliza la configuración de depuración local para ver informes en una ventana de vista previa local, la configuración de depuración para publicar informes en un servidor de pruebas y la configuración de lanzamiento para publicar los informes en un servidor de producción. En la lista desplegable de configuraciones de soluciones de la barra de herramientas estándar, se muestra la configuración activa. Para utilizar una configuración diferente, selecciónela en la lista.  
  
 ![ssrs_project_properties](../../reporting-services/reports/media/ssrs-project-properties.png) 
  
 Para más información, vea:
 + [Páginas de propiedades del proyecto (cuadro de diálogo)](../../reporting-services/tools/project-property-pages-dialog-box.md)
 + [Implementación y compatibilidad de versiones en las herramientas de datos de SQL Server](../../reporting-services/tools/deployment-and-version-support-in-sql-server-data-tools-ssrs.md)
 + [Configurar propiedades de implementación para proyectos de Reporting Services en SSDT](../../reporting-services/tools/set-deployment-properties-reporting-services.md)
  
## Para publicar todos los informes de un proyecto  
  
En el menú **Generar**, haga clic en **Implementar \<nombre de proyecto de informe>**. Como alternativa, en el Explorador de soluciones, haga clic con el botón derecho en el proyecto de informe y, después, haga clic en **Implementar**. El estado del proceso de publicación se puede ver en la ventana Resultados.  
  
Al implementar un proyecto del servidor de informes, también se implementan los orígenes de datos compartidos en el proyecto de informe. Todos los informes se implementan utilizando la misma configuración de proyecto: el mismo servidor de informes, la misma carpeta en el servidor, etc. Para publicar informes en servidores diferentes, publíquelos uno por uno o incluya solo los que desee en el proyecto del servidor de informes. Una solución puede incluir varios proyectos del servidor de informes. Utilizar varios proyectos podría facilitar la administración de la implementación de informes porque se puede usar una configuración diferente para implementar proyectos distintos. 
  
## Para publicar solo un informe  
  
En el Explorador de soluciones, haga clic con el botón derecho en el informe y, después, haga clic en **Implementar**. El estado del proceso de publicación se puede ver en la ventana Resultados.  
  
 Al publicar un informe, también debe implementar los orígenes de datos compartidos que el informe utiliza.   
 Si no desea publicar todos los informes de un proyecto, puede optar por publicar uno solo. Para ello, seleccione una configuración que implemente el informe (por ejemplo, la configuración de lanzamiento), haga clic con el botón derecho en el informe y, después, haga clic en **Implementar**.  
  
 Si un informe utiliza un origen de datos compartido, también tiene que implementar el origen de datos compartido o el informe implementado no se ejecutará. Haga clic con el botón derecho en el origen de datos compartido y, después, haga clic en **Implementar**.  
  
 Se debe especificar la dirección URL del servidor de destino del servidor de informes y puede ser conveniente cambiar las carpetas predeterminadas en las que los informes y orígenes de datos compartidos se implementan.  

  
## Vea también  
 [Páginas de propiedades del proyecto (cuadro de diálogo)](../../reporting-services/tools/project-property-pages-dialog-box.md)   
 [Administración de contenido del servidor de informes &#40;Modo nativo de SSRS&#41;](../../reporting-services/report-server/report-server-content-management-ssrs-native-mode.md)   
 [Actualizar informes](../../reporting-services/install-windows/upgrade-reports.md)  
  
  