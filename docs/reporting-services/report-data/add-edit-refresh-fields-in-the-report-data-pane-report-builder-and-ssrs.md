---
title: "Agregar, editar y actualizar campos en el panel Datos de informe (Generador de informes y SSRS) | Microsoft Docs"
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
ms.assetid: 2e36f0fe-8100-4513-b169-14d611646f81
caps.latest.revision: 7
author: "guyinacube"
ms.author: "asaxton"
manager: "erikre"
caps.handback.revision: 7
---
# Agregar, editar y actualizar campos en el panel Datos de informe (Generador de informes y SSRS)
  Los campos de conjunto de datos son la colección integrada de nombres de campo que representan los datos que se devuelven cuando una consulta de conjunto de datos se ejecuta en un origen de datos externo.  
  
 En un conjunto de datos incrustado, los campos de conjunto de datos son los que se crean cuando se termina de generar una consulta y se cierra el panel del Diseñador de consultas y los campos calculados que se crean.  
  
 En un conjunto de datos compartido, los campos de conjunto de datos son los de la definición del conjunto de datos compartido cuando se agregó al informe. Aunque la consulta del conjunto de datos compartido del servidor de informes siempre se utiliza al ejecutar el informe, la lista de campos de conjunto de datos del informe es estática.  
  
 Use **Actualizar campos** para actualizar la lista de campos en el informe de modo que coincida con la lista actual de campos de la consulta del conjunto de datos compartido. Actualizar la lista de campos no afecta a los campos calculados que defina en un informe.  
  
> [!NOTE]  
>  [!INCLUDE[ssRBRDDup](../../includes/ssrbrddup-md.md)]  
  
### Para agregar un campo de consulta  
  
1.  En el panel Datos de informe, haga clic con el botón derecho en el conjunto de datos y, después, haga clic en **Agregar campo de consulta**.  
  
    > [!NOTE]  
    >  Si no puede ver el panel Datos de informe, en el menú **Ver**, haga clic en **Datos de informe**.  
  
2.  En la página **Campos** del cuadro de diálogo **Propiedades del conjunto de datos** , haga clic en **Agregar**y, a continuación, haga clic en **Campo de consulta**. En la parte inferior de la cuadrícula se agrega una nueva fila.  
  
3.  En el cuadro de texto **Nombre de campo** , escriba el nombre del campo.  
  
    > [!NOTE]  
    >  El nombre debe ser único en el conjunto de datos.  
  
4.  En el cuadro de texto **Origen del campo** , escriba el nombre de un campo existente en el origen de datos.  
  
5.  [!INCLUDE[clickOK](../../includes/clickok-md.md)]  
  
### Para agregar un campo calculado  
  
1.  En el panel Datos de informe, haga clic con el botón derecho en el conjunto de datos y, después, haga clic en **Agregar campo calculado**.  
  
2.  En la página **Campos** del cuadro de diálogo **Propiedades del conjunto de datos** , haga clic en **Agregar**y, a continuación, haga clic en **Campo calculado**. En la parte inferior de la cuadrícula se agrega una nueva fila.  
  
3.  En el cuadro de texto **Nombre de campo** , escriba el nombre del campo.  
  
    > [!NOTE]  
    >  El nombre debe ser único en el conjunto de datos.  
  
4.  En el cuadro de texto **Origen del campo** , escriba la expresión para el campo. Haga clic en el botón Expresión (**fx**) para generar una expresión.  
  
    > [!NOTE]  
    >  La expresión de un campo calculado no puede contener agregados ni referencias a elementos de informe.  
  
5.  [!INCLUDE[clickOK](../../includes/clickok-md.md)]  
  
### Para modificar un campo de consulta o un campo de conjunto de datos  
  
1.  En el panel Datos de informe, haga clic con el botón derecho en el campo y, después, haga clic en **Propiedades del campo**.  
  
2.  En la página **Campos** del cuadro de diálogo **Propiedades del conjunto de datos** , haga clic en un campo existente para seleccionar la fila.  
  
3.  Cambie el nombre o el valor del campo.  
  
4.  [!INCLUDE[clickOK](../../includes/clickok-md.md)]  
  
### Para eliminar un campo de consulta o un campo calculado  
  
1.  En el panel Datos de informe, expanda el conjunto de datos para mostrar la colección de campos.  
  
2.  Haga clic con el botón derecho en el campo que quiera quitar y, después, haga clic en **Eliminar**.  
  
### Para actualizar la colección de campos en el panel Datos de informe para un conjunto de datos compartido  
  
1.  En el panel Datos de informe, haga clic con el botón derecho en el conjunto de datos y, después, haga clic en **Consulta**.  
  
2.  Haga clic en **Actualizar campos**.  
  
     En el servidor de informes, la consulta del conjunto de datos compartido se ejecuta y devuelve la colección de campos actual.  
  
## Vea también  
 [Colección Campos del conjunto de datos &#40;Generador de informes y SSRS&#41;](../../reporting-services/report-data/dataset-fields-collection-report-builder-and-ssrs.md)   
 [Conjuntos de datos de informe &#40;SSRS&#41;](../../reporting-services/report-data/report-datasets-ssrs.md)   
 [Conjuntos de datos incrustados y compartidos de informe &#40;Generador de informes y SSRS&#41;](../../reporting-services/report-data/report-embedded-datasets-and-shared-datasets-report-builder-and-ssrs.md)   
 [Diseñadores de consultas de Reporting Services](../Topic/Reporting%20Services%20Query%20Designers.md)   
 [Diseñadores de consultas &#40;Generador de informes&#41;](../Topic/Query%20Designers%20\(Report%20Builder\).md)  
  
  