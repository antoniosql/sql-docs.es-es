---
title: Clases Security de AMO | Documentos de Microsoft
ms.date: 05/02/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: amo
ms.topic: conceptual
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 8ca8bf233f706883b29c518517a28216e144765d
ms.sourcegitcommit: c12a7416d1996a3bcce3ebf4a3c9abe61b02fb9e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/10/2018
ms.locfileid: "34023352"
---
# <a name="amo-security-classes"></a>Clases Security de AMO
  Este tema contiene las siguientes secciones:  
  
-   [Objetos role y RoleMember](#RolesMembers)  
  
-   [Objetos de permiso](#Permissions)  
  
 La ilustración siguiente muestra la relación de las clases que se explican en este tema.  
  
 ![Clases Security de AMO se tratan en este tema](../../../analysis-services/multidimensional-models/analysis-management-objects/media/amo-securityclasses.gif "clases Security de AMO se tratan en este tema")  
  
##  <a name="RolesMembers"></a>Objetos role y RoleMember  
 Para crear un objeto <xref:Microsoft.AnalysisServices.Role>, éste se agrega a la colección de roles de la base de datos y se actualiza el objeto <xref:Microsoft.AnalysisServices.Role> en el servidor mediante el método Update. Un objeto <xref:Microsoft.AnalysisServices.Role> debe actualizarse para poder utilizarlo.  
  
 Para quitar un <xref:Microsoft.AnalysisServices.Role> objeto, tiene que quitarse mediante el método Drop de la <xref:Microsoft.AnalysisServices.Role> objeto. El método Remove, de la colección de roles, solamente impide que vea el rol en su aplicación, pero no lo quita del servidor. Un objeto <xref:Microsoft.AnalysisServices.Role> no se puede quitar si tiene permisos asociados.  
  
 Para crear un objeto <xref:Microsoft.AnalysisServices.RoleMember>, se agrega un usuario a la colección de miembros del rol y se actualiza el objeto <xref:Microsoft.AnalysisServices.Role> en el servidor mediante el método Update. Solo se permite crear roles a los administradores de servidor o de bases de datos. Un objeto <xref:Microsoft.AnalysisServices.Role> debe actualizarse en el servidor para que se permita a cualquiera de sus miembros utilizar los objetos para los que se ha concedido permiso al usuario.  
  
 Para quitar un objeto <xref:Microsoft.AnalysisServices.RoleMember>, debe quitarse el objeto de la colección mediante el método Remove y actualizar a continuación el rol mediante el método Update.  
  
 Para obtener más información acerca de los métodos y las propiedades disponibles para estos objetos, vea <xref:Microsoft.AnalysisServices.Role> y <xref:Microsoft.AnalysisServices.RoleMember> en <xref:Microsoft.AnalysisServices>.  
  
##  <a name="Permissions"></a>Objetos de permiso  
 Para crear un objeto <xref:Microsoft.AnalysisServices.Permission>, éste se agrega a la colección de permisos del objeto y se actualiza el objeto <xref:Microsoft.AnalysisServices.Permission> en el servidor mediante el método Update.  
  
 Para quitar un objeto <xref:Microsoft.AnalysisServices.Permission>, se tiene que hacer mediante el método Drop del objeto. El método remove, de la colección de permisos, solamente impide que vea el permiso en su aplicación, pero no quita el objeto <xref:Microsoft.AnalysisServices.Permission> del servidor. Un rol no se puede eliminar si tiene permisos asociados.  
  
 Para obtener más información acerca de los métodos y las propiedades disponibles, vea <xref:Microsoft.AnalysisServices.Permission> en <xref:Microsoft.AnalysisServices>.  
  
## <a name="see-also"></a>Vea también  
 <xref:Microsoft.AnalysisServices>   
 [Programar objetos de seguridad AMO](../../../analysis-services/multidimensional-models/analysis-management-objects/programming-amo-security-objects.md)   
 [Permisos y derechos de acceso & #40; Analysis Services - datos multidimensionales & #41;](http://msdn.microsoft.com/library/59fa3573-f985-46cb-8042-7da71bd59a7b)   
 [Introducción a las clases AMO](../../../analysis-services/multidimensional-models/analysis-management-objects/amo-classes-introduction.md)   
 [Arquitectura lógica & #40; Analysis Services - datos multidimensionales & #41;](../../../analysis-services/multidimensional-models/olap-logical/understanding-microsoft-olap-logical-architecture.md)   
 [Objetos de base de datos & #40; Analysis Services - datos multidimensionales & #41;](../../../analysis-services/multidimensional-models/olap-logical/database-objects-analysis-services-multidimensional-data.md)  
  
  
