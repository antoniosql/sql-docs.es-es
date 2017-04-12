---
title: "Eliminar un grupo de cargas de trabajo | Microsoft Docs"
ms.custom: ""
ms.date: "03/03/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "database-engine"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "grupos de cargas de trabajo [SQL Server], eliminar"
  - "Regulador de recursos, eliminar grupo de cargas de trabajo"
ms.assetid: d5902c46-5c28-4ac1-8b56-cb4ca2b072d0
caps.latest.revision: 19
author: "JennieHubbard"
ms.author: "jhubbard"
manager: "jhubbard"
caps.handback.revision: 19
---
# Eliminar un grupo de cargas de trabajo
  Puede eliminar un grupo de cargas de trabajo o grupo de recursos de servidor mediante [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] o Transact-SQL.  
  
-   **Antes de empezar:**  [Limitaciones y restricciones](#LimitationsRestrictions), [Permisos](#Permissions)  
  
-   **Para eliminar un grupo de cargas de trabajo con:** [Explorador de objetos](#DelWGObjEx), [Propiedades del regulador de recursos](#DelWGRGProp), [Transact-SQL](#DelWGTSQL)  
  
##  <a name="BeforeYouBegin"></a> Antes de empezar  
 No puede eliminar un grupo de cargas de trabajo si contiene sesiones activas.  
  
###  <a name="LimitationsRestrictions"></a> Limitaciones y restricciones  
 Si un grupo de cargas de trabajo contiene sesiones activas, no se podrá eliminar ni mover el grupo de cargas de trabajo a otro grupo de recursos de servidor si se llama a la instrucción ALTER RESOURCE GOVERNOR RECONFIGURE para aplicar el cambio. Para evitar este problema, puede realizar una de las siguientes acciones:  
  
-   Espere hasta que se hayan desconectado todas las sesiones en el grupo afectado y, a continuación, vuelve a ejecutar la instrucción ALTER RESOURCE GOVERNOR RECONFIGURE.  
  
-   Detenga explícitamente las sesiones en el grupo afectado mediante el comando KILL y, a continuación, vuelva a ejecutar la instrucción ALTER RESOURCE GOVERNOR RECONFIGURE. Si decide que no quiere detener explícitamente las sesiones después de usar **Eliminar** pero antes de detener las sesiones activas, vuelva a crear el grupo usando el nombre original y mueva el grupo al grupo de recursos de servidor original.  
  
-   Reinicie el servidor. Una vez completado el proceso del reinicio, no se creará el grupo eliminado y un grupo movido utilizará la nueva asignación del grupo de recursos de servidor.  
  
###  <a name="Permissions"></a> Permisos  
 Eliminar un grupo de cargas de trabajo requiere un permiso CONTROL SERVER.  
  
##  <a name="DelWGObjEx"></a> Eliminar un grupo de carga de trabajo mediante el Explorador de objetos  
 **Para eliminar un grupo de cargas de trabajo mediante el Explorador de objetos**  
  
1.  En[!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], abra el Explorador de objetos y expanda de forma recursiva el nodo **Administración** hasta **Grupos de recursos de servidor**incluido.  
  
2.  Expanda de forma recursiva **Grupos de recursos** hasta e incluido el nodo **Grupos de carga de trabajo** en el grupo de recursos de servidor que contiene el grupo de cargas de trabajo que va a eliminar.  
  
3.  Haga clic con el botón derecho en el grupo de cargas de trabajo y, después, seleccione **Eliminar**.  
  
4.  En la ventana **Eliminar objeto** aparece el grupo de cargas de trabajo en la lista **Objeto que se va a eliminar** . Para eliminar el grupo de cargas de trabajo, haga clic en **Aceptar**.  
  
##  <a name="DelWGRGProp"></a> Eliminar un grupo de cargas de trabajo mediante Propiedades del regulador de recursos  
 **Para eliminar un grupo de cargas de trabajo mediante la página Propiedades del regulador de recursos**  
  
1.  En el Explorador de objetos, expanda de forma recursiva el nodo **Administración** hasta el nodo **Grupos de recursos de servidor**, éste incluido.  
  
2.  Haga clic con el botón derecho en el grupo de recursos de servidor que contiene el grupo de cargas de trabajo que va a eliminar y, después, haga clic en **Propiedades**. Se abre la página **Propiedades del regulador de recursos** .  
  
3.  En la ventana **Grupos de cargas de trabajo para grupos de recursos**, haga clic en la línea del grupo de cargas de trabajo que va a eliminar, haga clic con el botón derecho en la flecha derecha situada en el lado izquierdo de la línea y, después, haga clic en **Eliminar**.  
  
4.  Para eliminar el grupo de cargas de trabajo, haga clic en **Aceptar**.  
  
##  <a name="DelWGTSQL"></a> Eliminar un grupo de cargas de trabajo mediante Transact-SQL  
 **Para eliminar un grupo de cargas de trabajo utilizando Transact-SQL**  
  
1.  Ejecute la instrucción **DROP WORKLOAD GROUP** especificando el nombre del grupo de cargas de trabajo que desea eliminar.  
  
2.  Antes de emitir la instrucción **ALTER RESOURCE GOVERNOR RECONFIGURE** , compruebe que no hay ninguna solicitud activa en el grupo de cargas de trabajo que va a eliminar. Si hay solicitudes activas, **ALTER RESOURCE GOVERNOR** producirá un error. Para evitar este problema, puede realizar una de las siguientes acciones:  
  
    -   Espere hasta todas las sesiones del grupo de cargas de trabajo se hayan desconectado.  
  
    -   Detenga explícitamente las sesiones del grupo de cargas de trabajo mediante el comando **KILL** .  
  
    -   Reinicie el servidor. No se volverá a crear el grupo de cargas de trabajo.  
  
    -   En un escenario en el que ha emitido la instrucción **DROP WORKLOAD GROUP**, pero no quiere detener explícitamente las sesiones para aplicar el cambio, puede recrear el grupo si usa el mismo nombre que tenía antes de emitir la instrucción DROP y, después, lo mueve al grupo de recursos de servidor original.  
  
3.  Ejecute la instrucción **ALTER RESOURCE GOVERNOR RECONFIGURE** .  
  
### Ejemplo (Transact-SQL)  
 En el ejemplo siguiente se quita un grupo de cargas de trabajo denominado `groupAdhoc`.  
  
```  
DROP WORKLOAD GROUP groupAdhoc;  
GO  
ALTER RESOURCE GOVERNOR RECONFIGURE;  
GO  
```  
  
## Vea también  
 [Regulador de recursos](../../relational-databases/resource-governor/resource-governor.md)   
 [Crear un grupo de recursos de servidor](../../relational-databases/resource-governor/create-a-resource-pool.md)   
 [Crear un grupo de cargas de trabajo](../../relational-databases/resource-governor/create-a-workload-group.md)   
 [Eliminar un grupo de recursos de servidor](../../relational-databases/resource-governor/delete-a-resource-pool.md)   
 [DROP WORKLOAD GROUP &#40;Transact-SQL&#41;](../../t-sql/statements/drop-workload-group-transact-sql.md)   
 [DROP RESOURCE POOL &#40;Transact-SQL&#41;](../../t-sql/statements/drop-resource-pool-transact-sql.md)   
 [ALTER RESOURCE GOVERNOR &#40;Transact-SQL&#41;](../../t-sql/statements/alter-resource-governor-transact-sql.md)  
  
  