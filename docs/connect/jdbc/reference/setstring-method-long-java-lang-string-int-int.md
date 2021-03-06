---
title: Método setString (long, java.lang.String, int, int) | Documentos de Microsoft
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.suite: sql
ms.technology: connectivity
ms.tgt_pltfrm: ''
ms.topic: conceptual
apiname:
- SQLServerClob.setString (long, java.lang.String, int, int)
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: 9fb59b09-e825-46a6-ba5d-85d4a8dc143a
caps.latest.revision: 10
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: ef844ff6d9ce4d9868345b56c6e0f39dceeb8839
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/03/2018
ms.locfileid: "32844490"
---
# <a name="setstring-method-long-javalangstring-int-int"></a>Método setString (long, java.lang.String, int, int)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Escribe la cadena especificada en el objeto CLOB comenzando en la posición establecida y según el desplazamiento y longitud indicados.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
  
public int setString(long pos,  
                     java.lang.String str,  
                     int offset,  
                     int len)  
```  
  
#### <a name="parameters"></a>Parámetros  
 *punto de venta*  
  
 La posición donde se comienza a escribir en el CLOB.  
  
 *str*  
  
 La cadena que se va a escribir en CLOB.  
  
 *offset*  
  
 El desplazamiento en la cadena a partir del que se van a comenzar a leer los caracteres.  
  
 *len*  
  
 El número de caracteres que se va a escribir.  
  
## <a name="return-value"></a>Valor devuelto  
 El número de caracteres que se han escrito.  
  
## <a name="exceptions"></a>Excepciones  
 java.sql.SQLException  
  
## <a name="remarks"></a>Comentarios  
 Este método setString especificado por el método setString en la interfaz java.sql.Clob.  
  
 Los datos de caracteres se sobrescriben tomando como punto de inicio la posición especificada y pueden sobrescribir la longitud inicial del CLOB. Si se especifica un valor position+1, se anexará la cadena. Si se especifican valores position+2 o superiores (o cero o menos), se producirá un error de la posición.  
  
## <a name="see-also"></a>Vea también  
 [Método setString &#40;SQLServerClob&#41;](../../../connect/jdbc/reference/setstring-method-sqlserverclob.md)   
 [Métodos SQLServerClob](../../../connect/jdbc/reference/sqlserverclob-methods.md)   
 [Miembros SQLServerClob](../../../connect/jdbc/reference/sqlserverclob-members.md)   
 [Clase SQLServerClob](../../../connect/jdbc/reference/sqlserverclob-class.md)  
  
  
