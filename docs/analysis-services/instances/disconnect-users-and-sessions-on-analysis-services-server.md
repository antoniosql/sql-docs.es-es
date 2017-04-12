---
title: "Desconectar usuarios y sesiones en el servidor de Analysis Services | Microsoft Docs"
ms.custom: ""
ms.date: "03/06/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "analysis-services"
  - "analysis-services/multidimensional-tabular"
  - "analysis-services/data-mining"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "actividad de los usuarios, finalizar [Analysis Services]"
  - "conexiones [Analysis Services]"
  - "sesiones [Analysis Services]"
ms.assetid: 3b0145a2-f21d-4dd0-a09e-83afeb2ff4a9
caps.latest.revision: 37
author: "Minewiskan"
ms.author: "owend"
manager: "erikre"
caps.handback.revision: 37
---
# Desconectar usuarios y sesiones en el servidor de Analysis Services
  Como administrador de [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] puede que desee la actividad del usuario final como parte de la administración de la carga de trabajo. Esto se lleva a cabo cancelando sesiones y conexiones. Las sesiones se pueden formar automáticamente cuando se ejecuta una consulta (implícito) o definirse en el momento en que las crea el administrador (explícito). Las conexiones son conductos abiertos con los que se pueden ejecutar las consultas. Tanto las sesiones como las conexiones se pueden terminar aunque estén activas. Por ejemplo, es posible que un administrador desee finalizar el procesamiento de una sesión si dicho procesamiento está tardando demasiado o si han surgido dudas sobre si el comando que se está ejecutando está correctamente escrito.  
  
## Terminar sesiones y conexiones  
 Para administrar sesiones y conexiones, puede utilizar las vistas de administración dinámica (DMV) y XMLA:  
  
1.  En [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], conéctese a una instancia de Analysis Services.  
  
2.  Pegue una de las siguientes consultas de DMV en una ventana de consulta MDX para obtener una lista de todas las sesiones, conexiones y comandos que se están ejecutando actualmente:  
  
     `Select * from $System.Discover_Sessions`  
  
     `Select * from $System.Discover_Connections`  
  
     `Select * from $System.Discover_Commands`  
  
3.  Presione F5 para ejecutar la consulta.  
  
     La consulta de DMV devuelve información de conexión y de sesión en un conjunto de resultados tabulares cuya lectura y copia es más fácil.  
  
 Mantenga la ventana de consulta abierta. En el paso siguiente, querrá volver a esta página para copiar los SPID de la sesión que desea desconectar.  
  
 Para terminar una sesión, abra una segunda ventana de consulta XMLA.  
  
1.  Pegue la siguiente sintaxis en una ventana de consulta MDX, reemplazando el marcador de posición ConnectionID, SessionID o SPID con un valor válido que copió en el paso anterior.  
  
    ```  
    <Cancel xmlns="http://schemas.microsoft.com/analysisservices/2003/engine">  
  
       <ConnectionID>111</ConnectionID>  
       <SessionID>222</SessionID>  
       <SPID>333</SPID>  
  
    <CancelAssociated>1</CancelAssociated>  
    </Cancel>  
  
    ```  
  
2.  Presione F5 para ejecutar el comando de cancelación.  
  
 La finalización de una conexión cancela todas las sesiones y SPID, cerrando la sesión del host.  
  
 La finalización de una sesión detiene todos los comandos (SPID) que se estén ejecutando como parte de dicha sesión.  
  
 La finalización de un SPID cancela un comando concreto.  
  
 En muy pocos casos, [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] no cerrará una conexión si no puede realizar el seguimiento de todas las sesiones y SPID asociados a la conexión (por ejemplo, cuando haya varias sesiones abiertas en un escenario HTTP).  
  
 Para obtener más información sobre el XMLA al que se hace referencia en este tema, vea [Método Execute &#40;XMLA&#41;](../Topic/Execute%20Method%20\(XMLA\).md) y [Elemento Cancel &#40;XMLA&#41;](../../analysis-services/xmla/xml-elements-commands/cancel-element-xmla.md).  
  
## Vea también  
 [Administrar conexiones y sesiones &#40;XMLA&#41;](../../analysis-services/multidimensional-models-scripting-language-assl-xmla/managing-connections-and-sessions-xmla.md)   
 [Elemento BeginSession &#40;XMLA&#41;](../../analysis-services/xmla/xml-elements-headers/beginsession-element-xmla.md)   
 [EndSession, elemento &#40;XMLA&#41;](../../analysis-services/xmla/xml-elements-headers/endsession-element-xmla.md)   
 [Session, elemento &#40;XMLA&#41;](../../analysis-services/xmla/xml-elements-headers/session-element-xmla.md)  
  
  