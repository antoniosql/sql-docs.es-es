---
title: Novedades de Data Migration Assistant (SQL Server) | Microsoft Docs
ms.custom: ''
ms.date: 08/28/2018
ms.prod: sql
ms.prod_service: dma
ms.reviewer: ''
ms.technology: dma
ms.topic: conceptual
keywords: ''
helpviewer_keywords:
- Data Migration Assistant, new features
ms.assetid: ''
author: HJToland3
ms.author: rajpo
manager: craigg
ms.openlocfilehash: 31c75b46eb01e5d892a7930ab0bec84b19e02a54
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/01/2018
ms.locfileid: "47655663"
---
# <a name="whats-new-in-data-migration-assistant"></a>Novedades de Data Migration Assistant
En este artículo se enumera las adiciones en cada versión de Data Migration Assistant (DMA).

## <a name="dma-v40"></a>DMA v4.0
La versión v4.0 de DMA presenta la característica de recomendaciones de SKU de base de datos de SQL Azure, que permite a los usuarios identificar las mínimas recomendadas SKU de base de datos de SQL Azure en función de los contadores de rendimiento recopilados de los equipos que aloja las bases de datos. Esta característica proporciona recomendaciones relacionadas con los precios de nivel, el nivel de proceso y tamaño máximo de datos, así como el costo estimado por mes. También ofrece la posibilidad de aprovisionar todas las bases de datos a Azure de forma masiva.

> [!NOTE]
> Esta funcionalidad está actualmente esté disponible solo mediante la interfaz de línea de comandos (CLI). Compatibilidad con esta característica a través de la interfaz de usuario DMA está planeada para su entrega más adelante este año.

Para obtener detalles adicionales, consulte el artículo [identificar la SKU de base de datos SQL de Azure adecuada para la base de datos local](dma-sku-recommend-sql-db.md).

## <a name="dma-v36"></a>DMA v3.6
La versión 3.6 de DMA presenta "Corrección automática" para los objetos de esquema que se ven afectadas por los bloqueadores de migración más comunes.

Esta versión proporciona la reparación automática para el bloqueador de migración siguientes y problemas de cambio de comportamiento:
- Los objetos de esquema que utilizan la sintaxis de combinación no calificado.
- Los objetos de esquema que utilice la instrucción RAISEERROR heredada.
- Instrucciones SQL que usan el orden por entero Literal.

DMA realiza la conversión automática de esquemas para los objetos afectados por los problemas indicados y solicita al usuario confirmación antes de continuar con la conversión de esquema. Los usuarios pueden revisar los cambios de código sugerido y, a continuación, Aceptar o rechazar todas las conversiones para cualquier objeto de base de datos determinada.

