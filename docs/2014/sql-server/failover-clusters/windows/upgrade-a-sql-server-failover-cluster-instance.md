---
title: Actualizar un clúster de conmutación por error SQL Server | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- database-engine
ms.topic: conceptual
helpviewer_keywords:
- upgrading failover clusters
- clusters [SQL Server], upgrading
- failover clustering [SQL Server], upgrading
ms.assetid: daac41fe-7d0b-4f14-84c2-62952ad8cbfa
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 3397ac65b4c3ca5f5d7ac9e8068ca3e078d466c8
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/02/2018
ms.locfileid: "48211204"
---
# <a name="upgrade-a-sql-server-failover-cluster"></a>Actualizar un clúster de conmutación por error de SQL Server
  [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] admite la actualización de [!INCLUDE[ssDE](../../../includes/ssde-md.md)] y [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] desde los clústeres de conmutación por error de [!INCLUDE[ssVersion2005](../../../includes/ssversion2005-md.md)], [!INCLUDE[ssKatmai](../../../includes/sskatmai-md.md)], [!INCLUDE[ssKilimanjaro](../../../includes/sskilimanjaro-md.md)] y [!INCLUDE[ssSQL11](../../../includes/sssql11-md.md)] por separado en todos los nodos de clúster de conmutación por error.  
  
 Los detalles de compatibilidad son los siguientes:  
  
-   La actualización se puede realizar tanto a través de la interfaz de usuario como desde el símbolo del sistema. Para más información, vea [Actualizar una instancia de clúster de conmutación por error de SQL Server &#40;programa de instalación&#41;](upgrade-a-sql-server-failover-cluster-instance-setup.md) e [Instalar SQL Server 2014 desde el símbolo del sistema](../../../database-engine/install-windows/install-sql-server-from-the-command-prompt.md).  
  
-   Actualizar desde [!INCLUDE[ssKilimanjaro](../../../includes/sskilimanjaro-md.md)] : puede ejecutar la actualización desde el símbolo del sistema en cada nodo de clúster de conmutación por error, o usando la UI del programa de instalación para actualizar cada nodo de clúster. Si la instancia que se va a actualizar no dispone de las características de replicación y búsqueda de texto completo, éstas se instalarán automáticamente sin posibilidad de omitirlas.  
  
-   Instalación de los Service Pack: debe aplicar los Service Pack y las revisiones de [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] a los clústeres de conmutación por error de [!INCLUDE[ssSQL11](../../../includes/sssql11-md.md)] por separado en todos los nodos.  
  
-   Los escenarios siguientes no se admiten:  
  
    -   No puede realizar la migración desde una instancia independiente de [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] a un clúster de conmutación por error.  
  
    -   Agregar características a un clúster de conmutación por error. Por ejemplo, no se puede agregar [!INCLUDE[ssDE](../../../includes/ssde-md.md)] a un clúster de conmutación por error existente de [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)].  
  
    -   No puede degradar un nodo de clúster de conmutación por error a una instancia independiente.  
  
-   Para obtener más información, consulte [ instancias de clúster de conmutación por error de AlwaysOn (SQL Server)](always-on-failover-cluster-instances-sql-server.md).  
  
## <a name="upgrading-a-includessnoversionincludesssnoversion-mdmd-multi-subnet-failover-cluster"></a>Actualizar un clúster de conmutación por error de varias subredes de [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]  
 No puede actualizar directamente un clúster de conmutación por error de [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] que no es de varias subredes a un clúster de conmutación por error de [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] de varias subredes. Para más información, vea [Actualizar una instancia de clúster de conmutación por error de SQL Server &#40;programa de instalación&#41;](upgrade-a-sql-server-failover-cluster-instance-setup.md).  
  
## <a name="see-also"></a>Vea también  
 [Actualizaciones de ediciones y versiones admitidas](../../../database-engine/install-windows/supported-version-and-edition-upgrades.md)   
 [Actualizar una instancia de clúster de conmutación por error SQL Server &#40;el programa de instalación&#41;](upgrade-a-sql-server-failover-cluster-instance-setup.md)   
 [Instalar SQL Server 2014 desde el símbolo del sistema](../../../database-engine/install-windows/install-sql-server-from-the-command-prompt.md)  
  
  
