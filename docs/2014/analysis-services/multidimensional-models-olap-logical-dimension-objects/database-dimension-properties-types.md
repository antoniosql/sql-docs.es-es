---
title: Tipos de dimensión | Documentos de Microsoft
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- analysis-services
- docset-sql-devref
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- time dimensions [Analysis Services]
- quantitative dimensions [Analysis Services]
- BillOfMaterials dimension [Analysis Services]
- geography dimensions
- utility dimensions [Analysis Services]
- channel dimensions
- dimensions [Analysis Services], types
- products dimensions [Analysis Services]
- account dimensions [Analysis Services]
- organization dimensions
- currency dimensions [Analysis Services]
- rates dimensions
- promotion dimensions
- scenario dimensions [Analysis Services]
- customers dimensions [Analysis Services]
- Type property
ms.assetid: bd3195da-e762-4c98-b643-34c76e842343
caps.latest.revision: 37
author: Minewiskan
ms.author: owend
manager: mblythe
ms.openlocfilehash: 1fe0311a992f0f8c067ba6e7096698f96f8bc4bc
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/19/2018
ms.locfileid: "36196332"
---
# <a name="dimension-types"></a>Tipos de dimensiones
  El valor de la propiedad `Type` proporciona información acerca del contenido de una dimensión al servidor y a las aplicaciones cliente. En algunos casos, el valor de `Type` solo constituye una guía para las aplicaciones cliente y es opcional. En otros casos, como en las dimensiones `Accounts` o `Time`, la configuración de la propiedad `Type` para la dimensión y sus atributos determina comportamientos específicos basados en el servidor y puede que sea necesario implementar ciertos comportamientos en el cubo. Por ejemplo, la propiedad `Type` de una dimensión se puede establecer en `Accounts` para indicar a las aplicaciones cliente que la dimensión estándar contiene atributos de cuenta. Para obtener más información sobre el tiempo, cuenta y las dimensiones de moneda, vea [crear una dimensión de tipo de fecha](../multidimensional-models/database-dimensions-create-a-date-type-dimension.md), [crear una cuenta financiera de dimensión de tipo de elementos primarios y secundarios](../multidimensional-models/database-dimensions-finance-account-of-parent-child-type.md), y [crear una divisa tipo de dimensión](../multidimensional-models/database-dimensions-create-a-currency-type-dimension.md).  
  
 El valor predeterminado para el tipo de dimensión es `Regular`, que no realiza suposiciones acerca del contenido de la dimensión. Se trata del valor predeterminado para todas las dimensiones al definir inicialmente una dimensión, a menos que se especifique `Time` al definir la dimensión mediante el Asistente para Dimensiones. También se debe dejar `Regular` como tipo de dimensión si el Asistente para dimensiones no muestra un tipo adecuado para el tipo de dimensión.  
  
## <a name="available-dimension-types"></a>Tipos de dimensiones disponibles  
 La tabla siguiente describen los tipos de dimensiones disponibles en [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)].  
  
|Tipo de dimensión|Descripción|  
|--------------------|-----------------|  
|Regular|Dimensión cuyo tipo no se ha establecido en un tipo de dimensión especial.|  
|Time|Dimensión cuyos atributos representan periodos de tiempo, como años, semestres, trimestres, meses y días.|  
|Organización|Dimensión cuyos atributos representan información organizativa, como empleados o subsidiarias.|  
|Geografía|Dimensión cuyos atributos representan información geográfica, como ciudades o códigos postales.|  
|Lista de materiales|Dimensión cuyos atributos representan información de inventario o de fabricación, como listas de piezas para productos.|  
|Cuentas|Dimensión cuyos atributos representan un gráfico de cuentas para la elaboración de informes financieros.|  
|Clientes|Dimensión cuyos atributos representan información de clientes o de contacto.|  
|Productos|Dimensión cuyos atributos representan información de productos.|  
|Escenario|Dimensión cuyos atributos representan información de planeación o análisis estratégico.|  
|Cuantitativo|Dimensión cuyos atributos representan información cuantitativa.|  
|Utilidad|Dimensión cuyos atributos representan información diversa.|  
|Moneda|Este tipo de dimensión contiene datos de moneda y metadatos.|  
|Tarifas|Dimensión cuyos atributos representan información de tasa de cambio.|  
|Canal|Dimensión cuyos atributos representan información de canal.|  
|Promoción|Dimensión cuyos atributos representan información de promociones de marketing.|  
  
## <a name="see-also"></a>Vea también  
 [Crear una dimensión mediante el uso de una tabla existente](../multidimensional-models/create-a-dimension-by-using-an-existing-table.md)   
 [Dimensiones &#40;Analysis Services - datos multidimensionales&#41;](dimensions-analysis-services-multidimensional-data.md)  
  
  