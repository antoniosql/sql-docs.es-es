---
title: "Crear un atributo num&#233;rico (Master Data Services) | Microsoft Docs"
ms.custom: 
  - "SQL2016_New_Updated"
ms.date: "03/15/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "master-data-services"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "atributos [Master Data Services], crear atributos de número"
  - "crear atributos de número [Master Data Services]"
ms.assetid: c0dbb6d8-ba78-485a-a40d-6d5cb7e75d0a
caps.latest.revision: 9
author: "sabotta"
ms.author: "carlasab"
manager: "jhubbard"
caps.handback.revision: 9
---
# Crear un atributo num&#233;rico (Master Data Services)
  En [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)], cree un atributo numérico cuando desee que los usuarios escriban un número como valor de un atributo.  
  
> [!NOTE]  
>  Los atributos numéricos tienen limitaciones. Para obtener más información, consulte [Atributos &#40;Master Data Services&#41;](../master-data-services/attributes-master-data-services.md).  
  
## Requisitos previos  
 Para realizar este procedimiento:  
  
-   Debe disponer de permiso para tener acceso al área funcional de **Administración del sistema** .  
  
-   Debe ser administrador de modelo. Para obtener más información, vea [Administradores &#40;Master Data Services&#41;](../master-data-services/administrators-master-data-services.md).  
  
-   Debe existir una entidad para la que crear el atributo. Para obtener más información, consulte [Crear una entidad &#40;Master Data Services&#41;](../master-data-services/create-an-entity-master-data-services.md).  
  
## Información de atributo  
 Por cada atributo creado, se agrega una fila con siete columnas a la cuadrícula. En la siguiente tabla se describen las columnas.  
  
|Columna|Description|  
|------------|-----------------|  
|Estado|Estado del atributo.<br /><br /> Al hacer clic en Guardar, se muestra la imagen ![Icon for updating status](../master-data-services/media/mds-statusicon-updating.png "Icon for updating status"), lo que indica que el atributo se está actualizando.<br /><br /> Si aparecen errores al crear o editar un atributo, se muestra la imagen ![Icon for error status](../master-data-services/media/mds-statusicon-error.png "Icon for error status").<br /><br /> De lo contrario, el estado es correcto y se muestra la imagen ![Icon for OK status](../master-data-services/media/mds-statusicon-ok.png "Icon for OK status").|  
|Nombre|El nombre del atributo.|  
|Nombre para mostrar|Nombre para mostrar del atributo.|  
|Description|Descripción del atributo.|  
|Ancho de píxel de la pantalla|Ancho del atributo.|  
|Tipo y propiedades|Tipo e información sobre el tipo de datos del atributo.|  
|Habilitar seguimiento de cambios|Especifica si el atributo está habilitado para el seguimiento de cambios y muestra el número de grupo entre paréntesis.|  
  
 Cuando se hace clic en un atributo, se muestra la siguiente información.  
  
-   **Creado por:**nombre del usuario que creó el atributo.  
  
-   **El**: fecha y hora en que se creó el atributo.  
  
-   **Actualizado por**: nombre del último usuario que actualizó el atributo.  
  
-   **El**: Fecha y hora en que se actualizó el atributo por última vez.  
  
### Para crear un atributo numérico  
  
1.  En [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)], haga clic en **Administración del sistema**.  
  
2.  En la página **Manage Model** (Administrar modelo), seleccione un modelo de la cuadrícula y después haga clic en **Entidades**.  
  
3.  En la página **Manage Entity** (Administrar entidad), seleccione la fila de la entidad para la que desea crear un atributo.  
  
4.  Haga clic en **Atributos**.  
  
5.  En la página **Administrar atributos** , realice una de las siguientes acciones y haga clic en **Agregar**.  
  
    -   Si el atributo es para miembros hoja, seleccione **Hoja** en el cuadro de lista **Member Types** (Tipos de miembro).  
  
    -   Si el atributo es para miembros consolidados, seleccione **Consolidado** en el cuadro de lista **Member Types** (Tipos de miembro).  
  
    -   Si el atributo es para colecciones, seleccione **Colección** en el cuadro de lista **Member Types** (Tipos de miembro).  
  
6.  En el cuadro **Nombre** , escriba un nombre para el atributo. Para ver una lista de palabras que no se deben usar como nombres de atributo, consulte [Palabras reservadas &#40;Master Data Services&#41;](../master-data-services/reserved-words-master-data-services.md).  
  
7.  Opcionalmente, escriba un nombre para mostrar y una descripción para el atributo en el cuadro **Descripción** .  
  
8.  En el cuadro **Ancho de píxel de la pantalla** , escriba el ancho de la columna de atributo que se va a mostrar en la cuadrícula del **Explorador** .  
  
9. En la lista **Tipo de atributo**, seleccione **Forma libre**.  
  
10. En la lista **Tipo de datos** , seleccione **Número**.  
  
11. En el cuadro **Decimales** , escriba la cantidad de números que se pueden escribir después de un decimal.  
  
12. En la lista **Máscara de entrada** , seleccione un formato para los números negativos.  
  
13. Si lo desea, seleccione **Habilitar seguimiento de cambios** para realizar el seguimiento de los cambios en los grupos de atributos. Para obtener más información, consulte [Agregar atributos a un grupo de seguimiento de cambios &#40;Master Data Services&#41;](../master-data-services/add-attributes-to-a-change-tracking-group-master-data-services.md).  
  
14. Haga clic en **Guardar**.  
  
## Vea también  
 [Atributos &#40;Master Data Services&#41;](../master-data-services/attributes-master-data-services.md)   
 [Cambiar el nombre y el tipo de datos de un atributo &#40;Master Data Services&#41;](../master-data-services/change-an-attribute-name-and-data-type-master-data-services.md)   
 [Crear un atributo basado en dominio &#40;Master Data Services&#41;](../master-data-services/create-a-domain-based-attribute-master-data-services.md)   
 [Crear un atributo de archivo &#40;Master Data Services&#41;](../master-data-services/create-a-file-attribute-master-data-services.md)  
  
  