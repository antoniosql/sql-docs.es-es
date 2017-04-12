---
title: "Reutilizaci&#243;n del flujo de control en paquetes mediante el uso de elementos del paquete de flujo de control | Microsoft Docs"
ms.custom: 
  - "SQL2016_New_Updated"
ms.date: "03/01/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "integration-services"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "sql13.dts.designer.toolboxcontrolflowtemplate.f1"
  - "sql13.dts.designer.addcopyexistingtemplate.f1"
  - "sql13.dts.designer.addcopyexistingpackagepart.f1"
  - "sql13.dts.designer.packagepart.general.f1"
ms.assetid: 1edc91d9-1fab-4fe5-aed3-6f581fe32c18
caps.latest.revision: 14
author: "douglaslMS"
ms.author: "douglasl"
manager: "jhubbard"
caps.handback.revision: 14
---
# Reutilizaci&#243;n del flujo de control en paquetes mediante el uso de elementos del paquete de flujo de control
  Guarde un contenedor o una tarea de flujo de control que use con frecuencia en un archivo de elemento independiente —un archivo “.dtsxp”— y reutilícelos varias veces en uno o varios paquetes mediante elementos del paquete de flujo de control. Esta reusabilidad facilita el diseño y el mantenimiento de paquetes SSIS.  
  
## Creación de un nuevo elemento del paquete de flujo de control  
 Para crear un nuevo elemento del paquete de flujo de control, en el Explorador de soluciones, expanda la carpeta **Package Parts** . Haga clic con el botón derecho en **Flujo de control** y seleccione **Nuevo elemento de paquete de flujo de control**.  
  
 ![Create a new control flow template](../integration-services/media/control-flow-templates-create-new.png "Create a new control flow template")  
  
 Se creará un archivo de elemento con la extensión ".dtsxp" en la carpeta **Elementos del paquete | Flujo de control**. A la vez, también se agrega un nuevo elemento con el mismo nombre al cuadro de herramientas de SSIS. (El elemento del cuadro de herramientas solo está visible mientras tenga un proyecto que contenga el elemento del paquete abierto en Visual Studio).  
  
 ![Control flow templates in toolbox](../integration-services/media/control-flow-templates-in-toolbox.png "Control flow templates in toolbox")  
  
## Diseño de un elemento del paquete de flujo de control  
 Para abrir el editor de elemento del paquete, haga doble clic en el archivo del elemento en el Explorador de soluciones. Puede diseñar el elemento de la misma forma que diseñaría un paquete.  
  
 ![Step 1 of control flow template design](../integration-services/media/control-flow-template-design-step-1.png "Step 1 of control flow template design")  
  
 ![Step 2 of control flow template design](../integration-services/media/control-flow-template-design-step-2.png "Step 2 of control flow template design")  
  
 Los elementos del paquete de flujo de control presentan las siguientes limitaciones:  
  
-   Un elemento solo puede tener un contenedor o tarea de nivel superior. Si desea incluir varios contenedores o tareas, colóquelos en un solo contenedor de secuencias.  
  
-   No se puede ejecutar o depurar un elemento directamente en el diseñador.  
  
## Adición de un elemento del paquete de flujo de control existente a un paquete  
 Puede reutilizar elementos guardados en el proyecto de Integration Services actual o en uno distinto.  
  
-   Para reutilizar un elemento que forme parte del proyecto actual, arrástrelo desde el cuadro de herramientas y suéltelo donde desee.  
  
-   Para reutilizar un elemento que forma parte de un proyecto diferente, utilice el comando **Add Existing Control Flow Package Part** (Agregar elemento del paquete de flujo de control existente).  
  
### Acción de arrastrar y soltar un elemento del paquete de flujo de control  
 Para reutilizar un elemento en un proyecto, basta con arrastrarlo desde el cuadro de herramientas y soltarlo donde desee, al igual que sucede con cualquier otro contenedor o tarea. Puede arrastrar el elemento y colocarlo en el paquete varias veces para reutilizar la lógica en varias ubicaciones de este. Utilice este método para reutilizar un elemento que forme parte del proyecto actual.  
  
 ![Add a control flow template to a package](../integration-services/media/control-flow-templates-add-to-package.png "Add a control flow template to a package")  
  
 ![Package with multiple control flow templates](../integration-services/media/control-flow-templates-in-package.png "Package with multiple control flow templates")  
  
 Cuando se guarda el paquete, el Diseñador SSIS comprueba si hay alguna instancia del elemento en él.  
  
-   Si el paquete contiene instancias del elemento, el diseñador genera un nuevo archivo .dtsx.designer que contiene toda la información relacionada con el elemento.  
  
-   Si el paquete no utiliza elementos, el diseñador elimina cualquier archivo .dtsx.designer que se haya creado con anterioridad para el paquete (es decir, cualquier archivo .dtsx.designer que tenga el mismo nombre que el paquete).  
  
 ![Solution Explorer with control flow templates](../integration-services/media/control-flow-templates-in-solution-explorer.png "Solution Explorer with control flow templates")  
  
