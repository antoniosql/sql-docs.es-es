---
title: SQLExtendedFetch (biblioteca de cursores) | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- SQLExtendedFetch function [ODBC], Cursor Library
ms.assetid: 06fbf06f-127b-475c-b636-7b784918475d
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 600d90c14ae8b08a4860f3cff49c1615a9587063
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/01/2018
ms.locfileid: "47798223"
---
# <a name="sqlextendedfetch-cursor-library"></a>SQLExtendedFetch (biblioteca de cursores)
> [!IMPORTANT]  
>  Esta característica se quitará en una versión futura de Windows. Evite usar esta característica en nuevos trabajos de desarrollo y piense en modificar las aplicaciones que actualmente utilizan esta característica. Microsoft recomienda usar la funcionalidad de cursor del controlador.  
  
 Este tema describe el uso de la **SQLExtendedFetch** función en la biblioteca de cursores. Para obtener información general sobre **SQLExtendedFetch**, consulte [función SQLExtendedFetch](../../../odbc/reference/syntax/sqlextendedfetch-function.md).  
  
 La biblioteca de cursores implementa **SQLExtendedFetch** llamando repetidamente **SQLFetch** en el controlador.  
  
 Admite las llamadas a la biblioteca de cursores **SQLExtendedFetch** con un *FetchOrientation* de SQL_FETCH_BOOKMARK.  
  
 Cuando se utiliza la biblioteca de cursores, las llamadas a **SQLExtendedFetch** no se pueden mezclar con las llamadas a **SQLFetchScroll** o **SQLFetch**.
