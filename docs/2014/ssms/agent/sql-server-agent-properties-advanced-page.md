---
title: Propiedades de Agente SQL Server (página Avanzadas) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology: ''
ms.tgt_pltfrm: ''
ms.topic: conceptual
f1_keywords:
- sql12.ag.agent.advanced.f1
ms.assetid: a4d798ee-4c18-40d4-b6af-63d17503738c
caps.latest.revision: 16
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: b3e23c45859bb02baeec873f99392b318247bd69
ms.sourcegitcommit: 8ae6e6618a7e9186aab3c6a37ea43776aa9a382b
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/06/2018
ms.locfileid: "43807251"
---
# <a name="sql-server-agent-properties-advanced-page"></a>Propiedades de Agente SQL Server (página Avanzadas)
  Utilice esta página para ver y modificar las propiedades avanzadas del servicio del Agente [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .  
  
## <a name="options"></a>Opciones  
 **Reenvío de eventos de SQL Server**  
 Las opciones de esta categoría activan y configuran el reenvío de eventos.  
  
 **Reenviar eventos a otro servidor**  
 Reenvía los eventos del Agente [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] a otro servidor.  
  
 **Server**  
 Seleccione el nombre del servidor al que se reenvían los eventos.  
  
 **Eventos no controlados**  
 Solo reenvía eventos no controlados al servidor especificado. [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] solo reenvía eventos a los que no responde ninguna alerta.  
  
 **Todos los eventos**  
 Reenvía todos los eventos. Cuando una alerta de la instancia local responde al evento, el Agente [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] reenvía el evento y procesa la alerta.  
  
 **Si el evento tiene una gravedad de o por encima de**  
 Solo reenvía eventos con el nivel de gravedad igual o superior al especificado.  
  
 **Condición de CPU inactiva**  
 Las opciones de esta categoría definen las condiciones en las que el Agente [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ejecuta trabajos programados para ejecutarse en la programación de CPU inactiva.  
  
 **Definir condición de CPU inactiva**  
 Define las condiciones en las que el Agente [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] considera que la CPU está inactiva.  
  
 **El promedio de uso de la CPU baja de**  
 Porcentaje de uso de CPU por debajo del cual se considera inactiva la CPU.  
  
 **Y permanece por debajo durante**  
 Cantidad de tiempo que el promedio de uso de la CPU debe situarse por debajo del nivel especificado antes de que el Agente [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ejecute trabajos en la programación de CPU inactiva.  
  
## <a name="see-also"></a>Vea también  
 [Crear y adjuntar programaciones a trabajos](create-and-attach-schedules-to-jobs.md)   
 [Administrar eventos](manage-events.md)  
  
  
