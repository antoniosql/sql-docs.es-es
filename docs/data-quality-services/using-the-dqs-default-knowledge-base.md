---
title: Usar la base de conocimiento predeterminada de DQS | Microsoft Docs
ms.custom: ''
ms.date: 07/31/2012
ms.prod: sql
ms.prod_service: data-quality-services
ms.reviewer: ''
ms.technology:
- data-quality-services
ms.topic: conceptual
ms.assetid: b36af13b-9fcc-4168-bb92-214d600b1c93
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.openlocfilehash: bf9ada2b925846426df4bbe0b0f630bf1cb9c110
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 10/01/2018
ms.locfileid: "47803204"
---
# <a name="using-the-dqs-default-knowledge-base"></a>Utilizar la base de conocimiento predeterminada de DQS

[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

  En este tema se describe la base de conocimiento predeterminada, **Datos de DQS**, que se instala con [!INCLUDE[ssDQSnoversion](../includes/ssdqsnoversion-md.md)] (DQS). Esta es una base de conocimiento predeterminada pregenerada que contiene los dominios siguientes:  
  
-   **País o región**: contiene nombres largos (nombre válido según se designe por el país o región) y cortos convencionales (nombre común usado en las listas, en el mapa, etc.), la abreviatura de dos letras, la abreviatura de tres letras y el código de tres dígitos para cada ubicación.  El valor principal se establece en el nombre de país largo.  
  
-   **País o región (tres letras iniciales)**: contiene nombres largos (nombre válido según se designe por el país o región) y cortos convencionales (nombre común usado en las listas, en el mapa, etc.), la abreviatura de dos letras, la abreviatura de tres letras y el código de tres dígitos para cada ubicación.  Los valores iniciales se establecen en la abreviatura de tres letras del condado.  
  
-   **País o región (dos letras iniciales)**: contiene nombres largos (nombre válido según se designe por el país o región) y cortos convencionales (nombre común usado en las listas, en el mapa, etc.), la abreviatura de dos letras, la abreviatura de tres letras y el código de tres dígitos para cada ubicación.  El valor principal se establece en la abreviatura de dos letras del país.  
  
-   **EE.UU.) - Condados**: contiene una lista de los condados de Estados Unidos.  
  
-   **EE.UU.) - Apellido**: contiene una lista de apellidos que aparecen al menos 100 veces en el censo de 2000.  
  
-   **EE.UU.) - lugares**: contiene una lista de sitios para los 50 estados, el distrito de Columbia y Puerto Rico extraidos del censo de 2010.  
  
-   **EE. UU.) - estados**: contiene el nombre largo convencional (oficial) y la abreviatura de dos letras para cada estado de EE. UU. El valor principal se establece en el nombre convencional de estado.  
  
-   **EE. UU.) - estados (encabezado de 2 letras)**: contiene el nombre largo convencional (oficial) y la abreviatura de dos letras para cada estado de EE. UU. El valor inicial se establece en la abreviatura de dos letras del nombre de estado.  
  
## <a name="using-the-default-knowledge-base"></a>Usar la base de conocimiento predeterminada  
 Puede utilizar la base de conocimiento predeterminado DQS, DQS Data, de las maneras siguientes:  
  
-   Inicie y ejecute rápidamente un proyecto de limpieza de calidad de los datos mediante la base de conocimiento predeterminada sin tener primero que crear una base de conocimiento de DQS.  
  
-   Ejecute las actividades Administración de dominio, Detección de conocimiento, Coincidencia de directivas en la base de conocimiento predeterminada. Para ello, haga clic en **Abrir base de conocimiento** en la [Data Quality Client Home Screen](../data-quality-services/data-quality-client-home-screen.md), seleccione la base de conocimiento **Datos de DQS** en la pantalla **Abrir base de conocimiento** y, a continuación, seleccione la actividad necesaria en el área **Seleccione la actividad** . Haga clic en **Siguiente** para continuar.  
  
-   Cree una base de conocimiento con la base de conocimiento predeterminada. Para crear una base de conocimiento a partir de una base de conocimiento existente, vea [Create a Knowledge Base](../data-quality-services/create-a-knowledge-base.md).  
  
-   Úsela en el [componente Limpieza de DQS de Integration Services](http://go.microsoft.com/fwlink/?LinkId=238830) y [Complemento Master Data Services para Excel](../master-data-services/microsoft-excel-add-in/data-quality-matching-in-the-mds-add-in-for-excel.md).  
  
## <a name="see-also"></a>Ver también  
 [Bases de conocimiento y dominios de DQS](../data-quality-services/dqs-knowledge-bases-and-domains.md)  
  
  
