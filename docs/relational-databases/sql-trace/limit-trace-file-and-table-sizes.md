---
title: "Limitar el tama&#241;o de la tabla y el archivo de seguimiento | Microsoft Docs"
ms.custom: ""
ms.date: "03/14/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "database-engine"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "tamaño máximo de archivo para seguimientos"
  - "seguimientos [SQL Server], tamaño de archivo"
  - "tamaño [SQL Server], tablas"
  - "sustitución incremental, opción [SQL Server]"
  - "tamaño [SQL Server], archivos"
ms.assetid: 88c31b02-f44c-4a14-be8b-437f2097de12
caps.latest.revision: 23
author: "JennieHubbard"
ms.author: "jhubbard"
manager: "jhubbard"
caps.handback.revision: 23
---
# Limitar el tama&#241;o de la tabla y el archivo de seguimiento
  Los resultados de Seguimiento de SQL difieren en cuanto a tamaño en función de las clases de evento que se incluyen en el seguimiento y la forma en que se utiliza el [!INCLUDE[ssDE](../../includes/ssde-md.md)] . Si realiza el seguimiento de clases de evento que se producen con frecuencia, puede minimizar la cantidad de datos que recopila el seguimiento estableciendo el tamaño máximo del archivo o el número máximo de filas. Si especifica el tamaño máximo del archivo o las filas, se garantiza que el archivo o la tabla de seguimiento no crecerán más allá del límite especificado.  
  
> [!NOTE]  
>  Si guarda datos del seguimiento en un archivo que ya existe, puede anexar datos al archivo o sobrescribirlo. Si decide anexar datos al archivo y el archivo de seguimiento ya ha alcanzado o supera el tamaño máximo de archivo especificado, se le ofrece la posibilidad de aumentar el tamaño máximo de archivo o especificar un archivo nuevo. Lo mismo ocurre con las tablas de seguimiento.  
  
## Tamaño máximo del archivo  
 Un seguimiento con un tamaño máximo de archivo deja de guardar información de seguimiento en el archivo una vez que se ha alcanzado el tamaño máximo del archivo. Esta opción le permite agrupar eventos en archivos más pequeños y más fáciles de administrar. Además, al limitar el tamaño del archivo, la ejecución de seguimientos desatendidos es más segura, ya que el seguimiento se detiene al alcanzar el tamaño máximo del archivo. Para establecer el tamaño máximo de archivo de los seguimientos creados puede utilizar procedimientos almacenados de Transact-SQL o el [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)].  
  
 Hay un límite superior de 1 gigabyte (GB) para la opción de tamaño máximo del archivo. El tamaño máximo predeterminado de archivo es de 5 megabytes (MB).  
  
### Habilitar la sustitución incremental de archivos  
 La opción de sustitución incremental de archivos hace que [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] cierre el archivo actual y cree un archivo nuevo al alcanzar el tamaño máximo de archivo. El archivo nuevo tendrá el mismo nombre que el anterior, pero se agregará un número entero para indicar su secuencia. Por ejemplo, si el archivo de seguimiento original se denominaba nombreDearchivo_1.trc, el siguiente archivo de seguimiento se denominará nombreDearchivo_2.trc, y así sucesivamente. Si un archivo existente ya utiliza el nombre asignado a un archivo nuevo de sustitución incremental, el archivo existente se sobrescribe, a menos que sea de solo lectura. Esta opción de sustitución incremental de archivos está habilitada de forma predeterminada cuando guarda datos de un seguimiento en un archivo.  
  
> [!NOTE]  
>  Con la opción de sustitución incremental de archivos activada, el seguimiento continúa hasta que se detiene por otro medio. Para detener el seguimiento una vez que se ha alcanzado el límite de tamaño de archivo, deshabilite la opción de sustitución incremental de archivos.  
  
 **Para establecer un tamaño máximo de archivo para un archivo de seguimiento**  
  
 [Establecer un tamaño máximo de archivo para un archivo de seguimiento &#40;SQL Server Profiler&#41;](../../tools/sql-server-profiler/set-a-maximum-file-size-for-a-trace-file-sql-server-profiler.md)  
  
## Número máximo de filas  
 Un seguimiento con un número máximo de filas deja de guardar información de seguimiento en una tabla una vez que se ha alcanzado el número máximo de filas. Cada evento constituye una fila, por lo que este parámetro establece un límite en el número de eventos que se recopilan. Si se establece el número máximo de filas, se facilita la ejecución de seguimientos desatendidos. Por ejemplo, si necesita iniciar un seguimiento que guarde los datos del seguimiento en una tabla, pero desea detener el seguimiento cuando la tabla sea demasiado grande, puede hacerlo automáticamente.  
  
 Si se ha especificado el número máximo de filas y se ha alcanzado este límite, el seguimiento continúa ejecutándose mientras el [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] está en ejecución, pero la información de seguimiento ya no se registra. [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] continúa mostrando los resultados del seguimiento hasta que este se detiene.  
  
 **Para establecer un número máximo de filas para un seguimiento**  
  
 [Establecer un tamaño máximo de tabla para una tabla de seguimiento &#40;SQL Server Profiler&#41;](../../tools/sql-server-profiler/set-a-maximum-table-size-for-a-trace-table-sql-server-profiler.md)  
  
## Vea también  
 [sp_trace_create &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-trace-create-transact-sql.md)  
  
  