### Adición de una copia de un elemento del paquete de flujo de control existente o una referencia a un elemento existente  
 Para agregar una copia de un elemento existente en el sistema de archivos a un paquete, en el Explorador de soluciones, expanda la carpeta **Package Parts** . Haga clic con el botón derecho en **Flujo de control** y seleccione **Agregar elemento de paquete de flujo de control existente**.  
  
 ![Add a new control flow templates from the menu](../integration-services/media/control-flow-templates-add-from-menu.png "Add a new control flow templates from the menu")  
  
 ![Add Copy of Existing Templates dialog box](../integration-services/media/control-flow-templates-add-copy-dialog.png "Add Copy of Existing Templates dialog box")  
  
 **Opciones**  
  
 **Package Part path (Ruta del elemento del paquete)**  
 Escriba la ruta de acceso al archivo del elemento, o bien haga clic en el botón Examinar (…) y busque el archivo del elemento que quiera copiar o al que quiera hacer referencia.  
  
 **Add as a reference (Agregar como referencia)**  
 -   Si se activa, el elemento se agrega al proyecto de Integration Services como una referencia. Active esta casilla si desea hacer referencia a una sola copia de un archivo de elemento en varios proyectos de Integration Services.  
  
-   Si está desactivada, se agrega una copia del archivo del elemento al proyecto.  
  
## Configuración de un elemento del paquete de flujo de control  
 Para configurar elementos del paquete de flujo de control después de haberlos agregado al flujo de control de un paquete, utilice el cuadro de diálogo **Package Part Configuration**  (Configuración de elemento del paquete).  
  
#### Para abrir el cuadro de diálogo Package Part Configuration (Configuración de elemento del paquete), siga estos pasos:  
  
1.  Si desea configura una instancia del elemento, haga doble clic en ella en el flujo de control. También puede hacer clic con el botón derecho en la instancia del elemento y seleccionar **Editar**. Se abrirá el cuadro de diálogo **Package Part Configuration** (Configuración de elemento del paquete).  
  
2.  Configurar las propiedades y los administradores de conexiones para la instancia del elemento.  
  
### Pestaña Propiedades  
 Utilice la pestaña **Propiedades** del cuadro de diálogo **Package Part Configuration**  (Configuración de elemento del paquete) para especificar las propiedades del elemento.  
  
 ![Properties tab of the Template Configuration dialog box](../integration-services/media/template-configuration-properties-tab.png "Properties tab of the Template Configuration dialog box")  
  
 En la jerarquía de vista de árbol del panel izquierdo se enumeran todas las propiedades configurables de la instancia del elemento.  
  
-   Si está desactivada, la propiedad no está configurada en la instancia del elemento. La instancia del elemento utiliza el valor predeterminado para la propiedad, que se define en el elemento del paquete de flujo de control.  
  
-   Si está activada, el valor que escriba o seleccione reemplaza al valor predeterminado.  
  
 En la tabla del panel derecho se enumeran las propiedades que se deben configurar.  
  
-   **Ruta de acceso de la propiedad**. La ruta de acceso de la propiedad.  
  
-   **Tipo de propiedad**. El tipo de datos de la propiedad.  
  
-   **Valor**. El valor configurado. Este valor invalida el valor predeterminado.  
  
### Pestaña Administradores de conexiones  
 Utilice la pestaña **Administradores de conexiones** del cuadro de diálogo **Package Part Configuration**  (Configuración de elemento del paquete) para especificar las propiedades de los administradores de conexiones de la instancia del elemento.  
  
 ![Connection Managers tab of the Template Configuration dialog box](../integration-services/media/template-configuration-connection-managers-tab.png "Connection Managers tab of the Template Configuration dialog box")  
  
 En la tabla del panel izquierdo se enumeran todos los administradores de conexiones definidos en el elemento del flujo de control. Elija el administrador de conexiones que desea configurar.  
  
 En la lista del panel derecho se muestran las propiedades del administrador de conexiones seleccionado.  
  
-   **Establecer**. Las casillas estarán activadas si la propiedad en cuestión está configurada para la instancia del elemento.  
  
-   **Nombre de propiedad**. El nombre de la propiedad.  
  
-   **Valor**. El valor configurado. Este valor invalida el valor predeterminado.  
  
## Eliminación de un elemento de flujo de control  
 Para eliminar un elemento, en el Explorador de soluciones, haga clic con el botón derecho en el elemento y, después, seleccione **Eliminar**. Seleccione **Aceptar** para confirmar la eliminación o **Cancelar** para conservar el elemento.  
  
 Si elimina un elemento de un proyecto, se elimina de forma permanente del sistema de archivos y no se puede restaurar.  
  
> [!NOTE]  
>  Si quiere quitar un elemento de un proyecto de Integration Services, pero seguir usándolo en otros proyectos, use la opción **Excluir del proyecto** en lugar de **Eliminar**.  
  
## Los elementos del paquete son solo una característica de tiempo de diseño.  
 Los elementos del paquete son estrictamente una característica de tiempo de diseño. El Diseñador SSIS crea, abre, guarda y actualiza elementos, y agrega, configura o elimina instancias del elemento de un paquete. Sin embargo, el runtime de SSIS no es consciente de los elementos. Así es cómo el diseñador logra esta separación.  
  
-   El diseñador guarda las instancias del elemento del paquete con sus propiedades configuradas en un archivo “.dtsx.designer”.  
  
-   Cuando el diseñador guarda dicho archivo, también extrae el contenido de los elementos a los que se hace referencia en este archivo y reemplaza las instancias del elemento del paquete con el contenido de los elementos.  
  
-   Por último, todo el contenido, que ya no incluye información del elemento, se vuelve a guardar el archivo de paquete “.dtsx”. Este es el archivo que ejecuta el runtime de SSIS.  
  
 En el siguiente diagrama se muestra la relación entre los elementos (archivos “.dtsx”), el Diseñador de SSIS y el runtime de SSIS.  
  
 ![Control flow templates files and flow](../integration-services/media/control-flow-templates-intro.png "Control flow templates files and flow")  
  
  