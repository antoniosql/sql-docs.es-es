---
title: Frente a enlazado. Sin enlazar columnas Text e Image | Documentos de Microsoft
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.service: 
ms.component: native-client-odbc-text-image-columns
ms.reviewer: 
ms.suite: sql
ms.technology: docset-sql-devref
ms.tgt_pltfrm: 
ms.topic: reference
helpviewer_keywords:
- text columns [ODBC]
- SQL Server Native Client ODBC driver, image columns
- SQL Server Native Client ODBC driver, text columns
- data types [ODBC], image
- data types [ODBC], text
- columns [ODBC]
- ODBC data types, image columns
- ODBC data types, text columns
- image columns [ODBC]
ms.assetid: ffd3442e-d880-46e9-b848-2365a09a2406
caps.latest.revision: "29"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 44479d4350b43f4c38bf155d19ab03de19f8a159
ms.sourcegitcommit: 44cd5c651488b5296fb679f6d43f50d068339a27
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/17/2017
---
# <a name="bound-vs-unbound-text-and-image-columns"></a>Frente a enlazado. Columnas sin enlazar Text e Image
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]
[!INCLUDE[SNAC_Deprecated](../../includes/snac-deprecated.md)]

  Cuando se utilizan cursores de servidor, el [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] controlador ODBC Native Client está optimizado para no transmitir los datos sin delimitar **texto**, **ntext**, o **imagen** columnas en el momento de **SQLFetch** se lleva a cabo. El **texto**, **ntext**, o **imagen** datos no se recuperan realmente desde el servidor hasta que los problemas de aplicaciones [SQLGetData](../../relational-databases/native-client-odbc-api/sqlgetdata.md) para la columna.  
  
 Muchas aplicaciones se pueden escribir para que no **texto**, **ntext**, o **imagen** se muestran los datos mientras un usuario se desplaza hacia arriba y hacia abajo en un cursor. Cuando un usuario selecciona una fila para obtener más detalles, la aplicación, a continuación, puede llamar a **SQLGetData** para recuperar la **texto**, **ntext**, o **imagen** datos. Esto evitará que transmitir la **texto**, **ntext**, o **imagen** datos para cualquiera de las filas, el usuario no seleccione y, por tanto, evitar la transmisión de grandes cantidades de datos.  
  
## <a name="see-also"></a>Vea también  
 [Administrar columnas Text e Image](../../relational-databases/native-client-odbc-text-image-columns/managing-text-and-image-columns.md)   
 [Comportamientos de los cursores](../../relational-databases/native-client-odbc-cursors/cursor-behaviors.md)  
  
  