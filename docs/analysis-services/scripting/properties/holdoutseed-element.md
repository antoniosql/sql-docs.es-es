---
title: Elemento HoldoutSeed | Documentos de Microsoft
ms.date: 5/8/2018
ms.prod: sql
ms.custom: assl
ms.reviewer: owend
ms.technology: analysis-services
ms.topic: reference
author: minewiskan
ms.author: owend
manager: kfile
ms.openlocfilehash: f0fbf102dcfc731f02195964c6657244e9bf0b70
ms.sourcegitcommit: c12a7416d1996a3bcce3ebf4a3c9abe61b02fb9e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/10/2018
ms.locfileid: "34036436"
---
# <a name="holdoutseed-element"></a>Elemento HoldoutSeed
[!INCLUDE[ssas-appliesto-sqlas](../../../includes/ssas-appliesto-sqlas.md)]
  Especifica el valor de inicialización de una partición de extracción repetible que contiene el conjunto de pruebas de un [MiningStructure](../../../analysis-services/scripting/objects/miningstructure-element-assl.md) elemento. Esta semilla asegura que el contenido del modelo permanece igual durante el nuevo procesamiento. Si no se especifica o se establece en 0, [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] crea un valor de inicialización mediante un algoritmo hash en el nombre de la estructura de minería de datos.  
  
## <a name="syntax"></a>Sintaxis  
  
```xml  
  
<MiningStructure>  
   ...  
   <ddl100_100:HoldoutSeed>...</ddl100_100:HoldoutSeed>  
   ...  
</MiningStructure>  
```  
  
## <a name="element-characteristics"></a>Características de los elementos  
  
|Característica|Descripción|  
|--------------------|-----------------|  
|Tipo y longitud de los datos|Long|  
|Valor predeterminado|0|  
|Cardinalidad|0-1: Elemento opcional que puede producirse una sola y única vez.|  
  
## <a name="element-relationships"></a>Relaciones del elemento  
  
|Relación|Elemento|  
|------------------|-------------|  
|Elemento primario|[MiningStructure](../../../analysis-services/scripting/objects/miningstructure-element-assl.md)|  
|Elementos secundarios|Ninguno|  
  
## <a name="remarks"></a>Comentarios  
 Al crear primero una estructura de minería de datos, el identificador y el nombre son los mismos. Sin embargo, puede cambiar el nombre de la estructura de minería de datos. Por consiguiente, si desea asegurarse de que la partición es repetible, no debería confiar en la semilla creada por el nombre sino que debería definir explícitamente una semilla.  
  
 Además, cuando se crea una copia de una estructura de minería de datos mediante el uso de la **exportar** instrucción [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] conservará el nombre de la nueva estructura de minería de datos pero generará automáticamente un nuevo identificador. Por consiguiente, es posible tener dos estructuras de minería de datos que comparten el mismo nombre pero tienen identificadores diferentes. Dos estructuras de minería de datos que tengan el mismo nombre tendrán la misma semilla. Sin embargo, como el particionamiento de los datos también depende de los datos de origen, el contenido real de las particiones de cada estructura puede ser diferente.  
  
 Las nuevas propiedades **HoldoutMaxCases**, **HoldoutMaxPercent**, **HoldoutSeed**, o **HoldoutActualSize** sólo están disponibles en [!INCLUDE[ssKatmai](../../../includes/sskatmai-md.md)] y versiones posteriores. Por lo tanto, es necesario establecer estas propiedades como prefijos con el nuevo espacio de nombres, tal como se muestra en la descripción de la sintaxis, o [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] devolverá un error.  
  
 **Tenga en cuenta** en [!INCLUDE[ssVersion2005](../../../includes/ssversion2005-md.md)], [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] no admitía el uso de particiones de exclusión en una estructura de minería de datos. Por lo tanto, [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] instrucciones de Scripting Language (ASSL) que contienen los parámetros de exclusión **HoldoutMaxCases**, **HoldoutMaxPercent**, **HoldoutSeed**, o **HoldoutActualSize** no se puede usar en [!INCLUDE[ssVersion2005](../../../includes/ssversion2005-md.md)]. Si usa uno de estos parámetros de exclusión en una instrucción ASSL en [!INCLUDE[ssVersion2005](../../../includes/ssversion2005-md.md)], [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] devolverá un error.  
  
 El elemento que corresponde al elemento primario de **HoldoutSeed** en el objeto de Analysis Management Objects (AMO) es el modelo <xref:Microsoft.AnalysisServices.MiningStructure>.  
  
## <a name="see-also"></a>Vea también  
 [Propiedades &#40;ASSL&#41;](../../../analysis-services/scripting/properties/properties-assl.md)   
 [Elemento HoldoutActualSize](../../../analysis-services/scripting/properties/holdoutactualsize-element.md)   
 [Elemento HoldoutMaxPercent](../../../analysis-services/scripting/properties/holdoutmaxpercent-element.md)   
 [Elemento HoldoutMaxCases](../../../analysis-services/scripting/properties/holdoutmaxcases-element.md)  
  
  
