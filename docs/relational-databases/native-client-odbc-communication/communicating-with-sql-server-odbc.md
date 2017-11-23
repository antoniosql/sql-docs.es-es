---
title: Comunicar con SQL Server (ODBC) | Documentos de Microsoft
ms.custom: 
ms.date: 03/16/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.service: 
ms.component: native-client-odbc-communication
ms.reviewer: 
ms.suite: sql
ms.technology: docset-sql-devref
ms.tgt_pltfrm: 
ms.topic: reference
helpviewer_keywords:
- SQL Server Native Client ODBC driver, communicating with SQL Server
- ODBC applications, communicating with SQL Server
- ODBC, communicating with SQL Server
ms.assetid: cca3dcf0-2a7e-465a-84de-7ce055360eb6
caps.latest.revision: "34"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: On Demand
ms.openlocfilehash: dc4fb8f8483aaf97838db03f81ad7643cf413bc4
ms.sourcegitcommit: 44cd5c651488b5296fb679f6d43f50d068339a27
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/17/2017
---
# <a name="communicating-with-sql-server-odbc"></a>Comunicar con SQL Server (ODBC)
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]
[!INCLUDE[SNAC_Deprecated](../../includes/snac-deprecated.md)]

  Para una aplicación ODBC para comunicarse con una instancia de [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], debe asignar el entorno y conexión controla y conectarse al origen de datos. Una vez establecida una conexión, la aplicación puede enviar consultas al servidor y procesar cualquier conjunto de resultados. Cuando la aplicación ha terminado de usar el origen de datos, se desconecta del origen de datos y libera el identificador de conexión. Cuando la aplicación ha liberado todos sus identificadores de conexión, libera el identificador del entorno.  
  
 Una aplicación puede conectarse a cualquier número de orígenes de datos. La aplicación puede usar una combinación de controladores y orígenes de datos, el mismo controlador y una combinación de orígenes de datos o incluso el mismo controlador y varias conexiones al mismo origen de datos.  
  
 Puede descargar [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ejemplos de ODBC de Native Client desde el [descargas de SQL Server](http://go.microsoft.com/fwlink/?LinkId=62796) página en MSDN.  
  
## <a name="in-this-section"></a>En esta sección  
  
-   [Asignar un identificador de entorno](../../relational-databases/native-client-odbc-communication/allocating-an-environment-handle.md)  
  
-   [Asignar un identificador de conexión](../../relational-databases/native-client-odbc-communication/allocating-a-connection-handle.md)  
  
-   [Orígenes de datos de ODBC para SQL Server Native Client](../../relational-databases/native-client-odbc-communication/sql-server-native-client-odbc-data-sources.md)  
  
-   [Conectarse a un origen de datos &#40; ODBC &#41;](../../relational-databases/native-client-odbc-communication/connecting-to-a-data-source-odbc.md)  
  
-   [Desconectarse de un origen de datos](../../relational-databases/native-client-odbc-communication/disconnecting-from-a-data-source.md)  
  
## <a name="see-also"></a>Vea también  
 [Cliente nativo de SQL Server &#40; ODBC &#41;](../../relational-databases/native-client/odbc/sql-server-native-client-odbc.md)   
 [SQLSetEnvAttr](../../relational-databases/native-client-odbc-api/sqlsetenvattr.md)  
  
  