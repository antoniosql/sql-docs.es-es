---
title: "Transformaci&#243;n Conversi&#243;n de datos | Microsoft Docs"
ms.custom: ""
ms.date: "03/16/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "integration-services"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "sql13.dts.designer.dataconversiontrans.f1"
helpviewer_keywords: 
  - "convertir tipos de datos [Integration Services]"
  - "Conversión de datos, transformación"
  - "tipos de datos [Integration Services], convertir"
ms.assetid: fd515bbc-6f49-4d0c-ae7f-6ea3c3f24a1c
caps.latest.revision: 53
author: "douglaslMS"
ms.author: "douglasl"
manager: "jhubbard"
caps.handback.revision: 53
---
# Transformaci&#243;n Conversi&#243;n de datos
  La transformación Conversión de datos convierte los datos de una columna de entrada a otro tipo de datos diferente y después los copia a una nueva columna de salida. Por ejemplo, un paquete puede extraer los datos de diferentes orígenes y después usar esta transformación para convertir las columnas al tipo de datos necesario para el almacén de datos de destino. Puede aplicar múltiples conversiones a una sola columna de entrada.  
  
 Un paquete puede utilizar esta transformación para realizar las siguientes conversiones de tipos de datos:  
  
-   Cambiar el tipo de datos. Para más información, consulte [Integration Services Data Types](../../../integration-services/data-flow/integration-services-data-types.md).  
  
    > [!NOTE]  
    >  Si va a convertir datos a un tipo de datos de fecha o de fecha y hora, la fecha de la columna de salida tiene el formato ISO, aunque las preferencias de la configuración regional especifiquen un formato diferente.  
  
-   Establecer la longitud de la columna de los datos de cadena así como la precisión y la escala de los datos numéricos. Para más información, vea [Precisión, escala y longitud &#40;Transact-SQL&#41;](../../../t-sql/data-types/precision-scale-and-length-transact-sql.md).  
  
-   Especificar una página de códigos. Para más información, consulte [Comparing String Data](../../../integration-services/data-flow/comparing-string-data.md).  
  
    > [!NOTE]  
    >  Al copiar datos entre columnas con un tipo de datos de cadena, las dos columnas deben usar la misma página de códigos.  
  
 Si la longitud de una columna de salida de datos de tipo cadena es menor que la longitud de la columna de entrada correspondiente, se truncarán los datos de salida. Para más información, vea [Control de errores en los datos](../../../integration-services/data-flow/error-handling-in-data.md).  
  
 Esta transformación tiene una entrada, una salida y una salida de error.  
  
## Tareas relacionadas  
 Puede establecer propiedades a través del Diseñador [!INCLUDE[ssIS](../../../includes/ssis-md.md)] o mediante programación. Para más información sobre cómo usar la transformación Conversión de datos en el Diseñador SSIS, vea [Convertir datos en un tipo de datos diferente mediante la transformación Conversión de datos](../../../integration-services/data-flow/transformations/convert-data-type-by-using-data-conversion-transformation.md) y [Editor de transformación Conversión de datos](../../../integration-services/data-flow/transformations/data-conversion-transformation-editor.md). Para más información sobre cómo establecer las propiedades de esta transformación mediante programación, vea [Propiedades comunes](../Topic/Common%20Properties.md) y [Propiedades personalizadas de transformación](../../../integration-services/data-flow/transformations/transformation-custom-properties.md).  
  
## Contenido relacionado  
 Entrada de blog, sobre la [comparación de rendimiento entre las técnicas de conversión de tipos de datos en SSIS 2008](http://go.microsoft.com/fwlink/?LinkId=220823), en blogs.msdn.com.  
  
## Vea también  
 [Análisis rápido](../Topic/Fast%20Parse.md)   
 [Flujo de datos](../../../integration-services/data-flow/data-flow.md)   
 [Transformaciones de Integration Services](../../../integration-services/data-flow/transformations/integration-services-transformations.md)  
  
  