---
title: "Usar Mis informes (Generador de informes y SSRS) | Microsoft Docs"
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
ms.assetid: 49c3c1da-b106-41f6-9173-16ff225bade8
caps.latest.revision: 8
author: "guyinacube"
ms.author: "asaxton"
manager: "erikre"
caps.handback.revision: 8
---
# Usar Mis informes (Generador de informes y SSRS)
  En un servidor de informes configurado en modo nativo, la carpeta Mis informes es un área de trabajo personal que puede usar para trabajar con sus informes y para almacenarlos. Otras carpetas del servidor de informes son públicas y suelen requerir que los usuarios dispongan de permisos avanzados para agregar o modificar su contenido. En cambio, la carpeta Mis informes es un área de trabajo que administra el propio usuario. Así, es posible agregar o quitar informes y carpetas, o guardar informes vinculados, con una configuración personalizada.  
  
 Conceptualmente, la carpeta Mis informes es similar a la carpeta Mis documentos del sistema de archivos Windows. Aunque cada usuario dispone de una carpeta denominada Mis informes, la carpeta a la que obtienen acceso cada uno de ellos es distinta de la de los demás. A excepción de los administradores del servidor de informes, el resto de los usuarios no pueden obtener acceso a la carpeta Mis informes de otros usuarios.  
  
 La función Mis informes es opcional y los administradores del servidor de informes pueden deshabilitarla. Cuando está habilitada, la carpeta Mis informes aparece en la carpeta Inicio, a la que se puede tener acceso mediante el Administrador de informes o un explorador web. Para obtener más información, vea [Buscar y ver informes en el Administrador de informes &#40;Generador de informes y SSRS&#41;](https://msdn.microsoft.com/library/dd255286.aspx).  
  
 En un servidor de informes configurado en el modo integrado de SharePoint, no hay equivalente a la carpeta Mis informes. Para obtener más información, vea [Buscar, ver y administrar informes &#40;Generador de informes y SSRS&#41;](../../reporting-services/report-builder/finding-viewing-and-managing-reports-report-builder-and-ssrs.md).  
  
> [!NOTE]  
>  [!INCLUDE[ssRBRDDup](../../includes/ssrbrddup-md.md)]  
  
## Modos de empleo de Mis informes  
 La carpeta Mis informes está vacía hasta que se agregan informes, carpetas u otros elementos. A continuación se indican algunos métodos para agregar contenido a Mis informes.  
  
-   Crear un informe vinculado personal y almacenarlo en Mis informes. No todos los informes permiten la vinculación. Para obtener más información, vea [Crear un informe vinculado](../../reporting-services/reports/create-a-linked-report.md).  
  
-   Cargar un archivo de definición de informe (.rdl), un archivo de modelo de informe (.smdl) u otros archivos del sistema de archivos. Puede cargarse cualquier archivo, pero el servidor de informes solamente procesa los archivos con la extensión .rdl o .smdl. Para obtener más información, vea Definiciones de informe en la [documentación de Reporting Services](http://go.microsoft.com/fwlink/?linkid=121312), en los Libros en pantalla de SQL Server y en [Cargar un archivo o un informe &#40;Administrador de informes&#41;](../../reporting-services/reports/upload-a-file-or-report-report-manager.md).  
  
-   Crear y publicar sus propios informes en Mis informes. Para obtener más información, vea [Vista de diseño de informe &#40;Generador de informes&#41;](../../reporting-services/report-builder/report-design-view-report-builder.md).  
  
 Por lo general, los permisos para la carpeta Mis informes le permiten que sea usted mismo quien administre la carpeta. Sin embargo, siempre es el administrador del servidor de informes quien determina en última instancia las tareas que pueden realizar los usuarios. Si no tiene permisos suficientes para trabajar con la carpeta Mis informes, póngase en contacto con el administrador del servidor de informes.  
  
## Realizar búsquedas en Mis informes  
 Al realizar búsquedas en una base de datos del servidor de informes, el contenido de la carpeta Mis informes también se incluye en la búsqueda y se excluye el de las carpetas Mis informes de los otros usuarios. Los resultados de la búsqueda solo muestran los informes a los que se tiene acceso.  
  
## Vea también  
 [Buscar, ver y administrar informes &#40;Generador de informes y SSRS&#41;](../../reporting-services/report-builder/finding-viewing-and-managing-reports-report-builder-and-ssrs.md)  
  
  