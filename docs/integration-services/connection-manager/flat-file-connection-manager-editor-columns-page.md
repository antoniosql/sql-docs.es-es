---
title: "Editor del administrador de conexiones de archivos planos (p&#225;gina Columnas) | Microsoft Docs"
ms.custom: ""
ms.date: "03/01/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "integration-services"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "sql13.dts.designer.ffileconnection.columns.f1"
helpviewer_keywords: 
  - "Administrador de conexiones de archivos planos, editor del"
ms.assetid: 40ce7537-abd0-4973-97fd-6ccb90fddfa0
caps.latest.revision: 21
author: "douglaslMS"
ms.author: "douglasl"
manager: "jhubbard"
caps.handback.revision: 21
---
# Editor del administrador de conexiones de archivos planos (p&#225;gina Columnas)
  Utilice la página **Columnas** del cuadro de diálogo **Editor del administrador de conexiones de archivos planos** para especificar la información de filas y columnas, y para obtener una vista previa del archivo.  
  
 Para obtener más información acerca del administrador de conexiones de archivos planos, vea [Flat File Connection Manager](../../integration-services/connection-manager/flat-file-connection-manager.md).  
  
## Opciones estáticas  
 **Nombre del administrador de conexiones**  
 Especifique un nombre único para la conexión de archivo plano en el flujo de trabajo. El nombre que indique se mostrará en el Diseñador [!INCLUDE[ssIS](../../includes/ssis-md.md)] .  
  
 **Description**  
 Describe la conexión. Como método recomendado, describa la conexión desde el punto de vista de su propósito, para que los paquetes estén autodocumentados y sean más fáciles de mantener.  
  
## Opciones dinámicas de formato para archivos planos  
  
### Formato = Delimitado  
 **Delimitador de filas**  
 Selecciónelo de la lista de delimitadores de filas disponibles o escriba el texto delimitador.  
  
|Value|Description|  
|-----------|-----------------|  
|**{CR}{LF}**|Las filas se delimitan mediante una combinación de retorno de carro y avance de línea.|  
|**{CR}**|Las filas se delimitan mediante un retorno de carro.|  
|**{LF}**|Las filas se delimitan mediante un avance de línea.|  
|**Punto y coma {;}**|Las filas se delimitan mediante un punto y coma.|  
|**Dos puntos {:}**|Las filas se delimitan mediante dos puntos.|  
|**Coma {,}**|Las filas se delimitan mediante una coma.|  
|**Tabulación {t}**|Las filas se delimitan mediante un tabulador.|  
|**Barra vertical {&#124;}**|Las filas se delimitan mediante una barra vertical.|  
  
 **Delimitador de columna**  
 Selecciónelo de la lista de delimitadores de columna disponibles o escriba el texto delimitador.  
  
|Value|Description|  
|-----------|-----------------|  
|**{CR}{LF}**|Las columnas se delimitan mediante una combinación de retorno de carro y avance de línea.|  
|**{CR}**|Las columnas se delimitan mediante un retorno de carro.|  
|**{LF}**|Las columnas se delimitan mediante un avance de línea.|  
|**Punto y coma {;}**|Las columnas se delimitan mediante un punto y coma.|  
|**Dos puntos {:}**|Las columnas se delimitan mediante un punto y coma.|  
|**Coma {,}**|Las columnas se delimitan mediante una coma.|  
|**Tabulación {t}**|Las columnas se delimitan mediante un tabulador.|  
|**Barra vertical {&#124;}**|Las columnas se delimitan mediante una barra vertical.|  
  
 **Actualizar**  
 Al hacer clic en **Actualizar**, verá el efecto del cambio de delimitadores que se van a omitir. Este botón solo se hace visible después de cambiar otras opciones de conexión.  
  
 **Vista previa de filas**  
 Presenta datos de ejemplo del archivo plano, divididos en columnas y filas mediante las opciones seleccionadas.  
  
 **Restablecer columnas**  
 Al hacer clic en **Restablecer columnas** se eliminará todo, excepto las columnas originales.  
  
### Formato = Ancho fijo  
 **Fuente**  
 Seleccione la fuente en la que se presentará la vista previa de los datos.  
  
 **Columnas de datos de origen**  
 Ajuste el ancho de la fila desplazando el marcador vertical de color rojo de la fila; ajuste el ancho de las columnas haciendo clic en la regla, en la parte superior de la ventana de vista previa.  
  
 **Ancho de fila**  
 Especifique la longitud de la fila antes de agregar los delimitadores para las columnas individuales. O bien arrastre la línea roja vertical en la ventana de vista previa para marcar el final de la fila. El valor del ancho de la fila se actualizará automáticamente.  
  
 **Restablecer columnas**  
 Al hacer clic en **Restablecer columnas** se eliminará todo, excepto las columnas originales.  
  
### Formato = Derecho irregular  
  
> [!NOTE]  
>  Los archivos de derecho irregular son archivos en los que todas las columnas tienen un ancho fijo, a excepción de la última. Se delimita mediante el delimitador de fila.  
  
 **Fuente**  
 Seleccione la fuente en la que se presentará la vista previa de los datos.  
  
 **Columnas de datos de origen**  
 Ajuste el ancho de la fila desplazando el marcador vertical de color rojo de la fila; ajuste el ancho de las columnas haciendo clic en la regla, en la parte superior de la ventana de vista previa.  
  
 **Delimitador de filas**  
 Selecciónelo de la lista de delimitadores de filas disponibles o escriba el texto delimitador.  
  
|Value|Description|  
|-----------|-----------------|  
|**{CR}{LF}**|Las filas se delimitan mediante una combinación de retorno de carro y avance de línea.|  
|**{CR}**|Las filas se delimitan mediante un retorno de carro.|  
|**{LF}**|Las filas se delimitan mediante un avance de línea.|  
|**Punto y coma {;}**|Las filas se delimitan mediante un punto y coma.|  
|**Dos puntos {:}**|Las filas se delimitan mediante dos puntos.|  
|**Coma {,}**|Las filas se delimitan mediante una coma.|  
|**Tabulación {t}**|Las filas se delimitan mediante un tabulador.|  
|**Barra vertical {&#124;}**|Las filas se delimitan mediante una barra vertical.|  
  
 **Restablecer columnas**  
 Al hacer clic en **Restablecer columnas** se eliminará todo, excepto las columnas originales.  
  
## Vea también  
 [Referencia de errores y mensajes de Integration Services](../../integration-services/integration-services-error-and-message-reference.md)   
 [Editor del administrador de conexiones de archivos planos &#40;página General&#41;](../../integration-services/connection-manager/flat-file-connection-manager-editor-general-page.md)   
 [Editor del administrador de conexiones de archivos planos &#40;página Avanzadas&#41;](../../integration-services/connection-manager/flat-file-connection-manager-editor-advanced-page.md)   
 [Editor del administrador de conexiones de archivos planos &#40;página Vista previa&#41;](../../integration-services/connection-manager/flat-file-connection-manager-editor-preview-page.md)  
  
  