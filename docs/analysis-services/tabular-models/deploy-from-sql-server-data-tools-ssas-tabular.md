---
title: "Implementar con SQL Server Data Tools (SSAS tabular) | Microsoft Docs"
ms.custom: ""
ms.date: "03/01/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "analysis-services"
  - "analysis-services/multidimensional-tabular"
  - "analysis-services/data-mining"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "sql13.asvs.bidtoolset.deploystatus.f1"
ms.assetid: 67dde3fe-ba43-41f3-b56c-c656029ee93f
caps.latest.revision: 17
author: "Minewiskan"
ms.author: "owend"
manager: "erikre"
caps.handback.revision: 17
---
# Implementar con SQL Server Data Tools (SSAS tabular)
  Utilice las tareas de este tema para implementar una solución de modelo tabular mediante el comando Implementar en [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)].  
  
 Secciones de este tema:  
  
-   [Configurar las propiedades Opciones de implementación y Servidor de implementación](#bkmk_deploy)  
  
-   [Implementar una solución de modelo tabular](#bkmk_deploy_proc)  
  
-   [Estado de la implementación](#bkmk_deploy_status)  
  
##  <a name="bkmk_deploy"></a> Configurar las propiedades Opciones de implementación y Servidor de implementación  
 Antes de implementar la solución de modelo tabular, primero debe especificar las propiedades Opciones de implementación y Servidor de implementación. Para obtener más información sobre las propiedades y la configuración de la implementación, vea [Implementación de soluciones de modelos tabulares &#40;SSAS tabular&#41;](../../analysis-services/tabular-models/tabular-model-solution-deployment-ssas-tabular.md).  
  
#### Para configurar las propiedades Opciones de implementación y Servidor de implementación  
  
1.  En [!INCLUDE[ssBIDevStudio](../../includes/ssbidevstudio-md.md)], en el **Explorador de soluciones**, haga clic con el botón derecho en el nombre del proyecto y, después, haga clic en **Propiedades**.  
  
2.  En el cuadro de diálogo **Propiedades de \<nombre de proyecto>**, en **Opciones de implementación**, especifique la configuración de las propiedades si difiere de la predeterminada.  
  
    > [!NOTE]  
    >  Para los modelos en modo de almacenamiento en caché, el **Modo de consulta** siempre es **In-Memory**.  
  
    > [!NOTE]  
    >  No puede especificar la **Configuración de suplantación** de los modelos que se encuentran en modo DirectQuery.  
  
3.  En **Servidor de implementación**, especifique la configuración de las propiedades **Servidor** (nombre), **Edición**, **Base de datos** (nombre) y **Nombre del cubo** si difiere de la predeterminada y, después, haga clic en **Aceptar**.  
  
> [!NOTE]  
>  También puede especificar el valor de la propiedad Servidor de implementación predeterminado de modo que los proyectos que se creen se implementen automáticamente en el servidor especificado. Para obtener más información, vea [Configurar las propiedades predeterminadas de modelado de datos y de implementación &#40;SSAS tabular&#41;](../../analysis-services/tabular-models/configure-default-data-modeling-and-deployment-properties-ssas-tabular.md).  
  
##  <a name="bkmk_deploy_proc"></a> Implementar una solución de modelo tabular  
  
#### Para implementar una solución de modelo tabular  
  
-   En [!INCLUDE[ssBIDevStudio](../../includes/ssbidevstudio-md.md)], en el menú **Compilar**, haga clic en **Implementar \<nombre del proyecto>**.  
  
     Aparecerá el cuadro de diálogo **Implementar** e indicará el estado de la implementación de los metadatos y del procesamiento (a menos que se haya establecido la propiedad Opción de procesamiento en No procesar) de cada tabla incluida en el modelo. Una vez completado el proceso de implementación, use [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] para conectarse a la instancia de Analysis Services y comprobar que se ha creado el nuevo objeto de base de datos de modelo, o use una aplicación cliente de informes para conectarse al modelo implementado.  
  
##  <a name="bkmk_deploy_status"></a> Estado de la implementación  
 El cuadro de diálogo **Implementar** permite supervisar el progreso de una operación de implementación. Una operación de implementación también se puede detener.  
  
 **Estado**  
 Indica si la operación de implementación se realizó correctamente o no.  
  
 **Detalles**  
 Enumera los elementos de metadatos implementados y el estado de cada uno, y proporciona un mensaje sobre cualquier problema.  
  
 **Detener implementación**  
 Haga clic en esta opción para detener la operación de implementación. Esta opción resulta útil si la operación de implementación tarda demasiado o hay demasiados errores.  
  
## Vea también  
 [Implementación de soluciones de modelos tabulares &#40;SSAS tabular&#41;](../../analysis-services/tabular-models/tabular-model-solution-deployment-ssas-tabular.md)   
 [Configurar las propiedades predeterminadas de modelado de datos y de implementación &#40;SSAS tabular&#41;](../../analysis-services/tabular-models/configure-default-data-modeling-and-deployment-properties-ssas-tabular.md)  
  
  