DMA usa tecnología de síntesis de programa de Microsoft (PROSE) para sugerir que corrige el código. Obtenga más información sobre [PROSE](https://microsoft.github.io/prose/).

## <a name="dma-v35"></a>DMA v3.5
La versión 3.5 de DMA incluye las siguientes adiciones:
- Mejoras de rendimiento significativas para migrar a Azure SQL Database (pruebas comparativas indican que el proceso es cuatro veces más rápido que con versiones anteriores de DMA).
- La superficie de memoria se optimiza aún más para mejorar la estabilidad del flujo de trabajo de migración.
- La capacidad de omitir las evaluaciones durante las migraciones de datos y el esquema (si ya ha realizado la evaluación y direccionar los objetos de esquema importantes antes de la migración).
- Una corrección para solucionar un problema con la herramienta de bloqueo cuando se proporciona una ruta de acceso del recurso compartido de red no válido para los archivos de copia de seguridad, al realizar una actualización de una versión heredada de SQL Server locales a una versión posterior o SQL Server en máquinas virtuales de Azure.

## <a name="dma-v34"></a>3.4 DMA
La versión 3.4 de DMA incluye las siguientes adiciones:
- Compatibilidad con SQL Server 2017 como origen para las migraciones a Azure SQL Database.
- Mejoras de estabilidad, rendimiento y evaluación de la corrección de regla.

## <a name="dma-v33"></a>V3.3 DMA
La versión v3.3 de DMA permite la migración de una instancia de SQL Server local a la nueva versión de SQL Server 2017 en Windows y Linux. Aunque el flujo de trabajo de migración general para Windows y Linux es el mismo, la migración a SQL Server 2017 para Linux requiere algunas consideraciones adicionales.

### <a name="specifying-the-back-up-path"></a>Especifica la ruta de acceso de copia de seguridad
Linux y Windows usan formatos de ruta de acceso diferente. Como resultado, la migración a SQL Server 2017 en Linux requiere que el usuario proporcione versiones de la Windows y Linux de la ruta de acceso a la ubicación del archivo físico. Puede proporcionar ambas versiones de la ruta de acceso de maneras diferentes según la ubicación del archivo físico.
Si el archivo de copia de seguridad físico está en un equipo que ejecute:
- Linux, use un 'samba' comparte para compartir el archivo con otros equipos de la red.
- Windows, use el comando "mnt" montar el recurso compartido en el equipo que ejecuta Linux.

> [!NOTE]
> Detalles de uso de un recurso compartido de 'samba' o el comando "mnt" están fuera del ámbito de este artículo.

### <a name="migrating-windows-logins"></a>Migrar los inicios de sesión de Windows
Mientras la migración de los inicios de sesión de Active Directory (AD) es compatible oficialmente con SQL Server 2017 en Linux, requiere configuración adicional para funcionar correctamente. Consulte el artículo [autenticación de Active Directory con SQL Server en Linux](https://docs.microsoft.com/sql/linux/sql-server-linux-active-directory-authentication) para obtener información detallada acerca de cómo configurar los inicios de sesión de Active Directory en SQL Server 2017 en Linux. Después de realizar la configuración necesaria, el programa de instalación está completa y puede migrar los inicios de sesión de Active Directory como de costumbre. Autenticación de SQL estándar funciona según lo esperado sin ninguna configuración adicional.

## <a name="dma-v32"></a>V3.2 DMA
La versión v3.2 de DMA incluye las siguientes adiciones:

- Migración de esquema y los datos están habilitadas de bases de datos de SQL Server local a Azure SQL Database con un nuevo flujo de trabajo de migración.
- Durante la migración de esquema a Azure SQL Database, DMA scripts los objetos de base de datos de origen, proporciona instrucciones sobre cómo solucionar los posibles problemas de compatibilidad y, a continuación, implementa el esquema en Azure.

## <a name="dma-v31"></a>V3.1 DMA
La versión de v3.1 de DMA incluye las siguientes adiciones:

- Las recomendaciones de evaluación mejorada para bases de datos de SQL Azure en cuanto a las intercalaciones de base de datos, el uso de procedimientos almacenados del sistema no compatibles y objetos de CLR.
- Guía de evaluación para los niveles de compatibilidad 100 al migrar a Azure SQL Database, 110, 120 y 130.

## <a name="dma-v30"></a>DMA v3.0
La versión v3.0 de DMA amplía la evaluación de la base de datos SQL de Azure para proporcionar recomendaciones integrales para ayudar a solucionar problemas relacionados con:

- Problemas de bloqueo de migración.
- Parcialmente o las funciones y características no admitidas.

## <a name="dma-v21"></a>DMA v2.1
La versión de v2.1 de DMA incluye las siguientes adiciones:
- Compatibilidad de línea de comandos para ejecutar las evaluaciones en modo desatendido, lo que ayuda a ejecutar las evaluaciones a escala. Para obtener detalles adicionales, consulte el artículo [ejecutar Data Migration Assistant desde la línea de comandos](dma-commandline.md).
- Mejoras de rendimiento cuando los usuarios iniciarán y cerrar DMA.
- La capacidad de configurar el tiempo de espera de conexión de SQL. Para obtener detalles adicionales, consulte el artículo [opciones de configuración de Data Migration Assistant](dma-configurationsettings.md).

## <a name="dma-v20"></a>DMA v2.0
La versión de la versión 2.0 de DMA incluye recomendaciones de características de base de datos de Stretch mejoradas para proporcionar las tablas apropiadas de prioridades que maximicen el ahorro de almacenamiento.

## <a name="dma-v10"></a>DMA v1.0
La versión 1.0 de DMA es la versión inicial, y proporciona para:
- Detección de problemas que pueden afectar a una actualización a una versión local de SQL Server. Se describen todas las observaciones como problemas de compatibilidad y se clasifica por categorías en las siguientes áreas:
    - Cambios importantes
    - Cambios de comportamiento
    - Características en desuso
- Detección de nuevas características de la plataforma de SQL Server de destino que la base de datos puede beneficiarse de una actualización. Se describen todas las observaciones como recomendación de característica y se clasifica por categorías en las siguientes áreas:
    - Rendimiento
    - Seguridad
    - Storage
-   Experiencia de usuario moderna a realizar evaluaciones.

## <a name="see-also"></a>Vea también
[Información general de Data Migration Assistant](../dma/dma-overview.md)
