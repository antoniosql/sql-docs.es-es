---
title: "Exportar una aplicaci&#243;n de capa de datos | Microsoft Docs"
ms.custom: 
  - "SQL2016_New_Updated"
ms.date: "03/14/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dbe-data-tier-apps"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "sql13.swb.exportdac.progress.f1"
  - "sql13.swb.exportdac.summary.f1"
  - "sql13.swb.exportdac.results.f1"
  - "sql13.swb. exportdac.results.f1"
  - "sql13.swb. exportdac.summary.f1"
  - "sql13.swb. exportdac.settings.f1"
  - "sql13.swb.exportdac.welcome.f1"
  - "sql13.swb.exportdac.settings.f1"
helpviewer_keywords: 
  - "Cómo [DAC], exportar"
  - "asistente [DAC], exportar"
  - "DAC, exportar"
  - "aplicación de capa de datos [SQL Server], exportar"
ms.assetid: 61915bc5-0f5f-45ac-8cfe-3452bc185558
caps.latest.revision: 20
author: "JennieHubbard"
ms.author: "jhubbard"
manager: "jhubbard"
caps.handback.revision: 19
---
# Exportar una aplicaci&#243;n de capa de datos
  Al exportar una aplicación de capa de datos (DAC) o base de datos implementada se crea un archivo de exportación que incluye las definiciones de los objetos de la base de datos y todos los datos contenidos en las tablas. El archivo de exportación se podrá importar a otra instancia de [!INCLUDE[ssDE](../../includes/ssde-md.md)] o a [!INCLUDE[ssSDSFull](../../includes/sssdsfull-md.md)]. Las operaciones de exportación-importación se pueden combinar para migrar una DAC de una instancia a otra, crear un archivo o crear una copia local de una base de datos implementada en [!INCLUDE[ssSDS](../../includes/sssds-md.md)].  
  
## Antes de comenzar  
 El proceso de exportación compila un archivo de exportación DAC en dos fases.  
  
1.  La exportación genera una definición de DAC en el archivo de exportación, archivo BACPAC, de la misma forma que un extracto de DAC genera una definición de DAC en un archivo de paquete DAC. La definición de DAC exportada incluye todos los objetos de la base de datos actual. Si el proceso de exportación se ejecuta en una base de datos que se implementó originalmente a partir de una DAC y se realizaron cambios directamente en la base de datos tras la implementación, la definición exportada coincide con el objeto establecido en la base de datos, no con lo definido en la DAC original.  
  
2.  La exportación masiva copia los datos de todas las tablas de la base de datos y los incorpora en el archivo de exportación.  
  
 El proceso de exportación establece la versión de DAC en 1.0.0.0 y la descripción de DAC en el archivo de exportación en una cadena vacía. Si la base de datos se implementó a partir de una DAC, la definición de DAC del archivo de exportación contiene el nombre asignado a DAC original; de lo contrario, el nombre de la DAC se establece el nombre de la base de datos.  
  
 Hay una aplicación de ejemplo en las prácticas de [!INCLUDE[ssSDS](../../includes/sssds-md.md)] que se pueden usar para probar la exportación e importación de DAC y bases de datos. Para obtener instrucciones acerca de cómo descargar y usar el ejemplo, vea [Importación y exportación de bases de datos para base de datos de Windows Azure SQL](http://go.microsoft.com/fwlink/?LinkId=219404).  
  
###  <a name="LimitationsRestrictions"></a> Limitaciones y restricciones  
 Una DAC o base de datos solo se puede extraer de una base de datos de [!INCLUDE[ssSDS](../../includes/sssds-md.md)] o [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] Service Pack 4 (SP4) o posterior.  
  
 No puede exportar una base de datos que tenga objetos que no se admiten en una DAC, o usuarios contenidos. Para obtener más información acerca de los objetos admitidos por una DAC, vea [DAC Support For SQL Server Objects and Versions](../../relational-databases/data-tier-applications/dac-support-for-sql-server-objects-and-versions.md).  
  
###  <a name="Permissions"></a> Permisos  
 La exportación de una DAC requiere al menos permisos ALTER ANY LOGIN y VIEW DEFINITION en el ámbito de la base de datos, así como permisos SELECT en **sys.sql_expression_dependencies**. La exportación de una DAC la pueden realizar los miembros del rol fijo de servidor securityadmin que sean también miembros del rol fijo de base de datos database_owner en la base de datos de la que se exporta la DAC. Los miembros del rol fijo de servidor sysadmin o de la cuenta de administrador del sistema de SQL Server integrada denominada **sa** también pueden exportar una DAC.  
  
##  <a name="UsingDeployDACWizard"></a> Usar el Asistente Exportar aplicación de capa de datos  
 **Para exportar una DAC mediante un asistente**  
  
1.  Conéctese con la instancia de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], ya sea local o en [!INCLUDE[ssSDS](../../includes/sssds-md.md)].  
  
