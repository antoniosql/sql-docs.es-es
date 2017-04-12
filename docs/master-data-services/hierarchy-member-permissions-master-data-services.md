---
title: "Permisos de miembros de la jerarqu&#237;a (Master Data Services) | Microsoft Docs"
ms.custom: ""
ms.date: "03/01/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "master-data-services"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "miembros [Master Data Services], permisos"
  - "permisos [Master Data Services], miembros"
ms.assetid: b3880eed-1bf6-4f65-ab23-b08c194cc858
caps.latest.revision: 11
author: "sabotta"
ms.author: "carlasab"
manager: "jhubbard"
caps.handback.revision: 11
---
# Permisos de miembros de la jerarqu&#237;a (Master Data Services)
  Los permisos de miembros de la jerarquía son opcionales y se deberían utilizar solo si se desea que un usuario tenga acceso limitado a miembros concretos. Si no asigna permisos en la pestaña **Miembros de la jerarquía** ,  permisos del usuario solo se basan en los permisos asignados en la pestaña **Modelos** .  
  
 Los permisos de miembros de la jerarquía se asignan en la interfaz de usuario de [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)] (UI), en el área funcional **Permisos de grupos y usuarios** de la pestaña **Miembros de la jerarquía**. Estos permisos determinan a qué miembros puede tener acceso un usuario en el área funcional del **Explorador** de la interfaz de usuario.  
  
 En la pestaña **Miembros de la jerarquía** , cada jerarquía se representa como una estructura de árbol. Al asignar permiso a un nodo en el árbol, todos los elementos secundarios heredan ese permiso a menos que el permiso se asigne explícitamente en un nivel inferior.  
  
> [!NOTE]  
>  Cuando asigna permisos a un nodo de una jerarquía, se deniegan implícitamente a todos los miembros de los demás nodos del mismo nivel o de un nivel superior.  
  
 En el **Explorador**, los permisos de miembro se aplican en todas las ubicaciones donde se muestre el miembro. Por ejemplo, un miembro con permiso de **Lectura** puede leer cualquier entidad, jerarquía y colección a las que pertenezca.  
  
 Los permisos de miembros de la jerarquía se aplican a la versión del modelo a la que los asigna y a cualquier copia futura de la versión. No se aplican a las versiones anteriores a la que los asigne.  
  
|Permiso|Description|  
|----------------|-----------------|  
|**Lectura**|Los miembros se muestran.<br /><br /> <br /><br /> Nota: Si solo asigna el permiso **Lectura** a **Raíz**, los miembros de **Raíz** son de solo lectura; en cambio, en las jerarquías explícitas y en las colecciones, el usuario puede mover miembros a **Raíz** y agregar miembros nuevos a **Raíz**.|  
|**Crear**|La creación de permisos no está disponible para los permisos de los miembros de jerarquías.|  
|**Update**|Se muestran los miembros, pero el usuario no puede cambiarlos. El usuario también puede mover los miembros en cualquier jerarquía explícita o colección a la que los miembros pertenezcan.|  
|**Delete**|Se muestran los miembros, y el usuario puede eliminarlos.|  
|**Denegar**|Los miembros no se muestran.|  
  
 En la pestaña **Miembros de la jerarquía** , los permisos que asigne no surtirán efecto inmediatamente. La frecuencia con la que se aplican permisos depende de la configuración del intervalo de procesamiento de la seguridad de los miembros **** en la tabla de configuración del sistema en la base de datos de [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] . Puede aplicar permisos de los miembros de forma inmediata si sigue los pasos descritos en [Aplicar inmediatamente los permisos de los miembros &#40;Master Data Services&#41;](../master-data-services/immediately-apply-member-permissions-master-data-services.md).  
  
> [!NOTE]  
>  No puede asignar los permisos de los miembros de la jerarquía a jerarquías recursivas, a jerarquías derivadas con límites explícitos y a jerarquías derivadas con niveles ocultos.  
  
## Posibilidad de superposición de permisos  
 Cuando asigne permisos a miembros, es posible que deba resolver problemas debidos a la superposición de permisos.  
  
### Cuando un miembro pertenece a varias jerarquías  
 Dos o más jerarquías pueden contener el mismo miembro.  
  
-   Si el nodo de una jerarquía tiene asignado el permiso **Actualizar** y otro tiene asignado el permiso **Lectura**, los miembros del nodo son de **Lectura**.  
  
-   Si un nodo de la jerarquía tiene asignados los permisos **Actualizar** y **Crear** y otro tiene asignados los permisos **Actualizar** y **Eliminar** , los miembros del nodo se pueden actualizar.  
  
-   Si un nodo de la jerarquía tiene asignada cualquier combinación de permisos **Crear**/**Lectura**/**Actualizar**/**Eliminar** y otro nodo tiene asignados permisos **Denegar**, se deniega el acceso a los miembros del nodo.  
  
## Recursos externos  
 Entrada de blog, [Security Improvements](http://go.microsoft.com/fwlink/p/?LinkId=615376)(Mejoras de seguridad), en msdn.com.  
  
## Vea también  
 [Asignar los permisos de los miembros de una jerarquía &#40;Master Data Services&#41;](../master-data-services/assign-hierarchy-member-permissions-master-data-services.md)   
 [Cómo se determinan los permisos &#40;Master Data Services&#41;](../master-data-services/how-permissions-are-determined-master-data-services.md)   
 [Miembros &#40;Master Data Services&#41;](../master-data-services/members-master-data-services.md)   
 [Jerarquías &#40;Master Data Services&#41;](../master-data-services/hierarchies-master-data-services.md)   
 [Aplicar inmediatamente los permisos de los miembros &#40;Master Data Services&#41;](../master-data-services/immediately-apply-member-permissions-master-data-services.md)  
  
  