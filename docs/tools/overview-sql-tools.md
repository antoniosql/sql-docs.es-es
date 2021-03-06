---
title: Herramientas SQL y utilidades para SQL Server, base de datos SQL Azure y Azure SQL Data Warehouse | Microsoft Docs
ms.custom: ''
ms.date: 02/22/2018
ms.prod: sql
ms.prod_service: sql-tools
ms.component: misc
ms.reviewer: ''
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: conceptual
ms.assetid: ''
caps.latest.revision: 0
author: stevestein
ms.author: sstein
manager: craigg
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017'
ms.openlocfilehash: a8f31d6479a0a2ba5e5f19f6a0739ab6322de92b
ms.sourcegitcommit: e02c28b0b59531bb2e4f361d7f4950b21904fb74
ms.translationtype: MTE75
ms.contentlocale: es-ES
ms.lasthandoff: 08/02/2018
ms.locfileid: "39458989"
---
# <a name="sql-tools-and-utilities-for-sql-server-azure-sql-database-and-azure-sql-data-warehouse"></a>Herramientas SQL y utilidades para SQL Server, base de datos SQL Azure y Azure SQL Data Warehouse
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

Para administrar (consulta, monitor, etc.) necesitan una herramienta de la base de datos. Hay varias herramientas de base de datos. Mientras que las bases de datos pueden ejecutarse en la nube, en Windows o en [Linux](../linux/sql-server-linux-overview.md), la herramienta no tiene que ejecutarse en la misma plataforma que la base de datos. 

En este artículo se proporciona información sobre las herramientas disponibles para trabajar con las bases de datos SQL. 


## <a name="tools-to-run-queries-and-manage-databases"></a>Herramientas para ejecutar consultas y administrar bases de datos  

