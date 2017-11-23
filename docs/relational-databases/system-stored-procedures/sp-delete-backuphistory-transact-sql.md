---
title: sp_delete_backuphistory (Transact-SQL) | Documentos de Microsoft
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: system-stored-procedures
ms.reviewer: 
ms.suite: sql
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- sp_delete_backuphistory
- sp_delete_backuphistory_TSQL
dev_langs: TSQL
helpviewer_keywords: sp_delete_backuphistory
ms.assetid: bdb56834-616e-47e4-b942-e895d2325e97
caps.latest.revision: "31"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: On Demand
ms.openlocfilehash: 700c5a3849aea0fe2d1db07cc0cce96bdc8d7e7b
ms.sourcegitcommit: 66bef6981f613b454db465e190b489031c4fb8d3
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/17/2017
---
# <a name="spdeletebackuphistory-transact-sql"></a>sp_delete_backuphistory (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Reduce el tamaño de las tablas del historial de copias de seguridad y restauración eliminando las entradas de conjuntos de copias de seguridad anteriores a la fecha especificada. Filas adicionales se agregan a la copia de seguridad y restauración de las tablas de historial después de cada copia de seguridad o se realiza la operación de restauración; por lo tanto, se recomienda ejecutar periódicamente **sp_delete_backuphistory**.  
  
> [!NOTE]  
>  Las tablas de historial de copia de seguridad y restauración residen en el **msdb** base de datos.  
  
||  
|-|  
|**Se aplica a**: [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ([!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] a través de la [versión actual](http://go.microsoft.com/fwlink/p/?LinkId=299658)).|  
  
 ![Icono de vínculo de tema](../../database-engine/configure-windows/media/topic-link.gif "Icono de vínculo de tema") [Convenciones de sintaxis de Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Sintaxis  
  
```  
  
sp_delete_backuphistory [ @oldest_date = ] 'oldest_date'   
```  
  
## <a name="arguments"></a>Argumentos  
 [  **@oldest_date=** ] **'***oldest_date***'**  
 Es la fecha más antigua mantenida en las tablas del historial de copias de seguridad y restauración. *oldest_date* es **datetime**, no tiene ningún valor predeterminado.  
  
## <a name="return-code-values"></a>Valores de código de retorno  
 0 (correcto) o 1 (error)  
  
## <a name="result-sets"></a>Conjuntos de resultados  
 Ninguno  
  
## <a name="remarks"></a>Comentarios  
 **sp_delete_backuphistory** se debe ejecutar desde la **msdb** la base de datos y afecta a las tablas siguientes:  
  
-   [backupfile](../../relational-databases/system-tables/backupfile-transact-sql.md)  
  
-   [backupfilegroup](../../relational-databases/system-tables/backupfilegroup-transact-sql.md)  
  
-   [backupmediafamily](../../relational-databases/system-tables/backupmediafamily-transact-sql.md)  
  
-   [backupmediaset](../../relational-databases/system-tables/backupmediaset-transact-sql.md)  
  
-   [backupset](../../relational-databases/system-tables/backupset-transact-sql.md)  
  
-   [restorefile](../../relational-databases/system-tables/restorefile-transact-sql.md)  
  
-   [restorefilegroup](../../relational-databases/system-tables/restorefilegroup-transact-sql.md)  
  
-   [restorehistory](../../relational-databases/system-tables/restorehistory-transact-sql.md)  
  
 Los archivos de copia de seguridad físicos se conservan, aunque se elimine todo el historial.  
  
## <a name="permissions"></a>Permissions  
 Debe pertenecer a la **sysadmin** rol fijo de servidor, pero los permisos se pueden conceder a otros usuarios.  
  
## <a name="examples"></a>Ejemplos  
 En el ejemplo siguiente se eliminan todas las entradas anteriores al 14 de enero de 2010, 12:00 a. m. de las tablas de historial de copias de seguridad y restauración.  
  
```  
USE msdb;  
GO  
EXEC sp_delete_backuphistory @oldest_date = '01/14/2010';  
```  
  
## <a name="see-also"></a>Vea también  
 [sp_delete_database_backuphistory &#40; Transact-SQL &#41;](../../relational-databases/system-stored-procedures/sp-delete-database-backuphistory-transact-sql.md)   
 [Historial de copias de seguridad e información de encabezados &#40;SQL Server&#41;](../../relational-databases/backup-restore/backup-history-and-header-information-sql-server.md)  
  
  