---
title: Cuadro de diálogo Propiedades del ensamblado (Analysis Services - datos multidimensionales) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- analysis-services
ms.topic: conceptual
f1_keywords:
- sql12.asvs.sqlserverstudio.assemblyproperties.f1
ms.assetid: da1174d6-d82b-4337-ac19-7368dbd95a84
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: cdaa5e0fe92c09b728540d28aa71bdc786d8cae3
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/02/2018
ms.locfileid: "48149185"
---
# <a name="assembly-properties-dialog-box-analysis-services---multidimensional-data"></a>Cuadro de diálogo Propiedades del ensamblado (Analysis Services - Datos multidimensionales)
  Use el cuadro de diálogo **Propiedades del ensamblado** en [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] para establecer las propiedades de una referencia de ensamblado en una base de datos [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] . Para mostrar el cuadro de diálogo **Propiedades del ensamblado** , haga clic con el botón derecho en **Explorador de objetos** y seleccione **Propiedades**.  
  
## <a name="options"></a>Opciones  
  
|Término|Definición|  
|----------|----------------|  
|**Nombre**|Escriba para cambiar el nombre de la referencia de ensamblado.<br /><br /> Nota: Al cambiar este valor no se cambia el nombre del ensamblado al que se refiere la referencia de ensamblado, sino que se cambia el nombre utilizado por la instancia o base de datos de [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] cuando se refiere a la referencia de ensamblado.|  
|**ID**|Muestra el identificador del ensamblado al que se refiere la referencia de ensamblado.|  
|**Descripción**|Escriba para cambiar la descripción de la referencia de ensamblado.|  
|**Marca de tiempo de creación**|Muestra la fecha y la hora de creación de la referencia de ensamblado.|  
|**Última actualización de esquema**|Muestra la fecha y la hora de la última actualización de los metadatos de la referencia de ensamblado.|  
|**Tipo**|Muestra el tipo de referencia de ensamblado. Se muestran las siguientes opciones:<br /><br /> **Ensamblado .NET**: la referencia de ensamblado hace referencia a un [!INCLUDE[msCoName](../includes/msconame-md.md)] ensamblado de .NET Framework.<br /><br /> **DLL de COM**: la referencia de ensamblado hace referencia a una biblioteca COM.|  
|**Source**|Muestra el origen de la referencia de ensamblado. Esta propiedad normalmente contiene la ruta completa y el nombre de archivo del ensamblado al que se refiere la referencia de ensamblado.|  
|**Conjunto de permisos**|Seleccione el conjunto de permisos utilizado para determinar el acceso a la referencia de ensamblado. Para obtener más información acerca de los valores disponibles para esta propiedad, vea <xref:Microsoft.AnalysisServices.ClrAssembly.PermissionSet%2A>.|  
|**Información de suplantación**|Seleccione la información de suplantación que se utilizará al obtener acceso a la referencia de ensamblado. Para más información sobre los valores disponibles para esta propiedad, vea [Elemento ImpersonationInfo &#40;ASSL&#41;](scripting/properties/impersonationinfo-element-assl.md).|  
  
## <a name="see-also"></a>Vea también  
 [Diseñadores y cuadros de diálogo de Analysis Services &#40;datos multidimensionales&#41;](analysis-services-designers-and-dialog-boxes-multidimensional-data.md)   
 [Administración de los ensamblados de modelos multidimensionales](multidimensional-models/multidimensional-model-assemblies-management.md)  
  
  