2.  En el **Explorador de objetos**, expanda el nodo para la instancia de la que dese exportar la DAC.  
  
3.  Haga clic con el botón secundario en el nombre de la base de datos.  
  
4.  Haga clic en **Tareas** y seleccione **Exportar aplicación de capa de datos**.  
  
5.  Complete los cuadros de diálogo del asistente:  
  
    -   [Página Introducción](#Introduction)  
  
    -   [Página Exportar configuraciones](#Export_settings)  
  
    -   [Página Validación](#Validation)  
  
    -   [Página Resumen](#Summary)  
  
    -   [Página Progreso](#Progress)  
  
    -   [Página Resultados](#Results)  
  
##  <a name="Introduction"></a> Página Introducción  
 Esta página describe los pasos para el Asistente Exportar aplicación de capa de datos.  
  
 **Opciones**  
  
 **No volver a mostrar esta página.** - Active la casilla para que la página Introducción deje de mostrarse en el futuro.  
  
 **Siguiente**: avanza a la página **Seleccionar paquete DAC**.  
  
 **Cancelar** ; cancela la operación y cierra el asistente.  
  
##  <a name="Export_settings"></a> Página Exportar configuraciones  
 En esta página se puede especificar la ubicación donde se desea crear el archivo BACPAC.  
  
-   **Guardar en disco local**: crea un archivo BACPAC en un directorio del equipo local. Haga clic en **Examinar…** para navegar por el equipo local, o especifique la ruta de acceso en el espacio proporcionado. El nombre de ruta de acceso debe incluir un nombre de archivo y la extensión .bacpac.  
  
-   **Guardar en Windows Azure**: crea un archivo BACPAC en un contenedor de Windows Azure. Debe conectarse a un contenedor de Windows Azure para validar esta opción. Observe que esta opción también requiere que se especifique un directorio local para el archivo temporal. Tenga en cuenta que el archivo temporal se creará en la ubicación especificada y permanecerá en ella una vez completada la operación.  
  
 Para especificar un subconjunto de tablas para exportar, utilice la opción **Avanzadas** .  
  
##  <a name="Validation"></a> Página Validación  
 La página de validación se utiliza para revisar los problemas que bloquean la operación. Para continuar, resuelva los problemas de bloqueo y, después, haga clic en **Volver a ejecutar la validación** para asegurarse de que la validación es correcta.  
  
 Para continuar, haga clic en **Siguiente**.  
  
##  <a name="Summary"></a> Página Resumen  
 Esta página se utiliza para revisar los valores de origen y de destino especificados de la operación. Para completar la operación de exportación mediante los valores especificados, haga clic en **Finalizar**. Para cancelar la operación de exportación y salir del asistente, haga clic en **Cancelar**.  
  
##  <a name="Progress"></a> Página Progreso  
 En esta página se muestra una barra de progreso que indica el estado de la operación. Para ver el estado detallado, haga clic en la opción **Ver detalles** .  
  
##  <a name="Results"></a> Página Resultados  
 En esta página se notifica la corrección o el error de la operación de exportación, mostrando los resultados de cada acción. Cualquier acción que encontrara un error tendrá un vínculo en la columna **Resultado** . Haga clic en el vínculo para ver un informe del error para esa acción.  
  
 Haga clic en **Finalizar** para cerrar el asistente.  
  
##  <a name="NetApp"></a> Mediante una aplicación de .Net Framework  
 **Para exportar una DAC mediante el método Export() en una aplicación .Net Framework**  
  
 Para obtener un ejemplo de código, descargue la aplicación de ejemplo de DAC en [Codeplex](http://go.microsoft.com/fwlink/?LinkId=219575).  
  
1.  Cree un objeto SMO Server y establézcalo en la instancia que contiene la DAC que se va a exportar.  
  
2.  Abra un objeto **ServerConnection** y conéctese a la misma instancia.  
  
3.  Use el método de **Export** de tipo **Microsoft.SqlServer.Management.Dac.DacStore** para exportar la DAC. Especifique el nombre de la DAC que se exportará y la ruta de acceso a la carpeta donde se va a guardar el archivo de exportación.  
  
## Vea también  
 [Aplicaciones de capa de datos](../../relational-databases/data-tier-applications/data-tier-applications.md)   
 [Extraer una DAC de una base de datos](../../relational-databases/data-tier-applications/extract-a-dac-from-a-database.md)  
  
  