---
title: 'Paso 2: Convertir el proyecto al modelo de implementación de proyectos | Microsoft Docs'
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- integration-services
ms.topic: conceptual
ms.assetid: 80964293-f1f5-4da7-b1fb-00ab8c30c1c5
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.openlocfilehash: 459630f452458d4bbc9723133013c861619806bc
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/02/2018
ms.locfileid: "48093935"
---
# <a name="step-2-converting-the-project-to-the-project-deployment-model"></a>Paso 2: Convertir el proyecto al modelo de implementación de proyectos
  En esta tarea, usará al Asistente para conversión de proyectos de Integration Services para convertir el proyecto en el modelo de implementación del proyecto.  
  
### <a name="converting-the-project-to-the-project-deployment-model"></a>Convertir el proyecto al modelo de implementación del proyectos  
  
1.  En el menú Proyecto, haga clic en Convertir al modelo de implementación de proyectos.  
  
2.  En la página de introducción del Asistente para conversión de proyectos de Integration Services, revise los pasos y haga clic en Siguiente.  
  
3.  En la página Seleccionar paquetes, en la lista de paquetes, desactive todas las casillas de verificación excepto Lesson 6.dtsx y haga clic en Siguiente.  
  
4.  En la página Especificar propiedades del proyecto, haga clic en Siguiente.  
  
5.  En la página Actualizar tarea Ejecutar paquete, haga clic en Siguiente.  
  
6.  En la página Seleccionar configuración, asegúrese de que el paquete Lesson 6.dtsx está seleccionado en la lista de configuraciones y haga clic en Siguiente.  
  
7.  En la página Crear parámetros, asegúrese de que el paquete Lesson 6.dtsx está seleccionado y el ámbito está configurado en Paquete, en la lista de propiedades de configuración, y haga clic en Siguiente.  
  
8.  En la página Configurar parámetros, compruebe que los valores de Nombre y Valor son el mismo nombre y el mismo valor especificados en Lesson 5 para la variable y el valor de configuración, y haga clic en Siguiente.  
  
9. En la página Revisar, en el panel de resumen, tenga en cuenta que el asistente ha usado la información del archivo de configuración para establecer las propiedades que se van a convertir.  
  
10. Haga clic en Convertir.  
  
     Cuando la conversión finaliza, se muestra un mensaje que advierte que los cambios no se guardarán hasta que el proyecto se guarde en Visual Studio. Haga clic en Aceptar del cuadro de diálogo de advertencia.  
  
11. En el Asistente para conversión de proyectos de Integration Services, haga clic en Cerrar.  
  
12. En Herramientas de datos de SQL Server, haga clic en el menú Archivo y haga clic en Guardar para guardar el paquete convertido.  
  
13. Haga clic en la ficha Parámetros y compruebe que el paquete contiene un parámetro para VarFolderName, y que el valor es la misma ruta de acceso especificada para la carpeta Nuevos datos de ejemplo del archivo de configuración Lesson 5.  
  
## <a name="next-task-in-lesson"></a>Siguiente tarea de la lección  
 [Paso 3: Probar el paquete de la lección 6](lesson-6-3-testing-the-lesson-6-package.md)  
  
  
