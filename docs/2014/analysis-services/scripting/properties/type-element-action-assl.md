---
title: Type (elemento) (acción) (ASSL) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- analysis-services
- docset-sql-devref
ms.topic: reference
api_name:
- Type Element (Action)
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
f1_keywords:
- TYPE
helpviewer_keywords:
- Type element
ms.assetid: 534cdf99-1edf-4490-9eaa-61f189a19434
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: af38eb6a60e8e54ecfc4ac5bb4fb05faeab69feb
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/02/2018
ms.locfileid: "48168425"
---
# <a name="type-element-action-assl"></a>Elemento Type (Action) (ASSL)
  Contiene el tipo de la [acción](../objects/action-element-assl.md) elemento.  
  
## <a name="syntax"></a>Sintaxis  
  
```xml  
  
<Action>  
   ...  
   <Type>...</Type>  
   ...  
</Action>  
```  
  
## <a name="element-characteristics"></a>Características de los elementos  
  
|Característica|Descripción|  
|--------------------|-----------------|  
|Tipo y longitud de los datos|String (enumeración)|  
|Valor predeterminado|None|  
|Cardinalidad|1-1: Elemento necesario que se produce una vez y solo una vez.|  
  
## <a name="element-relationships"></a>Relaciones del elemento  
  
|Relación|Elemento|  
|------------------|-------------|  
|Elemento primario|[Acción](../objects/action-element-assl.md)|  
|Elementos secundarios|None|  
  
## <a name="remarks"></a>Comentarios  
 El valor de este elemento se limita a una de las cadenas enumeradas en la tabla siguiente.  
  
|Valor|Descripción|  
|-----------|-----------------|  
|*Dirección URL*|Muestra una página variable en un explorador de Internet.|  
|*HTML*|Ejecuta un script HTML en un explorador de Internet.|  
|*Instrucción*|Ejecuta un comando de OLE DB.|  
|*Obtención de detalles*|Recupera un conjunto de filas para obtener detalles.<br /><br /> Este valor es idéntico al *conjunto de filas* e identifica acciones de obtención de detalles. Solo se pueden utilizar en acciones cuyo [TargetType](targettype-element-assl.md) valor se establece en *celdas*.|  
|*Conjunto de datos*|Recupera un conjunto de datos.|  
|*Conjunto de filas*|Recupera un conjunto de filas.|  
|*línea de comandos*|Ejecuta un comando en un símbolo del sistema.|  
|*Propietario*|Realiza una operación mediante una interfaz distinta de las descritas previamente en esta tabla.|  
|*Informe*|Muestra una página variable en un explorador de Internet.<br /><br /> Este valor es idéntico al *Url* e identifica acciones de informe.|  
  
 El elemento que se corresponde con el elemento primario de `Type` en el objeto de Analysis Management Objects (AMO) es el modelo <xref:Microsoft.AnalysisServices.Action>.  
  
## <a name="see-also"></a>Vea también  
 [Tipo de Drillthroughaction &#40;ASSL&#41;](../data-type/action-data-type-assl.md)   
 [Tipo de datos ReportAction &#40;ASSL&#41;](../data-type/reportaction-data-type-assl.md)   
 [Propiedades &#40;ASSL&#41;](properties-assl.md)  
  
  
