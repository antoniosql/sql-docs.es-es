---
title: Conjunto de filas DBSCHEMA_PROVIDER_TYPES | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- analysis-services
- docset-sql-devref
ms.topic: reference
api_name:
- DBSCHEMA_PROVIDER_TYPES
topic_type:
- apiref
helpviewer_keywords:
- DBSCHEMA_PROVIDER_TYPES rowset
ms.assetid: 255e01ba-53a9-478d-9b86-45faba76710e
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 2840e67e8ddb1b412164bacc6c26ff9ac0c90e10
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/02/2018
ms.locfileid: "48049195"
---
# <a name="dbschemaprovidertypes-rowset"></a>Conjunto de filas DBSCHEMA_PROVIDER_TYPES
  Identifica los tipos de datos (básicos) admitidos por el proveedor de datos.  
  
## <a name="rowset-columns"></a>Columnas del conjunto de filas  
 El `DBSCHEMA_PROVIDER_TYPES` conjunto de filas contiene las siguientes columnas.  
  
|Nombre de columna|Indicador de tipo|Longitud|Descripción|  
|-----------------|--------------------|------------|-----------------|  
|`TYPE_NAME`|`DBTYPE_WSTR`||El nombre del tipo de datos específico del proveedor.|  
|`DATA_TYPE`|`DBTYPE_UI2`||Indicador de tipo de datos.|  
|`COLUMN_SIZE`|`DBTYPE_UI4`||La longitud de una columna no numérica o parámetro que hace referencia al máximo o la longitud definida para este tipo por el proveedor. Para los datos del carácter, ésta es la longitud máxima o definida en caracteres. Para los tipos de datos DateTime, ésta es la longitud de la representación de cadena (suponiendo la precisión máxima permitida del componente de fracciones de segundo).<br /><br /> Si el tipo de datos es numérico, se corresponde al límite superior de la precisión máxima del tipo de datos.|  
|`LITERAL_PREFIX`|`DBTYPE_WSTR`||El carácter o caracteres utilizados para prefijar un literal de este tipo en un comando de texto.|  
|`LITERAL_SUFFIX`|`DBTYPE_WSTR`||El carácter o caracteres utilizados como sufijo de un literal de este tipo en un comando de texto.|  
|`CREATE_PARAMS`|`DBTYPE_WSTR`||Los parámetros de creación especificados por el consumidor al crear una columna de este tipo de datos. Por ejemplo, el tipo de datos SQL, `DECIMAL,` necesita una precisión y una escala. En este caso, los parámetros de creación podrían ser la cadena la "precisión, escala." En un comando de texto, para crear una columna `DECIMAL` con una precisión de 10 y una escala de 2, el valor de la columna `TYPE_NAME` podría ser `DECIMAL()` y la especificación de tipo completa sería `DECIMAL(10,2)`.<br /><br /> Los parámetros de creación aparecen como una lista separada por comas de valores, en el orden que se proporcionarán y sin estar entre paréntesis. Si un parámetro de creación es longitud, longitud máxima, precisión, escala, semilla o incremento, utilice la "longitud", "longitud del máximo", "precisión", "escala", "inicialización" e "incremento", respectivamente. Si el parámetro de creación es algún otro valor, el proveedor determina el texto que se utilizará para describir el parámetro de creación.<br /><br /> Si el tipo de datos requiere los parámetros de creación, "()" aparece normalmente en el nombre de tipo. Esto indica la posición en la que se insertarán los parámetros de creación. Si el nombre de tipo no incluye "()", los parámetros de creación se colocan entre paréntesis y anexan al nombre del tipo de datos.|  
|`IS_NULLABLE`|`DBTYPE_BOOL`||Un booleano que indica si el tipo de datos admite valores NULL.<br /><br /> `VARIANT_TRUE` indica que el tipo de datos admite valores NULL.<br /><br /> `VARIANT_FALSE` indica que el tipo de datos no admite valores NULL.<br /><br /> `NULL` indica que no se conoce si el tipo de datos admite valores NULL.|  
|`CASE_SENSITIVE`|`DBTYPE_BOOL`||Un booleano que indica si el tipo de datos es un tipo de caracteres y con distinción entre mayúsculas y minúsculas.<br /><br /> `VARIANT_TRUE` indica que el tipo de datos es un tipo de caracteres y distingue entre mayúsculas y minúsculas.<br /><br /> `VARIANT_FALSE` indica que el tipo de datos no es un tipo de caracteres o no distingue entre mayúsculas y minúsculas.|  
|`SEARCHABLE`|`DBTYPE_UI4`||Un entero que indica cómo el tipo de datos se puede utilizar en búsquedas si el proveedor admite `ICommandText`; en caso contrario, `NULL`.<br /><br /> Esta columna admite cualquiera de los siguientes valores:<br /><br /> -   `DB_UNSEARCHABLE` indica que no se puede usar el tipo de datos en un `WHERE` cláusula.<br />-   `DB_LIKE_ONLY` indica que se puede utilizar el tipo de datos en un `WHERE` cláusula sólo con el `LIKE` predicado.<br />-   `DB_ALL_EXCEPT_LIKE` indica que se puede utilizar el tipo de datos en un `WHERE` cláusula con todos los operadores de comparación excepto `LIKE`.<br />-   `DB_SEARCHABLE` indica que se puede utilizar el tipo de datos en un `WHERE` cláusula con cualquier operador de comparación.|  
|`UNSIGNED_ATTRIBUTE`|`DBTYPE_BOOL`||Un booleano que indica si el tipo de datos es sin signo.<br /><br /> `VARIANT_TRUE` indica que el tipo de datos es sin signo.<br /><br /> `VARIANT_FALSE` indica que el tipo de datos es con signo.<br /><br /> `NULL` indica que esto no es aplicable al tipo de datos.|  
|`FIXED_PREC_SCALE`|`DBTYPE_BOOL`||Un booleano que indica si el tipo de datos tiene una precisión y escala fijas.<br /><br /> `VARIANT_TRUE` indica que el tipo de datos tiene una precisión y escala fijas.<br /><br /> `VARIANT_FALSE` indica que el tipo de datos no tiene ninguna precisión y escala fijas.|  
|`AUTO_UNIQUE_VALUE`|`DBTYPE_BOOL`||Un booleano que indica si el tipo de datos aumenta automáticamente.<br /><br /> `VARIANT_TRUE` indica que los valores de este tipo pueden estar incrementando automáticamente.<br /><br /> `VARIANT_FALSE` indica que los valores de este tipo no pueden aumentar automáticamente.<br /><br /> Si este valor es `VARIANT_TRUE`, si una columna o no de este tipo siempre aumenta automáticamente depende de la propiedad de columna `DBPROP_COL_AUTOINCREMENT` del proveedor. Si la propiedad `DBPROP_COL_AUTOINCREMENT` es de lectura/escritura, el aumento automático de una columna de este tipo depende del valor de la propiedad `DBPROP_COL_AUTOINCREMENT`. Si `DBPROP_COL_AUTOINCREMENT` es una propiedad de solo lectura, todas o ninguna de las columnas de este tipo aumentan automáticamente.|  
|`LOCAL_TYPE_NAME`|`DBTYPE_WSTR`||La versión localizada de `TYPE_NAME`. Se devuelve `NULL` si el proveedor de datos no admite un nombre traducido.|  
|`MINIMUM_SCALE`|`DBTYPE_I2`||Si el indicador de tipo es `DBTYPE_VARNUMERIC`, `DBTYPE_DECIMAL`, o `DBTYPE_NUMERIC`, el número de dígitos que se encuentran a la derecha del separador decimal. En caso contrario, `NULL`.|  
|`MAXIMUM_SCALE`|`DBTYPE_I2`||Si el indicador de tipo es `DBTYPE_VARNUMERIC`, `DBTYPE_DECIMAL`, o `DBTYPE_NUMERIC`; en caso contrario, es N`U`LL.|  
|`GUID`|`DBTYPE_GUID`||(Se piensa para el uso futuro) `GUID` del tipo, si el tipo se describe en una biblioteca de tipos. En caso contrario, `NULL`.|  
|`TYPELIB`|`DBTYPE_WSTR`||(Se piensa para el uso futuro) La biblioteca de tipos que contiene la descripción del tipo, si el tipo se describe en una biblioteca de tipos. En caso contrario, NULL.|  
|`VERSION`|`DBTYPE_WSTR`||(Se piensa para el uso futuro) La versión de la definición de tipo. Los proveedores podrían desear controlar las versiones de las definiciones de tipo. Proveedores diferentes podrían utilizar esquemas de versiones diferentes, como una marca de tiempo o número (entero o flotante). `NULL` si no se admite.|  
|`IS_LONG`|`DBTYPE_BOOL`||Un booleano que indica si el tipo de datos es un objeto binario grande (BLOB) y tiene los datos muy largos.<br /><br /> `VARIANT_TRUE` indica que el tipo de datos es un `BLOB` que contiene datos muy largos; la definición de datos muy largos depende del proveedor.<br /><br /> `VARIANT_FALSE` indica que el tipo de datos es un `BLOB` que no contiene los datos muy largos o no es un `BLOB`.<br /><br /> Este valor determina el valor de la marca `DBCOLUMNFLAGS_ISLONG` devuelto por `GetColumnInfo` en `IColumnsInfo` y `GetParameterInfo` en `ICommandWithParameters`.|  
|`BEST_MATCH`|`DBTYPE_BOOL`||Un booleano que indica si el tipo de datos es una coincidencia mejor.<br /><br /> `VARIANT_TRUE` indica que el tipo de datos es la mejor coincidencia de entre todos los tipos de datos del almacén de datos y el tipo de datos de OLE DB indicado por el valor de la columna `DATA_TYPE`.<br /><br /> `VARIANT_FALSE` indica que el tipo de datos no es la coincidencia mejor.<br /><br /> Para cada conjunto de filas en que el valor de la columna `DATA_TYPE` es el mismo, la columna `BEST_MATCH` se define en `VARIANT_TRUE` en una sola fila.|  
|`IS_FIXEDLENGTH`|`DBTYPE_BOOL`||Un booleano que indica si la columna es fija en longitud.<br /><br /> `VARIANT_TRUE` indica que las columnas de este tipo creadas por el lenguaje de definición de datos (DDL) serán de la longitud fija.<br /><br /> `VARIANT_FALSE` indica que las columnas de este tipo creadas por el DDL serán de longitud variable.<br /><br /> Si el campo es `NULL`, no se conoce si el proveedor asignará este campo con una columna de longitud fija o de longitud variable.|  
  
 El conjunto de filas se ordena en `DATA_TYPE`.  
  
## <a name="restriction-columns"></a>Columnas de restricción  
 El `DBSCHEMA_PROVIDER_TYPES` conjunto de filas puede tener restricciones en las columnas enumeradas en la tabla siguiente.  
  
|Nombre de columna|Indicador de tipo|Estado de restricción|  
|-----------------|--------------------|-----------------------|  
|`DATA_TYPE`|`DBTYPE_UI2`||  
|`BEST_MATCH`|`DBTYPE_BOOL`||  
  
## <a name="see-also"></a>Vea también  
 [Conjuntos de filas de esquema OLE DB](ole-db-schema-rowsets.md)  
  
  
