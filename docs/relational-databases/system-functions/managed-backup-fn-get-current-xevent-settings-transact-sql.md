---
title: managed_backup.fn_get_current_xevent_settings (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 06/10/2016
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- fn_get_current_xevent_settings
- smart_admin.fn_get_current_xevent_settings_TSQL
- fn_get_current_xevent_settings_TSQL
- smart_admin.fn_get_current_xevent_settings
dev_langs:
- TSQL
helpviewer_keywords:
- smart_admin.fn_get_current_xevent_settings
- fn_get_current_xevent_settings
ms.assetid: 95d3adaa-bb9d-4833-b8b4-3d9fd4f9c82a
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.openlocfilehash: 1fa350d9ff9d5e90eb595f1f693b8e62a46fa555
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/01/2018
ms.locfileid: "47741063"
---
# <a name="managedbackupfngetcurrentxeventsettings-transact-sql"></a>managed_backup.fn_get_current_xevent_settings (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2016-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2016-xxxx-xxxx-xxx-md.md)]

  Devuelve una fila para cada tipo de evento extendido compatible con Administración inteligente.  
  
 Utilice esta función para devolver o revisar la configuración de eventos extendidos para identificar el tipo de evento configurable y las configuraciones actuales.  
  
 ![Icono de vínculo de tema](../../database-engine/configure-windows/media/topic-link.gif "Icono de vínculo de tema") [Convenciones de sintaxis de Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Sintaxis  
  
```sql  
smart_admin.fn_get_current_xevent_settings ()   
```  
  
##  <a name="Arguments"></a> Argumentos  
 Esta función no tiene argumentos.  
  
## <a name="table-returned"></a>Tabla devuelta  
 Los canales de administración, análisis y operativos de Eventos extendidos son necesarios, están habilitados de manera predeterminada y no son configurables.  
  
|Nombre de la columna|Tipo de datos|Descripción|  
|-----------------|---------------|-----------------|  
|Event_name|NVARCHAR(128)|Tipo de evento extendido|  
|is_configurable|NVARCHAR(128)|Se establece en **True** si el evento es configurable, lo contrario, establece en **False**.|  
|is_enabled|NVARCHAR(128)|Se establece en True si el evento está habilitado y en False si no lo está. Utilice smart_admin.sp_set_parameter para habilitar eventos de depuración.|  
  
## <a name="security"></a>Seguridad  
  
### <a name="permissions"></a>Permisos  
 Requiere **seleccione** permisos en la función.  
  
## <a name="examples"></a>Ejemplos  
 El ejemplo siguiente devuelve todos los eventos extendidos con su estado actual.  
  
```  
SELECT *   
FROM smart_admin.fn_get_current_xevent_settings ()  
  
```  
  
  
