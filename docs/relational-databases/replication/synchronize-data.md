---
title: Sincronizar datos | Microsoft Docs
ms.custom: ''
ms.date: 03/07/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
helpviewer_keywords:
- synchronization [SQL Server replication], about synchronization
- merge replication synchronization [SQL Server replication]
- scripts [SQL Server replication], synchronization and
- synchronization [SQL Server replication]
- snapshot replication [SQL Server], synchronization
- transactional replication, synchronization
- subscriptions [SQL Server replication], synchronizing
- on demand script execution
- replication [SQL Server], synchronization
- scripts [SQL Server replication]
ms.assetid: 724802f7-7d69-46d3-a330-bd8aa7f53114
author: MashaMSFT
ms.author: mathoma
manager: craigg
monikerRange: =azuresqldb-current||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current
ms.openlocfilehash: 8163d96451489e5704e92763de123cd208fb503f
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 10/01/2018
ms.locfileid: "47746073"
---
# <a name="synchronize-data"></a>Sincronizar datos
[!INCLUDE[appliesto-ss-asdb-xxxx-xxx-md](../../includes/appliesto-ss-asdb-xxxx-xxx-md.md)]
  La sincronización de los datos se refiere al proceso de propagación de los cambios en los datos y el esquema entre el publicador y los suscriptores después de haber aplicado la instantánea inicial en el suscriptor. La sincronización puede producirse:  
  
-   De forma continua, lo que es típico de la replicación transaccional.  
  
-   A petición, lo que es típico de la replicación de mezcla.  
  
-   Según una programación, lo que es típico de la replicación de instantáneas.  
  
 Cuando se sincroniza una suscripción, se producen diferentes procesos según el tipo de replicación que se utilice:  
  
-   Replicación de instantáneas. La sincronización significa que el Agente de distribución vuelve a aplicar la instantánea en el suscriptor, de modo que los datos y el esquema de la base de datos de suscripciones sean coherentes con la base de datos de publicación.  
  
     Si se han realizado modificaciones de los datos o del esquema en el publicador, es necesario generar una nueva instantánea para poder propagarlas al suscriptor.  
  
-   Replicación transaccional. La sincronización significa que el Agente de distribución transfiere las actualizaciones, las inserciones, las eliminaciones y otros cambios de la base de datos de distribución al suscriptor.  
  
-   Replicación de mezcla. La sincronización significa que el Agente de mezcla carga los cambios del suscriptor en el publicador y, después, descarga los cambios del publicador en el suscriptor. Si hubiera conflictos, se detectan y se resuelven. Los datos convergen y, al final, el publicador y todos los suscriptores acaban por tener los mismos valores. Si se detectan conflictos y se resuelven, el trabajo confirmado por algunos usuarios se modifica para solucionar el conflicto según las directrices definidas.  
  
 Las publicaciones de instantáneas actualizan completamente el esquema en el suscriptor cada vez que se produce una sincronización, así que todos los cambios de esquema se aplican en el suscriptor. La replicación transaccional y la replicación de mezcla también admiten los cambios de esquema más comunes. Para más información, vea [Make Schema Changes on Publication Databases](../../relational-databases/replication/publish/make-schema-changes-on-publication-databases.md) (Realizar cambios de esquema en bases de datos de publicaciones).  
  
 Para sincronizar una suscripción de inserción, vea [Synchronize a Push Subscription](../../relational-databases/replication/synchronize-a-push-subscription.md).  
  
 Para sincronizar una suscripción de extracción, vea [Synchronize a Pull Subscription](../../relational-databases/replication/synchronize-a-pull-subscription.md).  
  
 Para establecer programaciones de sincronización, vea [Specify Synchronization Schedules](../../relational-databases/replication/specify-synchronization-schedules.md).  
  
 **Para ver y solucionar los conflictos de sincronización**  
  
-   [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]: [Ver y resolver conflictos de datos para publicaciones de mezcla &#40;SQL Server Management Studio&#41;](../../relational-databases/replication/view-and-resolve-data-conflicts-for-merge-publications.md)  
  
-   [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]: [Ver conflictos de datos para publicaciones transaccionales &#40;SQL Server Management Studio&#41;](../../relational-databases/replication/view-data-conflicts-for-transactional-publications-sql-server-management-studio.md)  
  
## <a name="executing-code-during-synchronization"></a>Ejecutar código durante la sincronización  
 La replicación admite dos métodos de ejecución de código durante la sincronización  
  
-   La ejecución de script a petición se admite en la replicación transaccional y la replicación de mezcla. Con la ejecución de script a petición es posible especificar un script SQL para ejecutarlo durante la sincronización. Este script se copia en el suscriptor y se ejecuta mediante **sqlcmd** al inicio del proceso de sincronización. El script no tiene acceso a los cambios replicados cuando se aplican al suscriptor. Para más información, vea [Execute Scripts During Synchronization &#40;Replication Transact-SQL Programming&#41;](../../relational-databases/replication/execute-scripts-during-synchronization-replication-transact-sql-programming.md) (Ejecutar scripts durante la sincronización (programación de la replicación con Transact-SQL)).  
  
-   La replicación de mezcla admite controladores de lógica de negocios. El uso de un marco de trabajo de controladores de lógica de negocios le permite escribir un ensamblado de código administrado al que se llama durante el proceso de sincronización de mezcla. El ensamblado incluye lógica de negocios que puede responder a varias condiciones durante la sincronización: cambios de datos, conflictos y errores. Para más información, vea [Execute Business Logic During Merge Synchronization](../../relational-databases/replication/merge/execute-business-logic-during-merge-synchronization.md) (Ejecutar lógica de negocios durante la sincronización de mezcla).  
  
## <a name="see-also"></a>Ver también  
 [Detectar y solucionar conflictos de replicación de mezcla](../../relational-databases/replication/merge/advanced-merge-replication-resolve-merge-replication-conflicts.md)  
  
  
