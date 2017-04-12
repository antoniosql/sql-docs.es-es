---
title: "Ver entradas del registro en la ventana Registrar eventos | Microsoft Docs"
ms.custom: ""
ms.date: "03/01/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "integration-services"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "registros [Integration Services], ver"
  - "paquetes de Integration Services, registros"
  - "paquetes [Integration Services], registros"
ms.assetid: c02123c3-67fc-4370-ad14-91ed259f1873
caps.latest.revision: 21
author: "douglaslMS"
ms.author: "douglasl"
manager: "jhubbard"
caps.handback.revision: 21
---
# Ver entradas del registro en la ventana Registrar eventos
  En este procedimiento se describe cómo ejecutar un paquete y ver las entradas de registro que escribe. Se pueden ver las entradas del registro en tiempo real. Las entradas del registro escritas en la ventana **Registrar eventos** también se pueden copiar y guardar para futuros análisis.  
  
 No es necesario escribir las entradas en un registro para que se escriban en la ventana **Registrar eventos** .  
  
### Para ver entradas del registro  
  
1.  En [!INCLUDE[ssBIDevStudio](../../includes/ssbidevstudio-md.md)], abra el proyecto de [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] que contiene el paquete que desea.  
  
2.  En el menú **SSIS** , haga clic en **Registrar eventos**. Opcionalmente, se puede mostrar la ventana **Registrar eventos** asignando el comando View.LogEvents a una combinación de teclas elegida por el usuario en la página **Teclado** del cuadro de diálogo **Opciones** .  
  
3.  En el menú **Depurar** , haga clic en **Iniciar depuración**.  
  
     A medida que el tiempo de ejecución encuentra eventos y mensajes personalizados que están habilitados para el registro, las entradas del registro para cada evento o mensaje se escriben en la ventana **Registrar eventos** .  
  
4.  En el menú **Depurar** , haga clic en **Detener depuración**.  
  
     Las entradas del registro permanecen disponibles en la ventana **Registrar eventos** hasta que vuelve a ejecutar el paquete, ejecuta un paquete diferente o cierra [!INCLUDE[ssBIDevStudio](../../includes/ssbidevstudio-md.md)].  
  
5.  Vea las entradas del registro en la ventana **Registrar eventos** .  
  
6.  También puede hacer clic en las entradas del registro que quiere copiar, hacer clic con el botón derecho y luego hacer clic en **Copiar**.  
  
7.  O bien, puede hacer doble clic en una entrada del registro y, en el cuadro de diálogo **Entrada del registro**, ver los detalles de una única entrada.  
  
8.  En el cuadro de diálogo **Entrada del registro** , haga clic en las flechas arriba y abajo para mostrar la entrada del registro anterior o siguiente, y haga clic en el icono de copiar para copiar la entrada del registro.  
  
9. Abra un editor de texto, pegue y luego guarde la entrada del registro en un archivo de texto.  
  
## Vea también  
 [Registro de Integration Services &#40;SSIS&#41;](../../integration-services/performance/integration-services-ssis-logging.md)  
  
  