---
title: Elemento ExecuteResponse (XMLA) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- analysis-services
- docset-sql-devref
ms.topic: reference
api_name:
- ExecuteResponse Element
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
f1_keywords:
- urn:schemas-microsoft-com:xml-analysis#ExecuteResponse
- http://schemas.microsoft.com/analysisservices/2003/engine#ExecuteResponse
- microsoft.xml.analysis.executeresponse
helpviewer_keywords:
- ExecuteResponse element
ms.assetid: 6edb1b82-da4c-4cd9-9385-bea04032f0eb
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 002da257a4d1137b0e52743eec99f1b0aced56c0
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/02/2018
ms.locfileid: "48047586"
---
# <a name="executeresponse-element-xmla"></a>Elemento ExecuteResponse (XMLA)
  Contiene la información devuelta por una instancia de [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] en respuesta a una [Execute](xml-elements-methods-execute.md) llamada al método.  
  
 **Espacio de nombres** urn:schemas-microsoft-com:xml-analysis  
  
## <a name="syntax"></a>Sintaxis  
  
```xml  
  
<ExecuteResponse>  
   <return>  
</ExecuteResponse>  
```  
  
## <a name="element-characteristics"></a>Características de los elementos  
  
|Característica|Descripción|  
|--------------------|-----------------|  
|Tipo y longitud de los datos|None|  
|Valor predeterminado|None|  
|Cardinalidad|1-1: Elemento requerido que puede aparecer una y solo una vez.|  
  
## <a name="element-relationships"></a>Relaciones del elemento  
  
|Relación|Elemento|  
|------------------|-------------|  
|Elementos primarios|None|  
|Elementos secundarios|[devolver](xml-elements-properties/return-element-xmla.md)|  
  
## <a name="remarks"></a>Comentarios  
 El elemento `ExecuteResponse` es el elemento superior dentro del cuerpo de una respuesta de SOAP para el método `Execute`.  
  
## <a name="see-also"></a>Vea también  
 [Elemento DiscoverResponse &#40;XMLA&#41;](xml-elements-objects-discoverresponse.md)   
 [Objetos &#40;XMLA&#41;](xml-elements-objects.md)  
  
  
