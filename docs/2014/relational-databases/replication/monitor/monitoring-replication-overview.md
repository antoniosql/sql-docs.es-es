---
title: Supervisión de la replicación | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- replication
ms.topic: conceptual
helpviewer_keywords:
- monitoring performance [SQL Server replication], Replication Monitor
- Replication Monitor, about Replication Monitor
ms.assetid: 81f596d2-27a5-489d-bf8d-0f4361decd02
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: c18872dee35e55da6af067f9459e15f99f9402bd
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/02/2018
ms.locfileid: "48165445"
---
# <a name="monitoring-replication"></a>Supervisar la replicación
  El Monitor de replicación de[!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] es una herramienta gráfica que le permite supervisar el estado general de un topología de replicación. El Monitor de replicación proporciona información detallada sobre el estado y rendimiento de las publicaciones y suscripciones, y le permite responder a preguntas comunes, tales como:  
  
-   ¿Es correcto el sistema de replicación?  
  
-   ¿Qué suscripciones son lentas?  
  
-   ¿Cuál es el retraso de la suscripción transaccional?  
  
-   ¿Cuánto tardará una transacción confirmada ahora en llegar al suscriptor en la replicación transaccional?  
  
-   ¿Por qué es lenta la suscripción de mezcla?  
  
-   ¿Por qué no se ejecuta un agente?  
  
 Para supervisar la replicación, un usuario debe ser miembro del rol fijo de servidor **sysadmin** en el distribuidor o miembro del rol fijo de base de datos **replmonitor** en la base de datos de distribución. Un administrador del sistema puede agregar cualquier usuario al rol **replmonitor** , que permite a un usuario ver la actividad de replicación en el Monitor de replicación; sin embargo, el usuario no puede administrar la replicación.  
  
## <a name="in-this-section"></a>En esta sección  
 En los siguientes temas se proporciona información sobre las características del Monitor de replicación.  
  
 [Información general de la interfaz del Monitor de replicación](overview-of-the-replication-monitor-interface.md)  
 Describe cada ventana y pestaña del Monitor de replicación y proporciona información sobre cómo responder a las preguntas enumeradas anteriormente.  
  
 [Iniciar el Monitor de replicación](start-the-replication-monitor.md)  
 Describe cómo iniciar el Monitor de replicación.  
  
 [Permitir el uso del Monitor de replicación a los usuarios que no son administradores](allow-non-administrators-to-use-replication-monitor.md)  
 Describe cómo asignar permisos a los usuarios que no son administradores de forma que puedan usar el Monitor de replicación.  
  
 [Agregar y quitar publicadores del Monitor de replicación](add-and-remove-publishers-from-replication-monitor.md)  
 Describe cómo agregar y quitar publicadores del Monitor de replicación.  
  
 [Actualizar datos en el Monitor de replicación](refresh-data-in-replication-monitor.md)  
 Describe cómo actualizar datos en el Monitor de replicación.  
  
 [Supervisar el rendimiento con el Monitor de replicación](monitor-performance-with-replication-monitor.md)  
 Describe cómo supervisar el rendimiento en el Monitor de replicación, incluida información sobre el establecimiento de umbrales de rendimiento. Incluye información sobre estadísticas de artículos para la replicación de mezcla, que proporcionan una visión detallada del procesamiento.  
  
 [Medir la latencia y validar las conexiones de la replicación transaccional](measure-latency-and-validate-connections-for-transactional-replication.md)  
 Describe los testigos de seguimiento que le permiten medir el rendimiento de una topología de replicación transaccional.  
  
 [Supervisar agentes de replicación](../agents/replication-agents.md)  
 Describe el modo de localizar información acerca de cada agente de replicación.  
  
 [Establecer umbrales y advertencias en el Monitor de replicación](set-thresholds-and-warnings-in-replication-monitor.md)  
 Describe las advertencias, umbrales y alertas que puede establecer en el Monitor de replicación. Se recomienda habilitar las advertencias para la topología, con el fin de estar puntualmente informado sobre el estado y rendimiento.  
  
 [Almacenamiento en caché, actualización y rendimiento del Monitor de replicación](caching-refresh-and-replication-monitor-performance.md)  
 Describe cómo el Monitor de replicación almacena en memoria datos y cálculos para mejorar el rendimiento; explica cómo la actualización de la interfaz de usuario se relaciona con la actualización de la memoria caché.  
  
 [Ver el estado de la suscripción y la publicación en el Monitor de replicación](view-publication-and-subscription-status-in-replication-monitor.md)  
 Describe cómo ver información de estado de una publicación o suscripción mediante el Monitor de replicación.  
  
 [Ver información y realizar tareas para un publicador &#40;Monitor de replicación&#41;](view-information-and-perform-tasks-for-a-publisher-replication-monitor.md)  
 Describe cómo ver información y realizar tareas para un publicador mediante el Monitor de replicación.  
  
 [Ver información y realizar tareas para una publicación &#40;Monitor de replicación&#41;](view-information-and-perform-tasks-for-a-publication-replication-monitor.md)  
 Describe cómo ver información y realizar tareas para una publicación mediante el Monitor de replicación.  
  
 [Ver información y realizar tareas para los agentes asociados a una publicación &#40;Monitor de replicación&#41;](view-information-and-perform-tasks-for-publication-agents.md)  
 Describe cómo ver información y realizar tareas para los agentes asociados con una publicación mediante el Monitor de replicación.  
  
 [Ver información y realizar tareas para una suscripción &#40;Monitor de replicación&#41;](view-information-and-perform-tasks-for-a-subscription-replication-monitor.md)  
 Describe cómo ver información y realizar tareas para una suscripción mediante el Monitor de replicación.  
  
 [Ver información y realizar tareas para los agentes asociados a una suscripción &#40;Monitor de replicación&#41;](view-information-and-perform-tasks-for-subscription-agents.md)  
 Describe cómo ver información y realizar tareas para los agentes asociados con una suscripción mediante el Monitor de replicación.  
  
  
