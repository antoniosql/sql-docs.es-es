---
title: Type (elemento) (MeasureGroupAttribute) (ASSL) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- analysis-services
- docset-sql-devref
ms.topic: reference
api_name:
- Type Element (MeasureGroupAttribute)
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
f1_keywords:
- TYPE
helpviewer_keywords:
- Type element
ms.assetid: 93740504-297a-4a06-ab3e-b598e466eebb
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: dfe3b0cda9061e18b9a275eac98e02ed90453adc
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/02/2018
ms.locfileid: "48087937"
---
# <a name="type-element-measuregroupattribute-assl"></a>Elemento Type (MeasureGroupAttribute) (ASSL)
  Contiene el tipo de un [MeasureGroupAttribute](../data-type/measuregroupattribute-data-type-assl.md) elemento.  
  
## <a name="syntax"></a>Sintaxis  
  
```xml  
  
<MeasureGroupAttribute>  
   ...  
   <Type>...</Type>  
   ...  
</MeasureGroupAttribute>  
```  
  
## <a name="element-characteristics"></a>Características de los elementos  
  
|Característica|Descripción|  
|--------------------|-----------------|  
|Tipo y longitud de los datos|String (enumeración)|  
|Valor predeterminado|*Regular*|  
|Cardinalidad|0-1: Elemento opcional que puede aparecer una y solo una vez.|  
  
## <a name="element-relationships"></a>Relaciones del elemento  
  
|Relación|Elemento|  
|------------------|-------------|  
|Elemento primario|[MeasureGroupAttribute](../data-type/measuregroupattribute-data-type-assl.md)|  
|Elementos secundarios|None|  
  
## <a name="remarks"></a>Comentarios  
 El valor de este elemento se limita a una de las cadenas enumeradas en la tabla siguiente.  
  
|Valor|Descripción|  
|-----------|-----------------|  
|*Regular*|Representa un atributo normal.|  
|*Granularidad*|Representa un atributo de granularidad.|  
  
 La enumeración que corresponde a los valores permitidos para `Type` en el objeto de Analysis Management Objects (AMO) es el modelo <xref:Microsoft.AnalysisServices.MeasureGroupAttributeType>.  
  
 El elemento que se corresponde con el elemento primario de `Type` en el objeto de Analysis Management Objects (AMO) es el modelo <xref:Microsoft.AnalysisServices.MeasureGroupAttribute>.  
  
## <a name="see-also"></a>Vea también  
 [Atributos de elemento &#40;ASSL&#41;](../collections/attributes-element-assl.md)   
 [Tipo de datos RegularMeasureGroupDimension &#40;ASSL&#41;](../data-type/dimension-data-type-assl.md)   
 [Propiedades &#40;ASSL&#41;](properties-assl.md)  
  
  
