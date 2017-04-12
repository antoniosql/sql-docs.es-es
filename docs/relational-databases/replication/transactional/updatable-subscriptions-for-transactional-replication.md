---
title: "Suscripciones actualizables para replicaci&#243;n transaccional | Microsoft Docs"
ms.custom: ""
ms.date: "07/21/2016"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "replication"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "replicación transaccional, suscripciones actualizables"
  - "suscripciones actualizables, acerca de las suscripciones actualizables"
  - "suscripciones de actualización en cola [replicación de SQL Server]"
  - "suscripciones de actualización inmediata"
  - "suscripciones [replicación de SQL Server], actualizables"
  - "updatable subscriptions"
ms.assetid: 8eec95cb-3a11-436e-bcee-bdcd05aa5c5a
caps.latest.revision: 60
author: "BYHAM"
ms.author: "rickbyh"
manager: "jhubbard"
caps.handback.revision: 60
---
# Suscripciones actualizables para replicaci&#243;n transaccional
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx_md](../../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

    
> [!NOTE]  
>  Esta característica sigue siendo compatible con las versiones de [!INCLUDE[ssNoVersion_md](../../../includes/ssnoversion-md.md)] entre 2012 y 2016. [!INCLUDE[ssNoteDepFutureAvoid](../../../includes/ssnotedepfutureavoid-md.md)]  
  
 La replicación transaccional admite actualizaciones en los suscriptores mediante suscripciones actualizables y replicación punto a punto. A continuación se indican los dos tipos de suscripciones actualizables:  
  
-   Actualización inmediata. Para actualizar datos en el suscriptor, el publicador y el suscriptor deben estar conectados.  
  
-   Actualización en cola. No es necesario que el publicador y el suscriptor estén conectados para actualizar datos en el suscriptor. Las actualizaciones se pueden realizar mientras el suscriptor o el publicador están sin conexión.  
  
 Cuando se actualizan datos en un suscriptor, primero se propagan al publicador y después a los otros suscriptores. Si se utiliza la actualización inmediata, los cambios se propagan inmediatamente mediante el protocolo de confirmación en dos fases. Si se utiliza la actualización en cola, los cambios se almacenan en una cola; después, las transacciones en cola se aplican de forma asincrónica en el publicador cuando exista conectividad de red. Debido a que las actualizaciones se propagan de forma asincrónica al publicador, los mismos datos pueden haber sido actualizados por el publicador o por otro suscriptor y, por lo tanto, se pueden producir conflictos al aplicar las actualizaciones. Los conflictos se detectan y resuelven según una directiva de resolución de conflictos establecida al crear la publicación.  
  
 Si crea una publicación transaccional con suscripciones actualizables en el Asistente para nueva publicación, se habilitan la actualización inmediata y la actualización en cola. Si crea una publicación con procedimientos almacenados, puede habilitar una o ambas opciones. Al crear una suscripción a la publicación, se especifica el modo de actualización que se va a utilizar. Después, puede cambiar entre modos de actualización si es necesario. Para obtener más información, vea la sección siguiente "Cambio entre modos de actualización".  
  
 Para habilitar las suscripciones actualizables para publicaciones transaccionales, [Enable Updating Subscriptions for Transactional Publications](../../../relational-databases/replication/publish/enable-updating-subscriptions-for-transactional-publications.md)  
  
 Para crear suscripciones actualizables para publicaciones transaccionales, consulte [crear una suscripción actualizable a una publicación transaccional (Management Studio)](../../../relational-databases/replication/publish/create-an-updatable-subscription-to-a-transactional-publication.md) 
  
## Cambio entre modos de actualización  
 Al utilizar las suscripciones actualizables, puede especificar que una suscripción utilice un modo de actualización y, después, cambie al otro si la aplicación lo requiere. Por ejemplo, puede especificar que una suscripción utilice la actualización inmediata, pero cambie a la actualización en cola si se pierde la conectividad de red por un error del sistema.  
  
> [!NOTE]  
>  La replicación no cambia automáticamente entre modos de actualización. Debe establecer el modo de actualización a través de SQL Server Management Studio o la aplicación debe llamar [sp_setreplfailovermode &#40; Transact-SQL &#41;](../../../relational-databases/system-stored-procedures/sp-setreplfailovermode-transact-sql.md) Para cambiar entre modos.  
  
 Si se cambia de actualización inmediata a actualización en cola, no puede volver a cambiar a la actualización inmediata hasta que el suscriptor y el publicador estén conectados y el Agente de lectura de cola haya aplicado todos los mensajes pendientes en la cola al publicador.  
  
 **Para cambiar entre modos de actualización**  
  
 Para cambiar entre modos de actualización, debe habilitar la publicación y suscripción para ambos modos de actualización y, a continuación, cambiar entre ellos si es necesario. Para obtener más información, vea  
[Cambiar entre modos de actualización para una suscripción transaccional actualizable](../../../relational-databases/replication/administration/switch-between-update-modes-for-an-updatable-transactional-subscription.md).  
  
### Consideraciones para el uso de suscripciones actualizables  
  
-   Después de haber habilitado una publicación para suscripciones de actualización o suscripciones de actualización en cola, no se puede deshabilitar la opción para la publicación (aunque las suscripciones no necesitan utilizarla). Para deshabilitar la opción, se debe eliminar la publicación y crear una nueva.  
  
-   No se admiten los datos de republicación.  
  
-   La replicación agrega la **msrepl_tran_version** columna a las tablas publicadas con fines de seguimiento. A consecuencia de esta columna adicional, todas las instrucciones **INSERT** deben incluir una lista de columnas.  
  
-   Para realizar cambios de esquema en una tabla de una publicación que admita suscripciones de actualización, se debe detener toda la actividad de la tabla en el publicador y los suscriptores, y se deben propagar los cambios de datos pendientes a todos los nodos antes de realizar cambios de esquema. De esta forma se garantiza que las transacciones pendientes no entren en conflicto con el cambio de esquema pendiente. Una vez propagados los cambios de esquema a todos los nodos, se puede reiniciar la actividad en las tablas publicadas. Para más información, vea [Poner en modo inactivo una topología de replicación &#40;programación de la replicación con Transact-SQL&#41;](../../../relational-databases/replication/administration/quiesce-a-replication-topology-replication-transact-sql-programming.md).  
  
-   Si planea cambiar entre modos de actualización, el Agente de lectura de cola se debe ejecutar una vez como mínimo después de que se haya inicializado la suscripción (de manera predeterminada, el Agente de lectura de cola se ejecuta de forma continua).  
  
-   Si se realiza una partición horizontal de la base de datos de suscriptor y hay filas en la partición que existen en el suscriptor, pero no en el publicador, el suscriptor no podrá actualizar las filas preexistentes. Si intenta actualizar estas filas, se obtendrá un error. Las filas deben eliminarse de la tabla y agregarse después al publicador.  

-   La replicación transaccional con suscriptores actualizables de puesta en cola podría experimentar un rendimiento lento cuando se utilizan los índices filtrados únicos. Si se produce un conflicto en un artículo que tiene índices filtrados únicos, a continuación, la resolución de conflictos conduciría a adicionales elimina e inserta en el suscriptor para las filas que no están cubiertas por el índice filtrado único.
  
### Actualizaciones en el suscriptor  
  
-   Las actualizaciones en el suscriptor se propagan al publicador incluso cuando una suscripción ha expirado o está inactiva. Asegúrese de que tales suscripciones se quitan o reinicializan.  
  
-   Si se usan columnas **TIMESTAMP** o **IDENTITY** , y se replican como sus tipos de datos base, los valores de estas columnas no se deben actualizar en el suscriptor.  
  
-   Los suscriptores no pueden actualizar ni insertar **texto**, **ntext** o **imagen** valores porque no es posible leer desde las tablas insertadas o eliminadas dentro de los desencadenadores de seguimiento de cambios de replicación. Igualmente, los suscriptores no pueden actualizar o insertar valores **text** o **image** utilizando **WRITETEXT** o **UPDATETEXT** porque el publicador sobrescribe los datos. En su lugar, puede dividir las columnas **text** y **image** en una tabla independiente y modificar las dos tablas en una transacción.  
  
     Para actualizar los objetos grandes en un suscriptor, utilice los tipos de datos **varchar (max)**, **nvarchar (max)**, **varbinary (max)** en lugar de **texto**, **ntext**, y **imagen** tipos de datos, respectivamente.  
  
-   Actualizaciones de claves únicas (incluidas las claves principales) que generan duplicados (por ejemplo, una actualización del formulario `UPDATE <column> SET <column> =<column>+1` no se admiten y se rechazarán debido a una infracción de unicidad. Esto se debe a que la replicación propaga las actualizaciones de conjuntos realizadas en el suscriptor como instrucciones **UPDATE** individuales para cada fila afectada.  
  
-   Si se realiza una partición horizontal de la base de datos de suscriptor y hay filas en la partición que existen en el suscriptor pero no en el publicador, el suscriptor no podrá actualizar las filas preexistentes. Si intenta actualizar estas filas, se obtendrá un error. Las filas deben eliminarse de la tabla e insertarse de nuevo.  
  
### Desencadenadores definidos por el usuario  
  
-   Si la aplicación requiere desencadenadores en el suscriptor, éstos se deben definir con la opción `NOT FOR REPLICATION` en el publicador y en el suscriptor. Así se garantiza que los desencadenadores se activen solamente para los cambios de datos originales, pero no cuando el cambio se replique.  
  
     Asegúrese de que el desencadenador definido por el usuario no se active cuando el desencadenador de replicación actualice la tabla. Esto se logra llamando al procedimiento **sp_check_for_sync_trigger** en el cuerpo del desencadenador definido por el usuario. Para obtener más información, consulte [sp_check_for_sync_trigger &#40; Transact-SQL &#41;](../../../relational-databases/system-stored-procedures/sp-check-for-sync-trigger-transact-sql.md).  
  
### Actualización inmediata  
  
-   Para las suscripciones de actualización inmediata, los cambios en el suscriptor se propagan al publicador y se aplican mediante Microsoft DTC (Coordinador de transacciones distribuidas). Asegúrese de que MS DTC se ha instalado y configurado en el publicador y en el suscriptor. Para obtener más información, consulte la documentación de Windows.  
  
-   Los desencadenadores que se utilizan en las suscripciones de actualización inmediata requieren una conexión al publicador para replicar los cambios.  
  
-   Si la publicación admite suscripciones de actualización inmediata y un artículo de la publicación tiene un filtro de columna, no puede excluir columnas que no admitan valores NULL y que no tengan valores predeterminados.  
  
### Actualización en cola  
  
-   Las tablas incluidas en una publicación de combinación no se pueden publicar como parte de una publicación transaccional que admite suscripciones de actualización en cola.  
  
-   No se recomienda realizar actualizaciones en columnas de clave principal al utilizar la actualización en cola, ya que se utiliza la clave principal como localizador de registros para todas las consultas. Cuando la directiva de resolución de conflictos está establecida en El suscriptor gana, las actualizaciones de las claves principales deben realizarse con precaución. Si se realizan actualizaciones de la clave principal en el publicador y en el suscriptor, el resultado serán dos filas con claves principales diferentes.  
  
-   Para las columnas de tipo de datos **SQL_VARIANT**: cuando se insertan o actualizan en el suscriptor, se asigna de la manera siguiente por el agente de lector de cola cuando se copian desde el suscriptor a la cola:  
  
    -   **BIGINT**, **DECIMAL**, **NUMERIC**, **MONEY**y **SMALLMONEY** se asignan a **NUMERIC**.  
  
    -   **BINARY** y **VARBINARY** se asignan a datos **VARBINARY** .  
  
### Detección y resolución de conflictos  
  
-   Para la directiva de conflictos El suscriptor gana: no se admite la resolución de conflictos para actualizaciones de columnas de clave principal.  
  
-   Los conflictos causados por errores de restricción de clave externa no se resuelven con la replicación:  
  
    -   Si no se esperan conflictos y los datos están correctamente divididos en particiones (los suscriptores no actualizan las mismas filas), puede utilizar restricciones de clave externa en el publicador y los suscriptores.  
  
    -   Si se esperan conflictos, no debe utilizar restricciones de clave externa en el publicador o suscriptor si utiliza la resolución de conflictos "El suscriptor gana"; no debe utilizar restricciones de clave externa en el suscriptor si utiliza la resolución de conflictos "El publicador gana".  
  
## Vea también  
 [Replicación transaccional punto a punto](../../../relational-databases/replication/transactional/peer-to-peer-transactional-replication.md)   
 [Tipos de publicaciones para la replicación transaccional](../../../relational-databases/replication/transactional/publication-types-for-transactional-replication.md)   
 [Publicar datos y objetos de base de datos](../../../relational-databases/replication/publish/publish-data-and-database-objects.md)   
 [Suscribirse a publicaciones](../../../relational-databases/replication/subscribe-to-publications.md)  
  
  