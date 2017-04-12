---
title: "Eliminar una publicaci&#243;n | Microsoft Docs"
ms.custom: ""
ms.date: "03/14/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "replication"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "quitar publicaciones"
  - "publicaciones [replicación de SQL Server], eliminar"
  - "artículos [replicación de SQL Server], eliminar"
  - "eliminar publicaciones"
ms.assetid: 408a1360-12ee-4896-ac94-482ae839593b
caps.latest.revision: 35
author: "BYHAM"
ms.author: "rickbyh"
manager: "jhubbard"
caps.handback.revision: 35
---
# Eliminar una publicaci&#243;n
  En este tema se describe cómo eliminar una publicación en [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)] mediante [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)], [!INCLUDE[tsql](../../../includes/tsql-md.md)] o Replication Management Objects (RMO).  
  
 **En este tema**  
  
-   **Para eliminar una publicación con:**  
  
     [SQL Server Management Studio](#SSMSProcedure)  
  
     [Transact-SQL](#TsqlProcedure)  
  
     [Replication Management Objects (RMO)](#RMOProcedure)  
  
##  <a name="SSMSProcedure"></a> Usar SQL Server Management Studio  
 Elimine publicaciones de la carpeta **Publicaciones locales** en [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)].  
  
#### Para eliminar una publicación  
  
1.  Conéctese al publicador en [!INCLUDE[ssManStudio](../../../includes/ssmanstudio-md.md)]y, a continuación, expanda el nodo del servidor.  
  
2.  Expanda la carpeta **Replicación** y, a continuación, expanda la carpeta **Publicaciones locales** .  
  
3.  Haga clic en la publicación que desea eliminar y, a continuación, haga clic en **Eliminar**.  
  
##  <a name="TsqlProcedure"></a> Usar Transact-SQL  
 Las publicaciones pueden eliminarse mediante programación con procedimientos almacenados de replicación. Los procedimientos almacenados que use dependen del tipo de publicación que se elimina.  
  
> [!NOTE]  
>  Al eliminar una publicación, no se quitan los objetos publicados de la base de datos de publicación ni los objetos correspondientes de la base de datos de suscripciones. Si es necesario, use el comando `DROP <object>` para quitar estos objetos manualmente.  
  
#### Para eliminar una publicación transaccional o de instantáneas  
  
1.  Realice una de las siguientes operaciones:  
  
    -   Para eliminar una publicación, ejecute [sp_droppublication](../../../relational-databases/system-stored-procedures/sp-droppublication-transact-sql.md) en el publicador de la base de datos de publicación.  
  
    -   Para eliminar todas las publicaciones de y quitar todos los objetos de replicación de base de datos publicada, ejecute [sp_removedbreplication](../../../relational-databases/system-stored-procedures/sp-removedbreplication-transact-sql.md) en el publicador. Especifique el valor de **tran** para **@type**. (Opcional) Si el distribuidor no puede tener acceso o si el estado de la base de datos es sospechosa o sin conexión, especifique un valor de **1** para **@force**. (Opcional) Especifique el nombre de la base de datos **@dbname** Si [sp_removedbreplication](../../../relational-databases/system-stored-procedures/sp-removedbreplication-transact-sql.md) no se ejecuta en la base de datos de publicación.  
  
        > [!NOTE]  
        >  Especifica el valor de **1** para **@force** puede dejar los objetos de publicación relacionadas con la replicación en la base de datos.  
  
2.  (Opcional) Si esta base de datos no tiene otras publicaciones, ejecute [sp_replicationdboption & #40; Transact-SQL & #41;](../../../relational-databases/system-stored-procedures/sp-replicationdboption-transact-sql.md) Para deshabilitar la publicación de la base de datos actual utilizando la replicación transaccional o instantáneas.  
  
3.  (Opcional) En el suscriptor en la base de datos de suscripción, ejecute [sp_subscription_cleanup](../../../relational-databases/system-stored-procedures/sp-subscription-cleanup-transact-sql.md) para quitar los metadatos de replicación restantes en la base de datos de suscripción.  
  
#### Para eliminar una publicación de combinación  
  
1.  Realice una de las siguientes operaciones:  
  
    -   Para eliminar una publicación, ejecute [sp_dropmergepublication & #40; Transact-SQL & #41;](../../../relational-databases/system-stored-procedures/sp-dropmergepublication-transact-sql.md) en el publicador de la base de datos de publicación.  
  
    -   Para eliminar todas las publicaciones de y quitar todos los objetos de replicación de base de datos publicada, ejecute [sp_removedbreplication](../../../relational-databases/system-stored-procedures/sp-removedbreplication-transact-sql.md) en el publicador. Especifique el valor de **merge** para **@type**. (Opcional) Si el distribuidor no puede tener acceso o si el estado de la base de datos es sospechosa o sin conexión, especifique un valor de **1** para **@force**. (Opcional) Especifique el nombre de la base de datos **@dbname** Si [sp_removedbreplication](../../../relational-databases/system-stored-procedures/sp-removedbreplication-transact-sql.md) no se ejecuta en la base de datos de publicación.  
  
        > [!NOTE]  
        >  Especifica el valor de **1** para **@force** puede dejar los objetos de publicación relacionadas con la replicación en la base de datos.  
  
2.  (Opcional) Si esta base de datos no tiene otras publicaciones, ejecute [sp_replicationdboption & #40; Transact-SQL & #41;](../../../relational-databases/system-stored-procedures/sp-replicationdboption-transact-sql.md) Para deshabilitar la publicación de la base de datos actual mediante la replicación de mezcla.  
  
3.  (Opcional) En el suscriptor en la base de datos de suscripción, ejecute [sp_mergesubscription_cleanup & #40; Transact-SQL & #41;](../../../relational-databases/system-stored-procedures/sp-mergesubscription-cleanup-transact-sql.md) Para quitar los metadatos de replicación restantes en la base de datos de suscripción.  
  
###  <a name="TsqlExample"></a> Ejemplos (Transact-SQL)  
 Este ejemplo muestra cómo quitar una publicación transaccional y deshabilitar la publicación transaccional para una base de datos. Este ejemplo supone que se quitaron todas las suscripciones previamente. Para obtener más información, consulte [Delete a Pull Subscription](../../../relational-databases/replication/delete-a-pull-subscription.md) o [Delete a Push Subscription](../../../relational-databases/replication/delete-a-push-subscription.md).  
  
 [!code-sql[HowTo#sp_droppublication](../../../relational-databases/replication/codesnippet/tsql/delete-a-publication_1.sql)]  
  
 Este ejemplo muestra cómo quitar una publicación de combinación y deshabilitar la publicación de combinación para una base de datos. Este ejemplo supone que se quitaron todas las suscripciones previamente. Para obtener más información, consulte [Delete a Pull Subscription](../../../relational-databases/replication/delete-a-pull-subscription.md) o [Delete a Push Subscription](../../../relational-databases/replication/delete-a-push-subscription.md).  
  
 [!code-sql[HowTo#sp_dropmergepublication](../../../relational-databases/replication/codesnippet/tsql/delete-a-publication_2.sql)]  
  
##  <a name="RMOProcedure"></a> Usar Replication Management Objects (RMO)  
 Puede eliminar publicación mediante programación utilizando Replication Management Objects (RMO). Las clases RMO que utiliza para quitar una publicación dependen del tipo de publicación que quita.  
  
#### Para quitar una publicación transaccional o de instantáneas  
  
1.  Crear una conexión al publicador mediante la <xref:Microsoft.SqlServer.Management.Common.ServerConnection> clase.  
  
2.  Cree una instancia de la <xref:Microsoft.SqlServer.Replication.TransPublication> clase.  
  
3.  Establecer el <xref:Microsoft.SqlServer.Replication.Publication.Name%2A> y <xref:Microsoft.SqlServer.Replication.Publication.DatabaseName%2A> Propiedades de la publicación y establezca el <xref:Microsoft.SqlServer.Replication.ReplicationObject.ConnectionContext%2A> propiedad en la conexión creada en el paso 1.  
  
4.  Compruebe el <xref:Microsoft.SqlServer.Replication.ReplicationObject.IsExistingObject%2A> propiedad para comprobar que la publicación existe. Si el valor de esta propiedad es **false**, significa que las propiedades de la publicación del paso 3 se definieron incorrectamente, o bien que la publicación no existe.  
  
5.  Llame a la <xref:Microsoft.SqlServer.Replication.Publication.Remove%2A> método.  
  
6.  (Opcional) Si no existe ninguna otra publicación transaccional para esta base de datos, ésta se puede deshabilitar para la publicación transaccional del siguiente modo:  
  
    1.  Cree una instancia de la <xref:Microsoft.SqlServer.Replication.ReplicationDatabase> clase. Establecer el <xref:Microsoft.SqlServer.Replication.ReplicationObject.ConnectionContext%2A> propiedad a la instancia de <xref:Microsoft.SqlServer.Management.Common.ServerConnection> del paso 1.  
  
    2.  Llame a la <xref:Microsoft.SqlServer.Replication.ReplicationObject.LoadProperties%2A> método. Si este método devuelve **false**, confirme que la base de datos existe.  
  
    3.  Establecer el <xref:Microsoft.SqlServer.Replication.ReplicationDatabase.EnabledTransPublishing%2A> propiedad **false**.  
  
    4.  Llame a la <xref:Microsoft.SqlServer.Replication.ReplicationObject.CommitPropertyChanges%2A> método.  
  
7.  Cierre las conexiones.  
  
#### Para quitar una publicación de combinación  
  
1.  Crear una conexión al publicador mediante la <xref:Microsoft.SqlServer.Management.Common.ServerConnection> clase.  
  
2.  Cree una instancia de la <xref:Microsoft.SqlServer.Replication.MergePublication> clase.  
  
3.  Establecer el <xref:Microsoft.SqlServer.Replication.Publication.Name%2A> y <xref:Microsoft.SqlServer.Replication.Publication.DatabaseName%2A> Propiedades de la publicación y establezca el <xref:Microsoft.SqlServer.Replication.ReplicationObject.ConnectionContext%2A> propiedad en la conexión creada en el paso 1.  
  
4.  Compruebe el <xref:Microsoft.SqlServer.Replication.ReplicationObject.IsExistingObject%2A> propiedad para comprobar que la publicación existe. Si el valor de esta propiedad es **false**, significa que las propiedades de la publicación del paso 3 se definieron incorrectamente, o bien que la publicación no existe.  
  
5.  Llame a la <xref:Microsoft.SqlServer.Replication.Publication.Remove%2A> método.  
  
6.  (Opcional) Si no existe ninguna otra publicación de combinación para esta base de datos, ésta se puede deshabilitar para la publicación de combinación del siguiente modo:  
  
    1.  Cree una instancia de la <xref:Microsoft.SqlServer.Replication.ReplicationDatabase> clase. Establecer el <xref:Microsoft.SqlServer.Replication.ReplicationObject.ConnectionContext%2A> propiedad a la instancia de <xref:Microsoft.SqlServer.Management.Common.ServerConnection> del paso 1.  
  
    2.  Llame a la <xref:Microsoft.SqlServer.Replication.ReplicationObject.LoadProperties%2A> método. Si este método devuelve **false**, compruebe que la base de datos existe.  
  
    3.  Establecer el <xref:Microsoft.SqlServer.Replication.ReplicationDatabase.EnabledMergePublishing%2A> propiedad **false**.  
  
    4.  Llame a la <xref:Microsoft.SqlServer.Replication.ReplicationObject.CommitPropertyChanges%2A> método.  
  
7.  Cierre las conexiones.  
  
###  <a name="PShellExample"></a> Ejemplos (RMO)  
 En el siguiente ejemplo se elimina una publicación transaccional Si no existe ninguna otra publicación transaccional para esta base de datos, también se deshabilita la publicación transaccional.  
  
 [!code-csharp[HowTo#rmo_DropTranPub](../../../relational-databases/replication/codesnippet/csharp/rmohowto/rmotestevelope.cs#rmo_droptranpub)]  
  
 [!code-vb[HowTo#rmo_vb_DropTranPub](../../../relational-databases/replication/codesnippet/visualbasic/rmohowtovb/rmotestenv.vb#rmo_vb_droptranpub)]  
  
 En el siguiente ejemplo se elimina una publicación de combinación. Si no existe ninguna otra publicación de combinación para esta base de datos, también se deshabilita la publicación de combinación.  
  
 [!code-csharp[HowTo#rmo_DropMergePub](../../../relational-databases/replication/codesnippet/csharp/rmohowto/rmotestevelope.cs#rmo_dropmergepub)]  
  
 [!code-vb[HowTo#rmo_vb_DropMergePub](../../../relational-databases/replication/codesnippet/visualbasic/rmohowtovb/rmotestenv.vb#rmo_vb_dropmergepub)]  
  
## Vea también  
 [Conceptos sobre los procedimientos almacenados del sistema de replicación](../../../relational-databases/replication/concepts/replication-system-stored-procedures-concepts.md)   
 [Publicar datos y objetos de base de datos](../../../relational-databases/replication/publish/publish-data-and-database-objects.md)  
  
  