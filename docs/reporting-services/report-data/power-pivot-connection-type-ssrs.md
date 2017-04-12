---
title: "Tipo de conexi&#243;n de PowerPivot (SSRS) | Microsoft Docs"
ms.custom: ""
ms.date: "03/01/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "reporting-services-sharepoint"
  - "reporting-services-native"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: a104c3c7-f118-4d02-9a0f-6859f1469d11
caps.latest.revision: 9
author: "guyinacube"
ms.author: "asaxton"
manager: "erikre"
caps.handback.revision: 9
---
# Tipo de conexi&#243;n de PowerPivot (SSRS)
  Puede utilizar la extensión de procesamiento de datos de SQL Server Analysis Services para recuperar datos de un libro [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] publicado en una galería de [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] de SharePoint.  
  
 Utilice la información de este tema para crear un origen de datos. Para obtener instrucciones paso a paso, vea [Agregar y comprobar una conexión de datos o un origen de datos &#40;Generador de informes y SSRS&#41;](../../reporting-services/report-data/add-and-verify-a-data-connection-report-builder-and-ssrs.md).  
  
## Requisitos previos  
 El origen de datos [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] se debe publicar en una galería de [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] en un sitio de SharePoint.  
  
 Para admitir conexiones del Generador de informes con un libro [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] , debe tener SQL Server 2008 R2 ADOMD.NET en el equipo de la estación de trabajo. Esta biblioteca cliente se instala con [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] para Excel, pero si está usando un equipo que no tiene esta aplicación, debe descargar e instalar ADOMD.NET de la página [SQL Server 2008 R2 Feature Pack](http://go.microsoft.com/fwlink/?LinkId=192565).  
  
## Tipo de origen de datos  
 Utilice el origen de datos de informe de tipo **Microsoft SQL Server Analysis Services**.  
  
## Cadena de conexión  
 La cadena de conexión es la dirección URL al libro de [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] publicado en SharePoint en la Galería de [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] u otra biblioteca (por ejemplo, http://contoso-srv/subsite/PowerPivotLibrary/ContosoSales.xlsx).  
  
## Credenciales  
 Especifique las credenciales necesarias para tener acceso al libro de [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] y el sitio de SharePoint, como Autenticación de Windows (Seguridad integrada). Para más información, vea [Conexiones de datos, orígenes de datos y cadenas de conexión &#40;Generador de informes y SSRS&#41;](../../reporting-services/report-data/data-connections-data-sources-and-connection-strings-report-builder-and-ssrs.md) o [Especificar credenciales en el Generador de informes](../Topic/Specify%20Credentials%20in%20Report%20Builder.md).  
  
## Consultas  
 Cuando esté conectado al origen de datos [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] , utilice el diseñador gráfico de consultas MDX para crear una consulta examinando las estructuras de datos subyacentes y seleccionando una de ellas. Después de generar una consulta, ejecútela para ver los datos de muestra en el panel de resultados.  
  
 El diseñador de consultas analiza la consulta para determinar los campos del conjunto de datos. También puede modificar manualmente la colección de campos del conjunto de datos en el panel **Datos de informe** . Para más información, vea [Agregar, editar y actualizar campos en el panel Datos de informe &#40;Generador de informes y SSRS&#41;](../../reporting-services/report-data/add-edit-refresh-fields-in-the-report-data-pane-report-builder-and-ssrs.md).  
  
## Filtros  
 En el recuadro Filtros, especifique dimensiones y miembros para excluirlos o incluirlos en los resultados de la consulta.  
  
## Parámetros  
 En el panel Filtros, seleccione la opción **Parámetros** para que un filtro cree automáticamente un parámetro de informe con valores disponibles que correspondan a las selecciones de filtro.  
  
## Comentarios  
 Si abre el Generador de informes desde el libro de [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] en una Galería de [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)], las tablas dinámicas, los gráficos dinámicos, las segmentaciones y otras características de análisis y de diseño del libro de [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] no se volverán a crear en el informe. En lugar de ello, el informe en blanco contiene un origen de datos preconfigurado que selecciona los datos del libro [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] . El diseño de informes basados en un libro de [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] puede ser laborioso y lento, según el número de segmentaciones, filtros y tablas o gráficos que quiera volver a crear en el informe. Resulta más práctico imaginar la presentación de los datos deseados en un informe independientemente del diseño de [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] .  
  
 Los datos de un libro [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] están muy comprimidos. Los datos recuperados del libro [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] para crear un informe no están comprimidos. Use el diseñador de consultas para especificar filtros y parámetros con el fin de limitar los datos a los estrictamente necesarios en el informe.  
  
 A diferencia de la conexión a un cubo de Analysis Services, un modelo de [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] no tiene jerarquías. Para proporcionar una funcionalidad similar a las segmentaciones de datos relacionadas del libro, debe crear colocando parámetros en cascada en el informe. Para más información, vea [Agregar parámetros en cascada a un informe &#40;Generador de informes y SSRS&#41;](../../reporting-services/report-design/add-cascading-parameters-to-a-report-report-builder-and-ssrs.md).  
  
 En algunos casos, podría necesitar ajustar las expresiones para aceptar los valores de datos subyacentes del modelo de [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] . Podría tener que modificar las expresiones para convertir los datos en el tipo de datos correcto, o agregar o quitar una función de agregado. Por ejemplo, para convertir el tipo de datos de cadena en entero, utilice `=CInt`. Compruebe siempre que el informe muestra los valores esperados de los datos del modelo de [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] antes de publicar el informe.  
  
 Se generan vistas previas de las imágenes de un informe en una Galería de [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] solo si se cumplen las siguientes condiciones:  
  
-   El informe y el libro de [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] que proporciona los datos deben estar almacenados juntos en la misma Galería de [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] .  
  
-   El informe solo contiene datos [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] de un origen de datos [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] .  
  
## Vea también  
 [Interfaz de usuario del Diseñador de consultas MDX de Analysis Services &#40;Generador de informes&#41;](../Topic/Analysis%20Services%20MDX%20Query%20Designer%20User%20Interface%20\(Report%20Builder\).md)   
 [Expresiones &#40;Generador de informes y SSRS&#41;](../../reporting-services/report-design/expressions-report-builder-and-ssrs.md)  
  
  