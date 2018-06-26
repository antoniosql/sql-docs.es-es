---
title: Otros problemas de actualización de motor de base de datos | Documentos de Microsoft
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
- Database Engine [SQL Server], upgrading
ms.assetid: 78a1d8e8-fa97-476f-8777-84617d145340
caps.latest.revision: 42
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: b1c74bf4ffd8cf0eba5cb853cccda80cc0b5d662
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/19/2018
ms.locfileid: "36103475"
---
# <a name="other-database-engine-upgrade-issues"></a>Otros problemas de actualización del motor de base de datos
  La versión actual del Asesor de actualizaciones no podrá detectar los siguientes problemas de actualización. Examine los problemas enumerados a continuación para evaluar su posible impacto en los sistemas.  
  
## <a name="multiple-database-engine-deprecated-features"></a>Varias características desusadas del motor de base de datos  
 Las siguientes instrucciones u opciones de [!INCLUDE[tsql](../../includes/tsql-md.md)] están en desuso:  
  
-   Las opciones NO_LOG y TRUNCATE_ONLY de BACKUP LOG  
  
-   BACKUP TRANSACTION   
  
-   RESTORE TRANSACTION  
  
-   DUMP  
  
-   LOAD  
  
-   DBCC CONCURRENCYVIOLATION  
  
-   sp_addalias  
  
-   sp_addgroup  
  
-   sp_changegroup  
  
-   sp_dropgroup  
  
-   sp_helpgroup  
  
-   syssegments  
  
 El uso del protocolo VIA para conectarse a [!INCLUDE[ssDE](../../includes/ssde-md.md)] está desusado.  
  
## <a name="new-data-types"></a>Nuevos tipos de datos  
 Los siguientes son los tipos del sistema reservados. Cambie el nombre de los tipos definidos por el usuario que entran en conflicto, ya sea antes o después de llevar a cabo la actualización.  
  
-   Geografía  
  
-   Geometría  
  
-   Datetime2  
  
-   HierarchyID  
  
## <a name="target-table-of-the-output-into-clause-cannot-have-any-defined-triggers"></a>La tabla de destino de la cláusula OUTPUT INTO no puede tener ningún desencadenador definido  
 No se admite el uso de OUPUT INTO en una tabla de destino cuando la tabla tiene algún desencadenador habilitado.  
  
## <a name="compile-time-error-for-udfs-when-the-target-of-an-output-into-clause-is-a-table"></a>Error en tiempo de compilación con los UDF cuando el destino de una cláusula OUTPUT INTO sea una tabla  
 Las funciones definidas por el usuario (UDF) no se pueden utilizar para realizar acciones que modifiquen el estado de la base de datos. Por ejemplo, un UDF no puede realizar ninguna acción DDL (CREATE/ALTER/DROP) o DML (INSERT/UPDATE/DELETE) sobre ningún objeto, excepto para variables de tabla.  
  
## <a name="merge-is-a-reserved-keyword"></a>MERGE es una palabra clave reservada.  
 MERGE es ahora una palabra clave totalmente reservada. Las aplicaciones ya no pueden tener objetos (tablas, columnas, etc.) denominados MERGE.  
  
## <a name="rename-cdc-schema"></a>Cambiar el nombre del esquema CDC  
 Hay un nombre de esquema denominado CDC. Este nombre de esquema no se puede utilizar si **captura de datos modificados** está habilitada para la base de datos.  
  
 Debe quitar el esquema CDC antes de habilitar **captura de datos modificados** para la base de datos. Este paso se puede hacer antes o después de la actualización. Para eliminar el esquema, siga los pasos que se detallan a continuación:  
  
1.  Transfiera los objetos del esquema CDC a un nuevo nombre de esquema utilizando ALTER SCHEMA.  
  
2.  Compruebe los permisos para los objetos en el nuevo esquema.  
  
3.  Realice las modificaciones necesarias en la aplicación.  
  
4.  Elimine el esquema CDC utilizando DROP SCHEMA.  
  
## <a name="see-also"></a>Vea también  
 [Problemas de actualización de motor de base de datos](../../../2014/sql-server/install/database-engine-upgrade-issues.md)  
  
  