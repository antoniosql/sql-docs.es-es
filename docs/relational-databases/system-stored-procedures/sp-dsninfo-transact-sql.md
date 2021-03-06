---
title: sp_dsninfo (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 03/04/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology:
- replication
ms.topic: language-reference
f1_keywords:
- sp_dsninfo
- sp_dsninfo_TSQL
helpviewer_keywords:
- sp_dsninfo
ms.assetid: 34648615-814b-42bc-95a3-50e86b42ec4d
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 93b8fb31c89d48a3281e5d5b102e94f95e5f2855
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/01/2018
ms.locfileid: "47828181"
---
# <a name="spdsninfo-transact-sql"></a>sp_dsninfo (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Devuelve información del origen de datos ODBC u OLE DB tomada del distribuidor asociado con el servidor actual. Este procedimiento almacenado se ejecuta en el distribuidor de cualquier base de datos.  
  
 ![Icono de vínculo de tema](../../database-engine/configure-windows/media/topic-link.gif "Icono de vínculo de tema") [Convenciones de sintaxis de Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Sintaxis  
  
```  
  
sp_dsninfo [ @dsn =] 'dsn'   
    [ , [ @infotype =] 'info_type']   
    [ , [ @login =] 'login']   
    [ , [ @password =] 'password']  
    [ , [ @dso_type=] dso_type]  
```  
  
## <a name="arguments"></a>Argumentos  
 [  **@dsn =**] **'***dsn***'**  
 Es el nombre del DSN ODBC o del servidor vinculado OLE DB. *DSN* es **varchar (128)**, no tiene ningún valor predeterminado.  
  
 [  **@infotype =**] **'***tipo_de_info***'**  
 Es el tipo de información que se va a devolver. Si *tipo_de_info* no se especifica o si se especifica NULL, se devuelven todos los tipos de información. *tipo_de_info* es **varchar (128)**, su valor predeterminado es null, y puede tener uno de estos valores.  
  
|Valor|Descripción|  
|-----------|-----------------|  
|**DBMS_NAME**|Especifica el nombre del proveedor del origen de datos.|  
|**DBMS_VERSION**|Especifica la versión del origen de datos.|  
|**DATABASE_NAME**|Especifica el nombre de la base de datos.|  
|**O SQL_SUBSCRIBER**|Especifica que el origen de datos puede ser un suscriptor.|  
  
 [  **@login =**] **'***inicio de sesión***'**  
 Es el nombre de inicio de sesión del origen de datos. Si el origen de datos incluye un inicio de sesión, especifique NULL u omita el parámetro. *inicio de sesión*es **varchar (128)**, su valor predeterminado es null.  
  
 [  **@password =**] **'***contraseña***'**  
 Es la contraseña del inicio de sesión. Si el origen de datos incluye un inicio de sesión, especifique NULL u omita el parámetro. *contraseña*es **varchar (128)**, su valor predeterminado es null.  
  
 [  **@dso_type=**] *dso_type*  
 Es el tipo del origen de datos. *dso_type* es **int**, y puede tener uno de estos valores.  
  
|Valor|Descripción|  
|-----------|-----------------|  
|**1** (predeterminado)|Origen de datos ODBC|  
|**3**|Origen de datos OLE DB|  
  
## <a name="return-code-values"></a>Valores de código de retorno  
 **0** (correcto) o **1** (error)  
  
## <a name="result-sets"></a>Conjuntos de resultados  
  
|Nombre de columna|Tipo de datos|Descripción|  
|-----------------|---------------|-----------------|  
|**Tipo de información**|**Nvarchar (64)**|Tipos de información, como DBMS_NAME, DBMS_VERSION, DATABASE_NAME o SQL_SUBSCRIBER.|  
|**Valor**|**nvarchar(512)**|Valor del tipo de información asociado.|  
  
## <a name="remarks"></a>Comentarios  
 **sp_dsninfo** se utiliza en todos los tipos de replicación.  
  
 **sp_dsninfo** recupera información origen de datos ODBC u OLE DB que se muestra si se puede usar la base de datos para replicación o consultas.  
  
## <a name="permissions"></a>Permisos  
 Solo los miembros de la **sysadmin** rol fijo de servidor puede ejecutar **sp_dsninfo**.  
  
## <a name="see-also"></a>Vea también  
 [sp_enumdsn &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-enumdsn-transact-sql.md)   
 [Procedimientos almacenados del sistema &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
