---
title: "Ver un seguimiento guardado (Transact-SQL) | Microsoft Docs"
ms.custom: ""
ms.date: "03/04/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "database-engine"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "seguimientos [SQL Server], ver"
  - "mostrar seguimientos"
  - "ver seguimientos"
ms.assetid: 3a95a816-aa89-4d5f-858c-968a9cb3ee87
caps.latest.revision: 22
author: "JennieHubbard"
ms.author: "jhubbard"
manager: "jhubbard"
caps.handback.revision: 22
---
# Ver un seguimiento guardado (Transact-SQL)
  En este tema se describe cómo utilizar las funciones integradas para ver un seguimiento guardado.  
  
### Para ver un seguimiento específico  
  
1.  Ejecute **fn_trace_getinfo** especificando el identificador del seguimiento del que se precisa información. Esta función devuelve una tabla con el seguimiento, la propiedad del seguimiento e información acerca de la propiedad.  
  
     Llame a la función de esta manera:  
  
    ```  
    SELECT *  
    FROM ::fn_trace_getinfo(trace_id)  
    ```  
  
### Para ver todas los seguimientos existentes  
  
1.  Ejecute **fn_trace_getinfo** especificando `0` o `default`. Esta función devuelve una tabla con todos los seguimiento, sus propiedades e información acerca de estas propiedades.  
  
     Invoque la función de la siguiente manera:  
  
    ```  
    SELECT *  
    FROM ::fn_trace_getinfo(default)  
    ```  
  
## Seguridad de .NET Framework  
 Para ejecutar la función integrada **fn_trace_getinfo**, el usuario necesita el siguiente permiso:  
  
 ALTER TRACE en el servidor.  
  
## Vea también  
 [sys.fn_trace_getinfo &#40;Transact-SQL&#41;](../../relational-databases/system-functions/sys-fn-trace-getinfo-transact-sql.md)   
 [Ver y analizar seguimientos con SQL Server Profiler](../../tools/sql-server-profiler/view-and-analyze-traces-with-sql-server-profiler.md)  
  
  