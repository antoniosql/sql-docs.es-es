---
title: "Generar paquetes mediante programación | Documentos de Microsoft"
ms.custom: 
ms.date: 03/16/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- docset-sql-devref
ms.tgt_pltfrm: 
ms.topic: reference
applies_to:
- SQL Server 2016 Preview
ms.assetid: 7474b1f4-7607-4f28-a6fd-67f7db1dd3f8
caps.latest.revision: 26
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: 4a8ade977c971766c8f716ae5f33cac606c8e22d
ms.openlocfilehash: b80495b726ac6fdac713ba028629633bf84cc004
ms.contentlocale: es-es
ms.lasthandoff: 08/03/2017

---
# <a name="building-packages-programmatically"></a>Generar paquetes mediante programación
  Si necesita crear paquetes de forma dinámica o administrar y ejecutar paquetes de [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] fuera del entorno de desarrollo, puede manipular paquetes mediante programación. En este enfoque, tiene un intervalo de opciones continuo:  
  
-   Cargar y ejecutar un paquete existente sin modificarlo.  
  
-   Cargar un paquete existente, reconfigurarlo (por ejemplo, para un origen de datos distinto) y ejecutarlo.  
  
-   Crear un nuevo paquete, agregar y configurar componentes objeto por objeto y propiedad por propiedad, guardarlo y ejecutarlo.  
  
 Puede utilizar el modelo de objetos de [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] para escribir código que cree, configure y ejecute paquetes en cualquier lenguaje de programación administrado. Por ejemplo, quizá desee crear paquetes controlados por metadatos que configuren las conexiones o los orígenes de datos, las transformaciones y los destinos basándose en el origen de datos seleccionado y en sus tablas y columnas.  
  
 En esta sección se describe y se muestra cómo crear y configurar un paquete mediante programación línea a línea. Al final del intervalo de las opciones de programación del paquete menos complejo, simplemente puede cargar y ejecutar un paquete existente sin modificación como se describe en [ejecutar y administrar paquetes mediante programación](../../integration-services/run-manage-packages-programmatically/running-and-managing-packages-programmatically.md).  
  
 Una opción intermedia no descrita aquí consiste en cargar un paquete existente como una plantilla, reconfigurarlo (por ejemplo, para un origen de datos distinto) y ejecutarlo. También puede utilizar la información de esta sección para modificar los objetos existentes de un paquete.  
  
> [!NOTE]  
>  Al utilizar un paquete existente como una plantilla y modificar las columnas existentes del flujo de datos, quizá tenga que quitar las columnas existentes y llamar al método <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.ReinitializeMetaData%2A> de los componentes afectados.  
  
## <a name="in-this-section"></a>En esta sección  
 [Crear un paquete mediante programación](../../integration-services/building-packages-programmatically/creating-a-package-programmatically.md)  
 Describe cómo crear un paquete mediante programación.  
  
 [Agregar tareas mediante programación](../../integration-services/building-packages-programmatically/adding-tasks-programmatically.md)  
 Describe cómo agregar las tareas al paquete.  
  
 [Conectar tareas mediante programación](../../integration-services/building-packages-programmatically/connecting-tasks-programmatically.md)  
 Describe cómo controlar la ejecución de los contenedores y tareas de un paquete basándose en el resultado de la ejecución de una tarea o contenedor anterior.  
  
 [Agregar conexiones mediante programación](../../integration-services/building-packages-programmatically/adding-connections-programmatically.md)  
 Describe cómo agregar administradores de conexión a un paquete.  
  
 [Trabajar con Variables mediante programación](../../integration-services/building-packages-programmatically/working-with-variables-programmatically.md)  
 Describe cómo agregar y utilizar las variables durante la ejecución del paquete.  
  
 [Control de eventos mediante programación](../../integration-services/building-packages-programmatically/handling-events-programmatically.md)  
 Describe cómo administrar los eventos de paquetes y tareas.  
  
 [Habilitar el registro mediante programación](../../integration-services/building-packages-programmatically/enabling-logging-programmatically.md)  
 Describe cómo habilitar el registro de un paquete o tarea y cómo aplicar filtros personalizados a los eventos de registro.  
  
 [Agregar la tarea de flujo de datos mediante programación](../../integration-services/building-packages-programmatically/adding-the-data-flow-task-programmatically.md)  
 Describe cómo agregar y configurar la tarea Flujo de datos y sus componentes.  
  
 [Detectar componentes de flujo de datos mediante programación](../../integration-services/building-packages-programmatically/discovering-data-flow-components-programmatically.md)  
 Describe cómo detectar los componentes que se instalan en el equipo local.  
  
 [Agregar componentes de flujo de datos mediante programación](../../integration-services/building-packages-programmatically/adding-data-flow-components-programmatically.md)  
 Describe cómo agregar un componente a una tarea Flujo de datos.  
  
 [Conectar componentes de flujo de datos mediante programación](../../integration-services/building-packages-programmatically/connecting-data-flow-components-programmatically.md)  
 Describe cómo conectar dos componentes de flujo de datos.  
  
 [Seleccionar columnas de entrada mediante programación](../../integration-services/building-packages-programmatically/selecting-input-columns-programmatically.md)  
 Describe cómo seleccionar las columnas de entrada entre las proporcionadas a un componente por componentes de nivel superior en el flujo de datos.  
  
 [Guardar un paquete mediante programación](../../integration-services/building-packages-programmatically/saving-a-package-programmatically.md)  
 Describe cómo guardar un paquete mediante programación.  
  
## <a name="reference"></a>Referencia  
 [Referencia de mensajes y Error de Integration Services](../../integration-services/integration-services-error-and-message-reference.md)  
 Muestra los códigos de error predefinidos de [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] con sus nombres simbólicos y sus descripciones.  
  
## <a name="related-sections"></a>Secciones relacionadas  
 [Ampliar paquetes con Scripting](../../integration-services/extending-packages-scripting/extending-packages-with-scripting.md)  
 Explica cómo extender el flujo de control mediante la tarea Script y cómo extender el flujo de datos mediante el componente de script.  
  
 [Ampliar paquetes con objetos personalizados](../../integration-services/extending-packages-custom-objects/extending-packages-with-custom-objects.md)  
 Explica cómo crear tareas personalizadas de programa, componentes de flujo de datos y otros objetos de paquete para su uso en varios paquetes.  
  
 [Ejecutar y administrar paquetes mediante programación](../../integration-services/run-manage-packages-programmatically/running-and-managing-packages-programmatically.md)  
 Describe cómo enumerar, ejecutar y administrar paquetes y las carpetas en las que se almacenan.  
  
## <a name="external-resources"></a>Recursos externos  
  
-   Ejemplos de CodePlex, en la página [Integration Services Product Samples](http://go.microsoft.com/fwlink/?LinkID=131204)de www.codeplex.com/MSFTISProdSamples.  
  
-   Entrada de blog, [Generar perfiles de rendimiento de las extensiones personalizadas](http://go.microsoft.com/fwlink/?LinkId=238831), en blogs.msdn.com.  

## <a name="see-also"></a>Vea también  
 [SQL Server Integration Services](../../integration-services/sql-server-integration-services.md)  
  
  