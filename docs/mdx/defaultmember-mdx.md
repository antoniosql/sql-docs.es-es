---
title: DefaultMember (MDX) | Documentos de Microsoft
ms.date: 06/04/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: mdx
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 3a0c11acadcbdcadfd9398baff09db9292c87eb2
ms.sourcegitcommit: 97bef3f248abce57422f15530c1685f91392b494
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/04/2018
ms.locfileid: "34740134"
---
# <a name="defaultmember-mdx"></a>DefaultMember (MDX)


  Devuelve el miembro predeterminado de una jerarquía.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
  
Hierarchy_Expression.DefaultMember  
```  
  
## <a name="arguments"></a>Argumentos  
 *Hierarchy_Expression*  
 Expresión MDX válida que devuelve una jerarquía.  
  
## <a name="remarks"></a>Notas  
 El miembro predeterminado de un atributo se utiliza para evaluar expresiones cuando un atributo no está incluido en una consulta.  
  
## <a name="example"></a>Ejemplo  
 En el ejemplo siguiente se usa el **DefaultMember** función, junto con el **nombre** función para devolver el miembro predeterminado para la dimensión de moneda de destino en el cubo de Adventure Works. El ejemplo devuelve **dólar estadounidense**. El **nombre** función se utiliza para devolver el nombre de la medida en lugar de la propiedad predeterminada de la medida, que es **valor**.  
  
```  
WITH MEMBER Measures.x AS   
   [Destination Currency].[Destination Currency].DefaultMember.Name  
SELECT Measures.x ON 0  
FROM [Adventure Works]  
```  
  
## <a name="see-also"></a>Vea también  
 [Referencia de funciones MDX &#40;MDX&#41;](../mdx/mdx-function-reference-mdx.md)   
 [Definir a un miembro predeterminado](../analysis-services/multidimensional-models/attribute-properties-define-a-default-member.md)  
  
  
