---
title: "Conectarse a un repositorio MDS (complemento MDS para Excel) | Microsoft Docs"
ms.custom: ""
ms.date: "03/01/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "master-data-services"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 8f427312-4c09-4c8b-b9f9-8b235557a74b
caps.latest.revision: 12
author: "sabotta"
ms.author: "carlasab"
manager: "jhubbard"
caps.handback.revision: 12
---
# Conectarse a un repositorio MDS (complemento MDS para Excel)
  En el [!INCLUDE[ssMDSshort](../../includes/ssmdsshort-md.md)][!INCLUDE[ssMDSXLS](../../includes/ssmdsxls-md.md)], debe conectarse a un repositorio MDS para poder cargar o publicar datos.  
  
## Requisitos previos  
 Para realizar este procedimiento:  
  
-   Debe disponer de permiso de acceso al área funcional **Explorador** .  
  
### Para conectarse a un repositorio MDS  
  
1.  En MDS [!INCLUDE[ssMDSXLS](../../includes/ssmdsxls-md.md)], en la pestaña **Datos maestros** , en el grupo **Conectar y cargar** , haga clic en la flecha situada debajo del botón **Conectar** y haga clic en **Administrar conexiones**.  
  
2.  En el cuadro de diálogo **Administrar conexiones** , en la sección **Nueva conexión** , haga clic en **Crear una nueva conexión**.  
  
3.  Haga clic en **Nueva**.  
  
4.  En el cuadro de diálogo **Agregar nueva conexión** , en el campo **Descripción** , escriba una descripción de la conexión. Esta conexión se muestra al hacer clic en la flecha situada debajo del botón **Conectar** en la barra de herramientas.  
  
5.  En el cuadro **Dirección del servidor MDS**, escriba la dirección URL de la aplicación web de [!INCLUDE[ssMDSmdm](../../includes/ssmdsmdm-md.md)], por ejemplo http://contoso/mds.  
  
    > [!NOTE]  
    >  Asegúrese de utilizar el nombre del equipo; no utilice “localhost”.  
  
6.  Haga clic en **Aceptar**. El nombre se muestra en la sección **Conexiones existentes** .  
  
7.  Opcionalmente, haga clic en **Probar** para probar la conexión. Se muestra un cuadro de diálogo de confirmación o de error. Haga clic en **Aceptar** para cerrarlo.  
  
8.  Haga clic en **Conectar**. Se muestra el panel **Master Data Services** .  
  
## Pasos siguientes  
  
-   [Export Data to Excel from Master Data Services](../../master-data-services/microsoft-excel-add-in/export-data-to-excel-from-master-data-services.md)  
  
-   [Filtrar los datos antes de exportar &#40;complemento MDS para Excel&#41;](../../master-data-services/microsoft-excel-add-in/filter-data-before-exporting-mds-add-in-for-excel.md)  
  
## Vea también  
 [Conexiones &#40;complemento MDS para Excel&#41;](../../master-data-services/microsoft-excel-add-in/connections-mds-add-in-for-excel.md)  
  
  