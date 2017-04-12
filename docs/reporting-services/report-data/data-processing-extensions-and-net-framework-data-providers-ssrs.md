---
title: "Extensiones de procesamiento de datos y proveedores de datos de .NET Framework (SSRS) | Microsoft Docs"
ms.custom: ""
ms.date: "03/14/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "reporting-services-sharepoint"
  - "reporting-services-native"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "informes [Reporting Services], datos"
  - "extensiones de procesamiento de datos [Reporting Services]"
  - "proveedores de datos [Reporting Services]"
  - "recuperación de datos [Reporting Services]"
  - "Reporting Services, orígenes de datos"
  - "datos del informe [Generador de informes], acceder"
ms.assetid: 42a5afb5-f4c8-4957-b1fd-77bf39afa5be
caps.latest.revision: 19
author: "guyinacube"
ms.author: "asaxton"
manager: "erikre"
caps.handback.revision: 19
---
# Extensiones de procesamiento de datos y proveedores de datos de .NET Framework (SSRS)
  Una extensión de procesamiento de datos de [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] es un componente instalado con [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)], diseñado para recuperar datos de un tipo de origen de datos específico y proporcionar una funcionalidad adicional para admitir el diseño y el procesamiento de informes. Un proveedor de datos de [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] es un componente disponible de [!INCLUDE[msCoName](../../includes/msconame-md.md)] o de terceros que admite interfaces <xref:System.Data> que permiten recuperar y modificar datos de un tipo de origen de datos específico.  
  
## Descripción de las extensiones de procesamiento de datos  
 Una extensión de procesamiento de datos de [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] admite un subconjunto de las interfaces de <xref:System.Data>. Las extensiones de procesamiento de datos solo requieren acceso de lectura a un origen de datos, de modo que no se implementen las interfaces para escritura y actualización. Cada extensión de procesamiento de datos puede incluir características personalizadas para admitir el procesamiento de informes. Por ejemplo, una extensión de procesamiento de datos podría admitir los tipos siguientes de características:  
  
-   Administración de credenciales independientemente de la cadena de conexión  
  
-   Admisión de parámetros de varios valores  
  
-   Recuperación de agregados de servidor, que se calculan en el origen de datos  
  
-   Recuperación de propiedades y valores de datos del origen de datos  
  
## Descripción de un proveedor de datos  
 Un proveedor de datos de [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] (a veces conocido como controlador) admite un conjunto estándar de las interfaces <xref:System.Data> para leer, escribir y actualizar datos en un origen de datos. Se puede usar un proveedor de datos cuando no hay ninguna extensión de procesamiento de datos disponible para un tipo específico de origen de datos. Hay disponibles diversos proveedores de datos de [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] de terceros.  
  
 Debido a que [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] tiene una arquitectura de proveedor de datos extensible, puede generar una extensión de procesamiento de datos personalizada para incluir la funcionalidad adicional proporcionada por las extensiones de procesamiento de datos de [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] . Para obtener más información, vea [Implementing a Data Processing Extension](../../reporting-services/extensions/data-processing/implementing-a-data-processing-extension.md). Para las extensiones de procesamiento de datos de terceros, vea la documentación incluida con ellas.  
  
> [!NOTE]  
>  Se debe instalar y registrar un proveedor de datos de [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] o una extensión de procesamiento de datos personalizada para poder tener acceso a los datos de un origen de datos. La extensión de procesamiento de datos se debe instalar y registrar tanto en el cliente de informes para crear el informe como en el servidor de informes para ver el informe publicado. No todos los proveedores de datos están diseñados para funcionar en un entorno de servidor. Para obtener más información, vea [Registrar un proveedor de datos estándar de .NET Framework &#40;SSRS&#41;](../../reporting-services/report-data/register-a-standard-net-framework-data-provider-ssrs.md) e [Implementar una extensión de procesamiento de datos](../../reporting-services/extensions/data-processing/deploying-a-data-processing-extension.md).  
  
## Vea también  
 [Introducción a las extensiones de procesamiento de datos](../../reporting-services/extensions/data-processing/data-processing-extensions-overview.md)   
 [Conjuntos de datos incrustados y compartidos de informe &#40;Generador de informes y SSRS&#41;](../../reporting-services/report-data/report-embedded-datasets-and-shared-datasets-report-builder-and-ssrs.md)  
  
  