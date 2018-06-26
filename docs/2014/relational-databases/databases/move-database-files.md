---
title: Movimiento de archivos de base de datos | Microsoft Docs
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
- disaster recovery [SQL Server], moving database files
- files [SQL Server], moving
- data files [SQL Server], moving
- file moving [SQL Server]
- moving full-text catalogs
- moving databases
- full-text catalogs [SQL Server], moving
- moving database files
- scheduled disk maintenance [SQL Server]
- moving files
- relocating database files
- planned database relocations [SQL Server]
- databases [SQL Server], moving
ms.assetid: 89f01b10-5fae-4ed8-b0fb-a4b9f540fd28
caps.latest.revision: 33
author: craigg-msft
ms.author: craigg
manager: jhubbard
ms.openlocfilehash: fc0f4981ea6a1dab4d1cc687547738abc0d9a038
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/19/2018
ms.locfileid: "36110713"
---
# <a name="move-database-files"></a>Mover archivos de base de datos
  En [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], puede mover bases de datos del sistema y del usuario especificando la nueva ubicación de los archivos en la cláusula FILENAME de la instrucción [ALTER DATABASE](/sql/t-sql/statements/alter-database-transact-sql) . De este modo se pueden desplazar archivos de datos, registro y catálogo de texto completo. Esto puede resultar útil en las situaciones siguientes:  
  
-   Recuperación de un error. Por ejemplo, la base de datos se encuentra en modo sospechoso o se ha cerrado a causa de un error de hardware.  
  
-   Reubicación planeada.  
  
-   Reubicación para el mantenimiento planeado del disco.  
  
## <a name="in-this-section"></a>En esta sección  
  
|Tema|Descripción|  
|-----------|-----------------|  
|[Mover bases de datos de usuario](move-user-databases.md)|Describe los procedimientos para mover archivos de base de datos de usuario y archivos del catálogo de texto completo a una nueva ubicación.|  
|[Mover bases de datos del sistema](system-databases.md)|Describe el procedimiento para mover archivos de base de datos del sistema a una nueva ubicación.|  
  
## <a name="see-also"></a>Vea también  
 [ALTER DATABASE &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-database-transact-sql)   
 [CREATE DATABASE &#40;Transact-SQL de SQL Server&#41;](/sql/t-sql/statements/create-database-sql-server-transact-sql)   
 [Adjuntar y separar bases de datos &#40;SQL Server&#41;](database-detach-and-attach-sql-server.md)  
  
  