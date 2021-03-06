---
title: Conjunto de filas MDSCHEMA_CUBES | Documentos de Microsoft
ms.date: 05/03/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: schema-rowsets
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: da0fc34fedcd6980f8dd19e199314fc1295c78bb
ms.sourcegitcommit: c12a7416d1996a3bcce3ebf4a3c9abe61b02fb9e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/10/2018
ms.locfileid: "34037076"
---
# <a name="mdschemacubes-rowset"></a>Conjunto de filas MDSCHEMA_CUBES
[!INCLUDE[ssas-appliesto-sqlas](../../../includes/ssas-appliesto-sqlas.md)]
  Describe la estructura de cubos dentro de una base de datos.  
  
## <a name="rowset-columns"></a>Columnas del conjunto de filas  
 El conjunto de filas **MDSCHEMA_CUBES** contiene las siguientes columnas.  
  
|Nombre de columna|Indicador de tipo|Description|  
|-----------------|--------------------|-----------------|  
|**CATALOG_NAME**|**DBTYPE_WSTR**|El nombre de la base de datos.|  
|**SCHEMA_NAME**|**DBTYPE_WSTR**|No compatible.|  
|**RESTRICCIONES OBLIGATORIAS CUBE_NAME**|**DBTYPE_WSTR**|Nombre del cubo o de la dimensión. Un símbolo del signo de dólar ($) prologa los nombres de la dimensión.<br /><br /> Nota: Solo los administradores de base de datos y servidor tienen permisos para ver cubos creados a partir de una dimensión.|  
|**CUBE_TYPE**|**DBTYPE_WSTR**|El tipo de cubo. Los valores válidos son:<br /><br /> **CUBO**<br /><br /> **DIMENSIÓN**|  
|**CUBE_GUID**|**DBTYPE_GUID**|No compatible.|  
|**CREATED_ON**|**DBTYPE_DBTIMESTAMP**|No compatible.|  
|**LAST_SCHEMA_UPDATE**|**DBTYPE_DBTIMESTAMP**|Muestra la última vez que se procesó el cubo.|  
|**SCHEMA_UPDATED_BY**|**DBTYPE_WSTR**|No compatible.|  
|**LAST_DATA_UPDATE**|**DBTYPE_DBTIMESTAMP**|Muestra la última vez que se procesó el cubo.|  
|**DATA_UPDATED_BY**|**DBTYPE_WSTR**|No compatible.|  
|**DESCRIPTION**|**DBTYPE_WSTR**|Descripción del nodo fácil de comprender.|  
|**IS_DRILLTHROUGH_ENABLED**|**DBTYPE_BOOL**|Un valor booleano que siempre devuelve un valor verdadero.|  
|**IS_LINKABLE**|**DBTYPE_BOOL**|Un valor booleano que indica si un cubo se puede utilizar en un cubo vinculado.|  
|**IS_WRITE_ENABLED**|**DBTYPE_BOOL**|Un valor booleano que indica si un cubo tiene permiso de escritura.|  
|**IS_SQL_ENABLED**|**DBTYPE_BOOL**|Un valor booleano que indica si se puede utilizar SQL en el cubo.|  
|**CUBE_CAPTION**|**DBTYPE_WSTR**|El título del cubo.|  
|**BASE_CUBE_NAME**|**DBTYPE_WSTR**|El nombre del cubo de origen si este cubo es un cubo de perspectiva.|  
|**ANOTACIONES**|**DBTYPE_WSTR**|(Opcional) Conjunto de notas en formato XML.|  
  
 El conjunto de filas se ordena en **CATALOG_NAME**, **SCHEMA_NAME**, **CUBE_NAME**.  
  
## <a name="restriction-columns"></a>Columnas de restricción  
 El conjunto de filas **MDSCHEMA_CUBES** puede tener restricciones en las columnas que se muestran en la tabla siguiente.  
  
|Nombre de columna|Indicador de tipo|Estado de restricción|  
|-----------------|--------------------|-----------------------|  
|**CATALOG_NAME**|**DBTYPE_WSTR**|Opcional.|  
|**SCHEMA_NAME**|**DBTYPE_WSTR**|Opcional.|  
|**RESTRICCIONES OBLIGATORIAS CUBE_NAME**|**DBTYPE_WSTR**|Opcional.|  
|**CUBE_SOURCE**|**DBTYPE_UI2**|(Opcional) La restricción predeterminada es un valor de 1. Un mapa de bits con uno de estos valores válidos:<br /><br /> 1 CUBO<br /><br /> 2 DIMENSIÓN|  
|**Base restricciones obligatorias Cube_Name**|**DBTYPE_WSTR**|Opcional.|  
  
## <a name="see-also"></a>Vea también  
 [OLE DB para OLAP Schema Rowsets](../../../analysis-services/schema-rowsets/ole-db-olap/ole-db-for-olap-schema-rowsets.md)  
  
  
