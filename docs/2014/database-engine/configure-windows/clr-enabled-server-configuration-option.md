---
title: clr enabled (opción de configuración del servidor) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- database-engine
ms.topic: conceptual
helpviewer_keywords:
- assemblies [CLR integration], verifying can run
- clr enabled option
ms.assetid: 0722d382-8fd3-4fac-b4a8-cd2b7a7e0293
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.openlocfilehash: a796426f02c2ad9c0878c212c51eb0e90cfce8bf
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/02/2018
ms.locfileid: "48219385"
---
# <a name="clr-enabled-server-configuration-option"></a>clr enabled (opción de configuración del servidor)
  Utilice la opción clr enabled para especificar si [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]puede ejecutar ensamblados de usuario. La opción clr enabled proporciona los valores que se indican a continuación.  
  
|Valor|Descripción|  
|-----------|-----------------|  
|0|Ejecución de ensamblado no permitida en [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].|  
|1|Ejecución de ensamblado permitida en [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].|  
  
 Los servidores WOW64 se deben reiniciar antes de que los cambios de este valor surtan efecto. El reinicio no se requiere para otros tipos de servidor.  
  
> [!NOTE]  
>  Cuando se ejecuta RECONFIGURE y se cambia el valor de ejecución de la opción clr enabled de 1 a 0, se descargan inmediatamente todos los dominios de aplicación que incluyen ensamblados de usuario.  
  
> [!NOTE]  
>  No se admite la ejecución de Common Language Runtime (CLR) con "agrupación ligera". Deshabilite una de las dos opciones: "clr enabled" o "agrupación ligera". Las características que dependen de CLR y que no funcionan correctamente en modo de fibra incluyen el `hierarchy` tipo de datos, replicación y la administración basada en directivas.  
  
## <a name="example"></a>Ejemplo  
 El ejemplo siguiente muestra primero la configuración actual de la opción clr enabled y después habilita la opción estableciendo su valor en 1. Para deshabilitar la opción, establezca el valor en 0.  
  
```  
EXEC sp_configure 'clr enabled';  
EXEC sp_configure 'clr enabled' , '1';  
RECONFIGURE;  
  
```  
  
## <a name="see-also"></a>Vea también  
 [lightweight pooling (opción de configuración del servidor)](lightweight-pooling-server-configuration-option.md)   
 [Opciones de configuración de servidor &#40;SQL Server&#41;](server-configuration-options-sql-server.md)   
 [sp_configure &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-configure-transact-sql)   
 [lightweight pooling (opción de configuración del servidor)](lightweight-pooling-server-configuration-option.md)  
  
  
