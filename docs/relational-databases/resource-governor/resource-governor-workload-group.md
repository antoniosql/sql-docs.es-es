---
title: "Grupos de cargas de trabajo del regulador de recursos | Microsoft Docs"
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
  - "regulador de recursos, grupo de cargas de trabajo"
  - "grupos de cargas de trabajo [SQL Server]"
  - "grupos de cargas de trabajo [SQL Server], información general"
ms.assetid: a84c3c3f-55b6-4a30-9c42-13f082d9281e
caps.latest.revision: 6
author: "JennieHubbard"
ms.author: "jhubbard"
manager: "jhubbard"
caps.handback.revision: 6
---
# Grupos de cargas de trabajo del regulador de recursos
  En el regulador de recursos de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , un grupo de cargas de trabajo actúa como un contenedor de las solicitudes de sesión que tienen criterios de clasificación similares. Una carga de trabajo permite la supervisión agregada de las sesiones y define directivas para estas. Cada grupo de cargas de trabajo está en un grupo de recursos de servidor, que representa un subconjunto de los recursos físicos de una instancia de [!INCLUDE[ssDE](../../includes/ssde-md.md)]. Cuando se inicia una sesión, el clasificador del regulador de recursos asigna la sesión a un grupo de cargas de trabajo concreto, y la sesión se debe ejecutar utilizando las directivas asignadas al grupo de cargas de trabajo y los recursos definidos para el grupo de recursos de servidor.  
  
## Conceptos del grupo de cargas de trabajo  
 Un grupo de cargas de trabajo sirve como contenedor para las solicitudes de sesión que sean similares de acuerdo con los criterios de clasificación que se aplican a cada solicitud. Un grupo de cargas de trabajo permite la supervisión agregada del consumo de recursos y la aplicación de una directiva uniforme a todas las solicitudes en el grupo. Un grupo define las directivas para sus miembros.  
  
> [!NOTE]  
>  Los grupos de cargas de trabajo definidos por el usuario se pueden mover de un grupo de recursos de servidor a otro.  
  
 El regulador de recursos predefine dos grupos de cargas de trabajo: el grupo interno y el grupo predeterminado. Un usuario no puede cambiar nada que esté clasificado como grupo interno, pero puede supervisarlo. Las solicitudes se clasifican en el grupo predeterminado cuando se dan las condiciones siguientes:  
  
-   No hay ningún criterio para clasificar una solicitud.  
  
-   Hay un intento de clasificar la solicitud en un grupo inexistente.  
  
-   Hay un error de clasificación general.  
  
 El regulador de recursos también proporciona instrucciones DLL para crear, cambiar y quitar grupos de cargas de trabajo.  
  
## Tareas de grupo de cargas de trabajo  
  
|Descripción de la tarea|Tema|  
|----------------------|-----------|  
|Describe cómo crear un grupo de cargas de trabajo.|[Crear un grupo de cargas de trabajo](../../relational-databases/resource-governor/create-a-workload-group.md)|  
|Describe cómo cambiar la configuración del grupo de cargas de trabajo.|[Cambiar la configuración del grupo de cargas de trabajo](../../relational-databases/resource-governor/change-workload-group-settings.md)|  
|Describe cómo eliminar un grupo de cargas de trabajo.|[Eliminar un grupo de cargas de trabajo](../../relational-databases/resource-governor/delete-a-workload-group.md)|  
  
## Vea también  
 [Regulador de recursos](../../relational-databases/resource-governor/resource-governor.md)   
 [Habilitar el regulador de recursos](../../relational-databases/resource-governor/enable-resource-governor.md)   
 [Grupo de recursos de servidor del regulador de recursos](../../relational-databases/resource-governor/resource-governor-resource-pool.md)   
 [Función clasificadora del regulador de recursos](../../relational-databases/resource-governor/resource-governor-classifier-function.md)   
 [Configurar el regulador de recursos utilizando una plantilla](../../relational-databases/resource-governor/configure-resource-governor-using-a-template.md)   
 [Ver las propiedades del regulador de recursos](../../relational-databases/resource-governor/view-resource-governor-properties.md)  
  
  