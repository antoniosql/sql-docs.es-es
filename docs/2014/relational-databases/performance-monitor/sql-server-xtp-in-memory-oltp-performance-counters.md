---
title: Contadores de rendimiento de XTP (OLTP en memoria) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: conceptual
ms.assetid: fe3cbaf4-65f4-44c5-acc6-7b735cda0c5d
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.openlocfilehash: 2362807e8e033fbc55e75a08d9dec80bf3782e03
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/02/2018
ms.locfileid: "48084055"
---
# <a name="xtp-in-memory-oltp-performance-counters"></a>Contadores de rendimiento de XTP (OLTP en memoria)
  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ofrece objetos y contadores que el Monitor de rendimiento puede usar para supervisar la actividad de OLTP en memoria.  
  
##  <a name="SQLServerPOs"></a> Objetos de rendimiento de XTP (OLTP en memoria)  
 En la tabla siguiente se describen los objetos de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .  
  
|Objeto de rendimiento|Descripción|  
|------------------------|-----------------|  
|[Cursores XTP](../cursors.md)|El objeto de rendimiento Cursores XTP contiene contadores relacionados con los cursores internos del motor de XTP. Los cursores son los bloques de creación de bajo nivel que el motor de XTP utiliza para procesar consultas de [!INCLUDE[tsql](../../includes/tsql-md.md)] . Por tanto, el usuario no tiene normalmente control directo sobre ellos.|  
|[Recolección de elementos no utilizados de XTP](sql-server-xtp-garbage-collection.md)|El objeto de rendimiento Recolección de elementos no utilizados de XTP contiene contadores relacionados con el recolector de elementos no utilizados del motor de XTP.|  
|[Procesador fantasma de XTP](sql-server-xtp-phantom-processor.md)|El objeto de rendimiento Procesador fantasma de XTP contiene contadores relacionados con el subsistema de procesamiento fantasma del motor de XTP. Este componente es responsable de detectar filas fantasma en transacciones que se ejecutan en el nivel de aislamiento SERIALIZABLE.|  
|[Almacenamiento XTP](sql-server-xtp-storage.md)|El objeto de rendimiento XTP Storage contiene contadores relacionados con el almacenamiento de XTP en [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].|  
|[Registro de transacciones XTP](sql-server-xtp-transaction-log.md)|El objeto de rendimiento Registro de transacciones XTP contiene contadores relacionados con el registro de transacciones XTP en [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].|  
|[Transacciones XTP](sql-server-xtp-transactions.md)|El objeto de rendimiento Transacciones XTP contiene contadores relacionados con las transacciones del motor de XTP en [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].|  
  
  
