---
title: Declarar la aplicación&#39;s versión de ODBC | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- declaring ODBC version [ODBC]
- data sources [ODBC], declaring ODBC version
- ODBC drivers [ODBC], declaring ODBC version
- connecting to driver [ODBC], declaring ODBC version
- connecting to data source [ODBC], declaring ODBC version
- version declaration [ODBC]
ms.assetid: 083a1ef5-580a-4979-9cf3-50f4549a080a
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: cd212f45e02ddce4c64a8b4a7d664ddaedf8090a
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/01/2018
ms.locfileid: "47666833"
---
# <a name="declaring-the-application39s-odbc-version"></a>Declarar la aplicación&#39;s versión de ODBC
Antes de que una aplicación asigna una conexión, se debe establecer el atributo de entorno SQL_ATTR_ODBC_VERSION. Este atributo indica que la aplicación sigue el 2 de ODBC. *x* u ODBC 3. *x* especificación al usar los siguientes elementos:  
  
-   **SQLSTATE**. Muchos de los valores SQLSTATE son diferentes en ODBC 2. *x* y ODBC 3. *x*.  
  
-   **Fecha, hora y los identificadores de tipo de marca de tiempo**. La siguiente tabla muestra los identificadores de tipo de fecha, hora y datos de marca de tiempo de ODBC 2. *x* y ODBC 3. *x*.  
  
    |ODBC 2. *x*|ODBC 3. *x*|  
    |----------------|----------------|  
    |**Identificadores de tipo SQL**||  
    |SQL_DATE|SQL_TYPE_DATE|  
    |SQL_TIME|SQL_TYPE_TIME|  
    |SQL_TIMESTAMP|SQL_TYPE_TIMESTAMP|  
    |**Identificadores de tipo C**||  
    |SQL_C_DATE|SQL_C_TYPE_DATE|  
    |SQL_C_TIME|SQL_C_TYPE_TIME|  
    |SQL_C_TIMESTAMP|SQL_C_TYPE_TIMESTAMP|  
  
-   *CatalogName***argumento en SQLTables**.   En ODBC 2. *x*, los caracteres comodín ("%" y "_") en el *CatalogName* argumento se tratan literalmente. En ODBC 3. *x*, se tratan como caracteres comodín. Por lo tanto, una aplicación que sigue a la API ODBC 2. *x* especificación no puede utilizar tal y como caracteres comodín y no realiza escape de ellos cuando se usen como literales. Una aplicación que sigue el ODBC 3. *x* especificación puede usarlas como caracteres comodín o ponerlos y usarlos como literales. Para obtener más información, consulte [argumentos en funciones de catálogo](../../../odbc/reference/develop-app/arguments-in-catalog-functions.md).  
  
 El 3 de ODBC *.x* mientras que el Administrador de controladores ODBC 3 *.x* controladores comprobar la versión de la especificación de ODBC que se escribe una aplicación y responder según corresponda. Por ejemplo, si la aplicación sigue a la API ODBC 2. *x* especificación y llama a **SQLExecute** antes de llamar a **SQLPrepare**, el 3 de ODBC *.x* Administrador de controladores devuelve SQLSTATE S1010 () Error de secuencia de función). Si la aplicación sigue el ODBC 3 *.x* especificación, el Administrador de controladores devuelve SQLSTATE HY010 (función de error de secuencia). Para obtener más información, consulte [compatibilidad con versiones anteriores y el cumplimiento de estándares](../../../odbc/reference/develop-app/backward-compatibility-and-standards-compliance.md).  
  
> [!IMPORTANT]  
>  Aplicaciones que siguen el ODBC 3. *x* especificación debe utilizar código condicional para evitar el uso de la funcionalidad nueva a ODBC 3. *x* al trabajar con ODBC 2. *x* controladores. ODBC 2. *x* controladores no admiten la funcionalidad nueva a ODBC 3. *x* simplemente porque la aplicación declara que sigue el ODBC 3. *x* especificación. Además, ODBC 3. *x* no dejan de controladores admitir la funcionalidad nueva a ODBC 3. *x* simplemente porque la aplicación declara que sigue a la API ODBC 2. *x* especificación.
