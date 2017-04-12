---
title: "Configurar reglas de negocios para enviar notificaciones (Master Data Services) | Microsoft Docs"
ms.custom: 
  - "SQL2016_New_Updated"
ms.date: "03/01/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "master-data-services"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "reglas de negocio [Master Data Services], configurar notificaciones"
  - "correo electrónico [Master Data Services], configurar reglas de negocio"
  - "notificaciones [Master Data Services], configurar reglas de negocio"
ms.assetid: b24f7b11-ab53-4642-999c-e17b543b3558
caps.latest.revision: 10
author: "sabotta"
ms.author: "carlasab"
manager: "jhubbard"
caps.handback.revision: 10
---
# Configurar reglas de negocios para enviar notificaciones (Master Data Services)
  En [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)], configure reglas de negocios para enviar notificaciones cuando desee notificar a los usuarios los cambios de los valores de los atributos.  
  
## Requisitos previos  
 Para realizar este procedimiento:  
  
-   Debe disponer del permiso para tener acceso a las áreas funcionales de **Permisos de usuario y de grupo** y de **Administración del sistema** . Si no tiene permiso para el área funcional de **Permisos de usuario y grupo** , no puede ver la lista de usuarios y grupos a los que enviar las notificaciones.  
  
-   Debe ser administrador de modelo. Para obtener más información, vea [Administradores &#40;Master Data Services&#41;](../master-data-services/administrators-master-data-services.md).  
  
-   Ya debe existir una regla de negocio que use una acción de validación. Para obtener más información, consulte [Crear y publicar una regla de negocios &#40;Master Data Services&#41;](../master-data-services/create-and-publish-a-business-rule-master-data-services.md).  
  
-   El usuario o grupo que recibe la notificación debe tener al menos permiso de **Solo lectura** para el atributo que produce un error en la validación. Los usuarios o grupos a los que se haya denegado explícita o implícitamente el permiso para el atributo recibirán el correo electrónico pero no podrán obtener acceso al atributo en [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)].  
  
-   Si el correo se envía a un grupo, solo los miembros del mismo que hayan tenido acceso a [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)] recibirán el correo electrónico.  
  
### Configurar reglas de negocios para enviar notificaciones  
  
1.  En [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)], haga clic en **Administración del sistema**.  
  
2.  En la barra de menús, seleccione **Administrar** y haga clic en **Reglas de negocios**.  
  
3.  En la página **Reglas de negocios** , en la lista **Modelo** , seleccione un modelo.  
  
4.  En la lista desplegable **Entidad**, seleccione una entidad.  
  
5.  En la lista desplegable **Member Types** (Tipos de miembros), seleccione un tipo de miembro.  
  
6.  En la cuadrícula, seleccione la fila de la regla de negocios que desea editar y haga clic en **Editar**.  
  
7.  Marque la casilla **Enviar notificaciones** y, en la lista desplegable, seleccione un usuario o grupo al que enviar una notificación por correo electrónico.  
  
8.  Haga clic en **Guardar**.  
  
9. Haga clic en **Publish All**(Publicar todo).  
  
10. En el cuadro de diálogo de confirmación, haga clic en **Aceptar**. El valor de la columna **Estado de la regla de negocio** ha cambiado a **Activo** y en la columna **Notificación** se muestra el usuario o grupo seleccionado al que enviar la notificación.  
  
## Pasos siguientes  
  
-   Aplique las reglas de negocios a los datos siguiendo uno de estos procedimientos:  
  
    -   [Validar miembros específicos con las reglas de negocios &#40;Master Data Services&#41;](../master-data-services/validate-specific-members-against-business-rules-master-data-services.md)  
  
    -   [Validar una versión con las reglas de negocios &#40;Master Data Services&#41;](../master-data-services/validate-a-version-against-business-rules-master-data-services.md)  
  
-   Configure el protocolo de correo electrónico de la manera siguiente:  
  
    -   [Configurar notificaciones por correo electrónico &#40;Master Data Services&#41;](../master-data-services/configure-email-notifications-master-data-services.md)  
  
## Vea también  
 [Notificaciones &#40;Master Data Services&#41;](../master-data-services/notifications-master-data-services.md)   
 [Configurar notificaciones por correo electrónico &#40;Master Data Services&#41;](../master-data-services/configure-email-notifications-master-data-services.md)  
  
  