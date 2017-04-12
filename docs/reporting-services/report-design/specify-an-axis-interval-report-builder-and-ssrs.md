---
title: "Especificar un intervalo de eje (Generador de informes y SSRS) | Microsoft Docs"
ms.custom: ""
ms.date: "09/02/2016"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "reporting-services-sharepoint"
  - "reporting-services-native"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: ae46712d-a5bf-44c0-9929-e30ccc1e7e33
caps.latest.revision: 14
author: "maggiesMSFT"
ms.author: "maggies"
manager: "erikre"
caps.handback.revision: 12
---
# Especificar un intervalo de eje (Generador de informes y SSRS)
Aprenda a cambiar el número de etiquetas y las marcas de graduación en el eje de categorías (X) de un gráfico; para ello, establezca el intervalo de eje de un informe paginado de [!INCLUDE[ssRSnoversion_md](../../includes/ssrsnoversion-md.md)].
 
En el eje de valores (normalmente el eje Y), los intervalos de eje proporcionan una medida coherente de los puntos de datos representados en el gráfico. 

Pero en el eje de categorías (normalmente el eje X), a veces un intervalo de eje automático genera categorías sin etiquetas de eje. Puede especificar el número de intervalos que quiere en la propiedad Intervalo del eje. [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] calcula el número de intervalos en tiempo de ejecución, según los datos del conjunto de resultados. Para más información sobre cómo se calculan los intervalos de eje, consulte [Aplicar formato a las etiquetas de los ejes de un gráfico](../../reporting-services/report-design/formatting-axis-labels-on-a-chart-report-builder-and-ssrs.md).  

Para probar la configuración del intervalo de eje con datos de ejemplo, consulte [Tutorial: Agregar un gráfico de columnas a un informe](Tutorial:%20Add%20a%20Column%20Chart%20to%20Your%20Report%20\(Report%20Builder\).md).
  
> [!NOTE]  
>  El eje de categorías normalmente es el eje horizontal o eje X. Sin embargo, en el caso de los gráficos de barras, el eje de categorías es el eje vertical o eje Y.  
>
> Este tema no se aplica a lo siguiente:
>-   Valores de fecha u hora en el eje de categorías. De forma predeterminada, los valores de tipo **DateTime** aparecen como días. Puede especificar un intervalo de fecha u hora distinto, como un intervalo mensual o de hora. Para más información, consulte [Aplicar formato de fecha o de a las etiquetas de los ejes](../../reporting-services/report-design/format-axis-labels-as-dates-or-currencies-report-builder-and-ssrs.md).  
>-  Gráficos circulares, de anillo, de embudo ni piramidales, ya que no tienen ejes. 
  
## Para mostrar todas las etiquetas de categoría en el eje X  

En este gráfico de columnas, el intervalo de etiqueta horizontal está definido en automático.

![report-builder-column-chart-preview-x-axis-interval-auto](../../reporting-services/report-design/media/report-builder-column-chart-preview-x-axis-interval-auto.png)
  
1.  Haga clic con el botón derecho en el eje de categorías y haga clic en **Propiedades del eje horizontal**.   

    ![report-builder-column-chart-x-axis-labels](../../reporting-services/report-design/media/report-builder-column-chart-x-axis-labels.png)
  
2.  En el cuadro de diálogo **Propiedades del eje horizontal** > pestaña **Opciones del eje**, establezca el valor de **Intervalo** en **1** para mostrar cada etiqueta de grupo de categorías. Para mostrar cualquier otra etiqueta de grupo de categorías en el eje X, escriba **2**. 

     ![report-builder-column-chart-x-axis-interval-one](../../reporting-services/report-design/media/report-builder-column-chart-x-axis-interval-one.png)
  
3.  [!INCLUDE[clickOK](../../includes/clickok-md.md)]  

    El gráfico de columnas ahora muestra todas sus etiquetas del eje horizontal.

    ![report-builder-column-chart-preview-x-axis-interval-one](../../reporting-services/report-design/media/report-builder-column-chart-preview-x-axis-interval-one.png)
  
    > [!NOTE]  
    >  Cuando establece un intervalo de eje, se deshabilita todo el etiquetado automático. Si especifica un valor para el intervalo de eje, puede ver un comportamiento imprevisible del etiquetado en función del número de categorías existentes en el eje de categorías.  

## Cambiar el intervalo de etiqueta en el panel Propiedades

También puede establecer el intervalo de etiqueta en el panel Propiedades.

1.  En la vista Diseño del informe, haga clic en el gráfico y, luego, seleccione las etiquetas del eje horizontal.

3. En el panel Propiedades, establezca LabelInterval en **1**.

    ![report-builder-column-chart-set-label-interval](../../reporting-services/media/report-builder-column-chart-set-label-interval.png)

    El gráfico tiene el mismo aspecto en la vista Diseño. 
    
5.  Haga clic en **Ejecutar** para obtener la vista previa del informe.

    ![report-builder-column-chart-label-interval-one-preview](../../reporting-services/media/report-builder-column-chart-label-interval-one-preview.png)
    
    Ahora el gráfico muestra todas sus etiquetas.
  
## Para habilitar el cálculo de un intervalo variable en un eje  

De manera predeterminada, [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] establece el intervalo de eje en automático. Este procedimiento explica cómo puede volver a establecerlo en el valor predeterminado. 
  
1.  Haga clic con el botón derecho en el eje del gráfico que quiera cambiar y, después, haga clic en **Propiedades del eje**. 
  
2.  En el cuadro de diálogo **Propiedades del eje horizontal** > pestaña **Opciones del eje**, establezca el valor de **Intervalo** en **Automático**. El gráfico mostrará el número óptimo de etiquetas de categoría que quepan a lo largo del eje.  
  
3.  [!INCLUDE[clickOK](../../includes/clickok-md.md)]  
  
## Vea también  
 [Aplicar formato a un gráfico &#40;Generador de informes y SSRS&#41;](../../reporting-services/report-design/formatting-a-chart-report-builder-and-ssrs.md)   
 [Aplicar formato a los puntos de datos de un gráfico &#40;Generador de informes y SSRS&#41;](../../reporting-services/report-design/formatting-data-points-on-a-chart-report-builder-and-ssrs.md)   
 [Ordenar datos en una región de datos &#40;Generador de informes y SSRS&#41;](../../reporting-services/report-design/sort-data-in-a-data-region-report-builder-and-ssrs.md)   
 [Cuadro de diálogo Propiedades del eje, Opciones del eje &#40;Generador de informes y SSRS&#41;](../Topic/Axis%20Properties%20Dialog%20Box,%20Axis%20Options%20\(Report%20Builder%20and%20SSRS\).md)   
 [Especificar una escala logarítmica &#40;Generador de informes y SSRS&#41;](../../reporting-services/report-design/specify-a-logarithmic-scale-report-builder-and-ssrs.md)   
 [Trazar datos en un eje secundario &#40;Generador de informes y SSRS&#41;](../../reporting-services/report-design/plot-data-on-a-secondary-axis-report-builder-and-ssrs.md)  
  
  