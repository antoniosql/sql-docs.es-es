---
title: MSSQLSERVER_1406 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- 1406 (Database Engine error)
ms.assetid: 915f97de-9b74-41f8-8bd5-b2d061416718
caps.latest.revision: 15
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: 259d6e37f0798cfacaac39c89dec091053c16c57
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/19/2018
ms.locfileid: "36106781"
---
# <a name="mssqlserver1406"></a>MSSQLSERVER_1406
    
## <a name="details"></a>Detalles  
  
|||  
|-|-|  
|Nombre del producto|SQL Server|  
|Identificador del evento|1406|  
|Origen del evento|MSSQLSERVER|  
|Componente|SQLEngine|  
|Nombre simbólico|DBM_BADSTATEFORFORCESERVICE|  
|Texto del mensaje|No se puede forzar el servicio de forma segura. Quite el reflejo de la base de datos y recupere la base de datos "%.*ls" para obtener acceso.|  
  
## <a name="explanation"></a>Explicación  
 El [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] no puede forzar el servicio porque el estado de creación de reflejo no puede garantizar que el proceso de forzar el servicio funcione correctamente.  
  
## <a name="user-action"></a>Acción del usuario  
 Quite el reflejo de la base de datos. Después, puede recuperar la base de datos reflejada para obtener acceso a ella.  
  
## <a name="see-also"></a>Vea también  
 [Forzar el servicio en una sesión de creación de reflejo de la base de datos &#40;Transact-SQL&#41;](../../database-engine/database-mirroring/force-service-in-a-database-mirroring-session-transact-sql.md)   
 [Quitar la creación de reflejo de la base de datos &#40;SQL Server&#41;](../../database-engine/database-mirroring/database-mirroring-sql-server.md)  
  
  