| Herramienta | Descripción |
|:--|:--|
| [[!INCLUDE[name-sos](../includes/name-sos.md)]](../sql-operations-studio/download.md) | [!INCLUDE[name-sos](../includes/name-sos-short.md)] es una herramienta gratuita y ligera, para administrar las bases de datos siempre que se están ejecutando. Esta versión preliminar proporciona características de administración de base de datos, incluido un editor de Transact-SQL extendido y personalizables información sobre el estado operativo de las bases de datos. **[!INCLUDE[name-sos](../includes/name-sos-short.md)] se ejecuta en Windows, macOS y Linux**.|
| [SQL Server Management Studio (SSMS)](../ssms/download-sql-server-management-studio-ssms.md) | Use SQL Server Management Studio (SSMS) para consultar, diseñar y administrar SQL Server, Azure SQL Database y Azure SQL Data Warehouse. **SSMS se ejecuta en Windows**.|
| [SQL Server Data Tools (SSDT)](../ssdt/download-sql-server-data-tools-ssdt.md) | Convierta Visual Studio en un entorno de desarrollo eficaz para SQL Server, Azure SQL Database y Azure SQL Data Warehouse. **SSDT se ejecuta en Windows**.|
|[MSSQL-cli](mssql-cli.md)|MSSQL-cli es una herramienta de línea de comandos interactiva para realizar consultas en SQL Server. **MSSQL-cli que se ejecuta en Windows, macOS y Linux**|
| [Visual Studio Code](https://code.visualstudio.com/)| Después de instalar Visual Studio Code, instale el [extensión mssql](https://marketplace.visualstudio.com/items?itemName=ms-mssql.mssql) para el desarrollo de Microsoft SQL Server, Azure SQL Database y SQL Data Warehouse. **Código de Visual Studio se ejecuta en Windows, macOS y Linux**.|

## <a name="which-tool-should-i-choose"></a>¿Qué herramienta debo elegir?

- ¿Desea administrar una instancia de SQL Server o la base de datos, en un editor ligero en Windows, Linux o Mac? Seleccionar [[!INCLUDE[name-sos](../includes/name-sos.md)]](../sql-operations-studio/download.md)
- ¿Desea administrar una instancia de SQL Server o la base de datos en Windows con compatibilidad total con la interfaz gráfica de usuario? Seleccionar [SQL Server Management Studio (SSMS)](../ssms/download-sql-server-management-studio-ssms.md)
- ¿Desea crear o mantener el código de la base de datos, incluida la validación en tiempo de compilación, refactorización y el diseñador se admiten en Windows? Seleccionar [SQL Server Data Tools (SSDT)](../ssdt/download-sql-server-data-tools-ssdt.md)
- ¿Si desea consultar SQL Server con una herramienta de línea de comandos que incluye IntelliSense, sintaxis alto-iluminación, y mucho más? Elija [mssql-cli](mssql-cli.md)
- ¿Desea escribir secuencias de comandos de T-SQL en un editor ligero en Windows, Linux o Mac? Elija [Visual Studio Code](https://code.visualstudio.com/) y [extensión mssql](https://marketplace.visualstudio.com/items?itemName=ms-mssql.mssql)

## <a name="additional-tools"></a>Herramientas adicionales

| Herramienta | Descripción |
|:--|:--|
| [Administrador de configuración](../tools/configuration-manager/sql-server-configuration-manager-help.md) | Use el Administrador de configuración de SQL Server para configurar servicios de SQL Server y configurar la conectividad de red. Configuration Manager se ejecuta en Windows|
|[MSSQL-conf](../linux/sql-server-linux-configure-mssql-conf.md)|Use mssql-conf para configurar SQL Server que se ejecutan en Linux.|
| [SQL Server Migration Assistant](../ssma/sql-server-migration-assistant.md) | Use Microsoft SQL Server Migration Assistant para automatizar la migración de bases de datos a SQL Server desde Microsoft Access, DB2, MySQL, Oracle y Sybase.|
| [Distributed Replay](../tools/distributed-replay/install-distributed-replay-overview.md) | Use la característica Distributed Replay para ayudarle a evaluar el impacto de las actualizaciones futuras de SQL Server. También puede usar Distributed Replay para ayudar a evaluar el impacto de hardware y actualizaciones del sistema operativo y la optimización de SQL Server. |
| [ssbdiagnose](../tools/ssbdiagnose/ssbdiagnose-utility-service-broker.md) | La utilidad ssbdiagnose informa de problemas en las conversaciones de Service Broker o la configuración de servicios de Service Broker. |


## <a name="command-line-utilities"></a>Utilidades de la línea de comandos

  Las utilidades de la línea de comandos permiten incluir en scripts las operaciones de [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]. La siguiente tabla contiene una lista de utilidades de símbolo del sistema que se suministran junto con [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)].  
  
|**Utilidad**|**Descripción**|**Instalada en**|  
|-----------------|---------------------|----------------------|  
|[bcp (utilidad)](../tools/bcp-utility.md)|Se usa para copiar datos entre una instancia de [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] y un archivo de datos en un formato especificado por el usuario.|\<*unidad*:>\Archivos de programa\\[!INCLUDE[msCoName](../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]\Client SDK\ODBC\110\Tools\Binn|  
|[dta (utilidad)](../tools/dta/dta-utility.md)|Se utiliza para analizar una carga de trabajo y recomendar estructuras de diseño físico para optimizar el rendimiento del servidor para esa carga de trabajo.|[!INCLUDE[ssInstallPathVar](../includes/ssinstallpathvar-md.md)]Tools\Binn|  
|[dtexec (utilidad)](../integration-services/packages/dtexec-utility.md)|Se usa para configurar y ejecutar un paquete de [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] . Una versión de interfaz de usuario de esta utilidad del símbolo del sistema se denomina **DTExecUI**y abre la utilidad de ejecución de paquetes.|[!INCLUDE[ssInstallPathVar](../includes/ssinstallpathvar-md.md)]DTS\Binn|  
|[dtutil (utilidad)](../integration-services/dtutil-utility.md)|Se usa para administrar paquetes SSIS.|[!INCLUDE[ssInstallPathVar](../includes/ssinstallpathvar-md.md)]DTS\Binn|  
|[Implementar soluciones de modelos con la utilidad de implementación](../analysis-services/multidimensional-models/deploy-model-solutions-with-the-deployment-utility.md)|Se utiliza para implementar proyectos de [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] en instancias de [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)].|[!INCLUDE[ssInstallPathVar](../includes/ssinstallpathvar-md.md)]Tools\Binn\VShell\Common7\IDE|  
|[MSSQL-generador de scripts (versión preliminar)](https://blogs.technet.microsoft.com/dataplatforminsider/2017/05/17/try-new-sql-server-command-line-tools-to-generate-t-sql-scripts-and-monitor-dynamic-management-views/)|Se utiliza para generar scripts de creación y T-SQL INSERT para los objetos de base de datos en SQL Server, Azure SQL Database y Azure SQL Data Warehouse.|Consulte nuestra [repositorio de GitHub](https://github.com/Microsoft/sql-xplat-cli) para obtener información de descarga y uso.| 
|[osql (utilidad)](../tools/osql-utility.md)|Permite especificar instrucciones, procedimientos del sistema y archivos de scripts de [!INCLUDE[tsql](../includes/tsql-md.md)] en el símbolo del sistema.|[!INCLUDE[ssInstallPathVar](../includes/ssinstallpathvar-md.md)]Tools\Binn|  
|[Analizador (utilidad)](../tools/profiler-utility.md)|Se utiliza para iniciar [!INCLUDE[ssSqlProfiler](../includes/sssqlprofiler-md.md)] desde un símbolo del sistema.|[!INCLUDE[ssInstallPathVar](../includes/ssinstallpathvar-md.md)]Tools\Binn|  
|[Utilidad RS.exe &#40;SSRS&#41;](../reporting-services/tools/rs-exe-utility-ssrs.md)|Se utiliza para ejecutar scripts diseñados para administrar servidores de informes de [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] .|[!INCLUDE[ssInstallPathVar](../includes/ssinstallpathvar-md.md)]Tools\Binn|  
|[rsconfig (utilidad) &#40;SSRS&#41;](../reporting-services/tools/rsconfig-utility-ssrs.md)|Se utiliza para configurar una conexión de servidor de informes.|[!INCLUDE[ssInstallPathVar](../includes/ssinstallpathvar-md.md)]Tools\Binn|  
|[rskeymgmt (utilidad) &#40;SSRS&#41;](../reporting-services/tools/rskeymgmt-utility-ssrs.md)|Se utiliza para administrar claves de cifrado en un servidor de informes.|[!INCLUDE[ssInstallPathVar](../includes/ssinstallpathvar-md.md)]Tools\Binn|  
|[sqlagent90 (aplicación)](../tools/sqlagent90-application.md)|Se usa para iniciar el Agente de [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] desde un símbolo del sistema.|\<unidad>:\Archivos de programa\Microsoft SQL Server\\<*nombre_instancia*>\MSSQL\Binn|  
|[sqlcmd Utility](../tools/sqlcmd-utility.md)|Permite especificar instrucciones, procedimientos del sistema y archivos de scripts de [!INCLUDE[tsql](../includes/tsql-md.md)] en el símbolo del sistema.|\<*unidad*:>\Archivos de programa\\[!INCLUDE[msCoName](../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]\Client SDK\ODBC\110\Tools\Binn|  
|[SQLdiag (utilidad)](../tools/sqldiag-utility.md)|Se usa para recopilar información de diagnóstico para el Servicio de soporte y atención al cliente de [!INCLUDE[msCoName](../includes/msconame-md.md)] .|[!INCLUDE[ssInstallPathVar](../includes/ssinstallpathvar-md.md)]Tools\Binn|  
|[sqllogship (aplicación)](../tools/sqllogship-application.md)|Las aplicaciones lo utilizan para realizar operaciones de copia de seguridad, copia y restauración, y tareas de limpieza asociadas en una configuración de trasvase de registros sin ejecutar trabajos de copia de seguridad, copia y restauración.|[!INCLUDE[ssInstallPathVar](../includes/ssinstallpathvar-md.md)]Tools\Binn|  
|[SqlLocalDB (utilidad)](../tools/sqllocaldb-utility.md)|Un modo de ejecución de [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] destinado a los desarrolladores de programas.|[!INCLUDE[ssInstallPathVar](../includes/ssinstallpathvar-md.md)]Tools\Binn\|  
|[sqlmaint (utilidad)](../tools/sqlmaint-utility.md)|Se usa para ejecutar los planes de mantenimiento de bases de datos creados en versiones anteriores de [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)].|\<unidad>:\Archivos de programa\Microsoft SQL Server\MSSQL13.MSSQLSERVER\MSSQL\Binn|  
|[Utilidad sqlps](../tools/sqlps-utility.md)|Se usa para ejecutar comandos y scripts de PowerShell. Carga y registra el proveedor de PowerShell de [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] y los cmdlets.|[!INCLUDE[ssInstallPathVar](../includes/ssinstallpathvar-md.md)]Tools\Binn|  
|[sqlservr](../tools/sqlservr-application.md)|Se usa para iniciar y detener una instancia de [!INCLUDE[ssDE](../includes/ssde-md.md)] desde el símbolo del sistema para solucionar problemas.|\<unidad>:\Archivos de programa\Microsoft SQL Server\MSSQL13.MSSQLSERVER\MSSQL\Binn|  
|[Ssms (Utilidad)](../tools/sql-server-management-studio/ssms-utility.md)|Se utiliza para iniciar [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] desde un símbolo del sistema.|[!INCLUDE[ssInstallPathVar](../includes/ssinstallpathvar-md.md)]Tools\Binn\VSShell\Common7\IDE|  
|[tablediff (utilidad)](../tools/tablediff-utility.md)|Se utiliza para comparar los datos de dos tablas y ver si no convergen, lo que es útil para solucionar problemas de una topología de replicación.|[!INCLUDE[ssInstallPathVar](../includes/ssinstallpathvar-md.md)]COM|  

## <a name="sql-command-prompt-utilities-syntax-conventions"></a>Convenciones de la sintaxis de las utilidades del símbolo del sistema de SQL  
  
|**Convención**|**Se usa para**|  
|--------------------|------------------|  
|UPPERCASE|Instrucciones y términos usados en el sistema operativo.|  
|`monospace`|Comandos y código de programación de ejemplo.|  
|*cursiva*|Parámetros proporcionados por el usuario.|  
|**Negrita**|Comandos, parámetros y otros elementos de sintaxis que deben escribirse exactamente como se muestran.|  



