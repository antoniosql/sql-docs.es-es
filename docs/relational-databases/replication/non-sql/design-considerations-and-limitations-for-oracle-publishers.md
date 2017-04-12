---
title: "Consideraciones y limitaciones de dise&#241;o de los publicadores de Oracle | Microsoft Docs"
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
  - "publicación de Oracle [replicación de SQL Server], consideraciones y limitaciones de diseño"
ms.assetid: 8d9dcc59-3de8-4d36-a61f-bc3ca96516b6
caps.latest.revision: 48
author: "BYHAM"
ms.author: "rickbyh"
manager: "jhubbard"
caps.handback.revision: 48
---
# Consideraciones y limitaciones de dise&#241;o de los publicadores de Oracle
  La publicación de una base de datos de Oracle se diseña para que funcione casi idénticamente a la publicación de una base de datos de [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] . No obstante, debe tener en cuenta las siguientes limitaciones y problemas:  
  
-   La opción de puerta de enlace de Oracle proporciona mejor rendimiento que la opción Completo. No obstante, esta opción no se puede utilizar para publicar la misma tabla en varias publicaciones transaccionales. Una tabla puede aparecer como máximo en una publicación transaccional y en cualquier número de publicaciones de instantánea. Si necesita publicar la misma tabla en varias publicaciones transaccionales, elija la opción Completo de Oracle.  
  
-   La replicación admite la publicación de tablas, índices y vistas materializadas. No se replican otros objetos.  
  
-   Existen pequeñas diferencias entre el almacenamiento y el procesamiento de datos en Oracle y las bases de datos de [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] que afectan a la replicación.  
  
-   Existen ciertas diferencias en el modo en que se admiten las características de replicación transaccional al utilizar un publicador de Oracle.  
  
## Compatibilidad con objetos de publicación de Oracle  
 La replicación admite los siguientes objetos de las bases de datos de Oracle:  
  
-   Tablas  
  
-   Tablas organizadas por índices  
  
-   Índices  
  
-   Vistas materializadas (se replican como tablas)  
  
 Los siguientes elementos pueden aparecer en tablas publicadas pero no se replican:  
  
-   Índices basados en dominios  
  
-   Índices basados en funciones  
  
-   Valores predeterminados  
  
-   Restricciones CHECK  
  
-   Claves externas  
  
-   Opciones de almacenamiento (espacios de tabla, clústeres, etc.)  
  
 No es posible replicar los siguientes objetos:  
  
-   Tablas anidadas  
  
-   Vistas  
  
-   Paquetes, cuerpos de paquetes, procedimientos y desencadenadores  
  
-   Colas  
  
-   Secuencias  
  
-   Sinónimos  
  
 Para obtener información acerca de los tipos de datos compatibles, consulte [asignación de tipos de datos para los publicadores de Oracle](../../../relational-databases/replication/non-sql/data-type-mapping-for-oracle-publishers.md).  
  
## Diferencias entre Oracle y SQL Server  
  
-   Oracle tiene límites de tamaño máximo diferentes para algunos objetos. Cualquier objeto creado en la base de datos de publicación de Oracle debe respetar los límites de tamaño máximo de los correspondientes objetos en [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]. Para obtener información acerca de los límites de [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)], consulte [especificaciones de capacidad máxima para SQL Server](../../../sql-server/maximum-capacity-specifications-for-sql-server.md).  
  
-   Los nombres de objeto de Oracle se crean de manera predeterminada en mayúsculas. Asegúrese de proporcionar los nombres de los objetos de Oracle en mayúsculas al publicarlos a través de un distribuidor de [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] si están en mayúsculas en la base de datos de Oracle. Si no se especifican los objetos en mayúsculas o minúsculas correctamente, se puede producir un mensaje de error que indica que no se puede encontrar el objeto.  
  
-   Oracle tiene un dialecto SQL ligeramente diferente de [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]; los filtros de fila se deben escribir en sintaxis compatible con Oracle.  
  
### Consideraciones para objetos grandes  
 Los datos de objetos grandes (LOB) no se almacenan en la tabla de registro de artículos; las actualizaciones de datos LOB se recuperan directamente en la tabla publicada. Las actualizaciones se replican en publicaciones transaccionales solamente si la operación que afecta al LOB activa el desencadenador de replicación en la tabla replicada. Los desencadenadores de Oracle se activan cuando se insertan o eliminan filas que contienen LOB; sin embargo, las actualizaciones de columnas LOB no activan los desencadenadores. Una actualización de una columna LOB se replicará inmediatamente solo si una columna no LOB de la misma fila se actualiza también en la misma transacción de Oracle. Si no, la columna LOB se actualizará en el suscriptor cuando se produzca la siguiente actualización de una columna no LOB de la misma fila. Asegúrese de que este comportamiento es aceptable para su aplicación.  
  
 Para replicar actualizaciones de columnas LOB en publicaciones transaccionales, considere una de las siguientes estrategias cuando escriba la aplicación:  
  
-   Elimine y vuelva a insertar las filas en una transacción en lugar de actualizar la fila: especifique el nuevo LOB al volver a insertar la fila. Como la eliminación y la inserción activan desencadenadores, la fila se replicará.  
  
-   Incluya una columna no LOB en la actualización de filas además de la columna LOB, o actualice una columna no LOB de la fila como parte de la misma transacción de Oracle. En ambos casos, la actualización de la columna no LOB garantiza que se active el desencadenador.  
  
 Para obtener más información sobre los LOB, vea [Data Type Mapping for Oracle Publishers](../../../relational-databases/replication/non-sql/data-type-mapping-for-oracle-publishers.md).  
  
### Índices y restricciones únicos  
 En la replicación de instantáneas y transaccional, las columnas contenidas en índices y restricciones únicos (incluidas las restricciones de clave principal) deben respetar ciertas limitaciones Si no se respetan dichas limitaciones, la restricción o el índice no se replican.  
  
-   El número máximo de columnas permitido en un índice en [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] es de 16.  
  
-   Todas las columnas incluidas en restricciones únicas deben tener tipos de datos admitidos. Para obtener más información acerca de los tipos de datos, vea [Data Type Mapping for Oracle Publishers](../../../relational-databases/replication/non-sql/data-type-mapping-for-oracle-publishers.md).  
  
-   Todas las columnas incluidas en restricciones únicas se deben publicar (no se pueden filtrar).  
  
-   Las columnas incluidas en restricciones o índices únicos no deben ser de tipo NULL.  
  
 Considere también los siguientes problemas:  
  
-   Oracle y [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] tratan NULL de manera diferente: Oracle admite varias filas con valores NULL para las columnas que permiten NULL y se incluyen en restricciones o índices únicos. [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] aplica la singularidad solo permitiendo una única fila con un valor NULL para la misma columna. No puede publicar un índice o restricción únicos que permita el valor NULL porque se produciría una infracción de restricción en el suscriptor si la tabla publicada contiene varias filas con valores NULL para cualquiera de las columnas incluidas en el índice o restricción.  
  
-   Al probar la unicidad, [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] omite los espacios en blanco de un campo pero Oracle no.  
  
 Como en la replicación transaccional de [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] , las tablas de las publicaciones transaccionales de Oracle requieren una clave principal, que debe ser única según las reglas especificadas anteriormente. Si la clave principal no sigue las reglas indicadas anteriormente, no se puede publicar la tabla para la replicación transaccional.  
  
## Diferencias entre la publicación de Oracle y la replicación transaccional estándar  
  
-   Un publicador de Oracle no puede tener el mismo nombre que su distribuidor de [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] ni el mismo nombre que ninguno de los publicadores de [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] que utilizan el mismo distribuidor, ni que ninguno de los suscriptores que reciben la publicación. Las publicaciones a las que da servicio el mismo distribuidor deben tener nombres únicos.  
  
-   Una tabla publicada en una publicación de Oracle no puede recibir datos replicados. Por eso, la publicación de Oracle no es compatible con publicaciones con suscripciones de actualización inmediata o de actualización en cola, ni con topologías en las que las tablas de publicación son a la vez tablas de suscripción, como la replicación punto a punto y bidireccional.  
  
-   Las relaciones de clave principal a clave externa de la base de datos de Oracle no se replican en los suscriptores. No obstante, se mantienen las relaciones en los datos cuando se entregan los cambios.  
  
-   Las publicaciones transaccionales estándar admiten tablas de hasta 1000 columnas. Las publicaciones transaccionales de Oracle admiten 995 columnas (la replicación agrega cinco columnas a cada tabla publicada).  
  
-   Se agregan cláusulas de intercalación a las instrucciones CREATE TABLE para habilitar las comparaciones que distinguen entre mayúsculas y minúsculas, que es importante para las claves principales y las restricciones únicas. Este comportamiento se controla con la opción de esquema 0 x 1000, que se especifica con el **@schema_option** parámetro de [sp_addarticle & #40; Transact-SQL & #41;](../../../relational-databases/system-stored-procedures/sp-addarticle-transact-sql.md).  
  
-   Si utiliza procedimientos almacenados para configurar o mantener un publicador de Oracle, no coloque los procedimientos dentro de una transacción explícita. El servidor vinculado que se utiliza para conectar al publicador de Oracle no admite dicha transacción.  
  
-   Si crea una suscripción de extracción en una publicación de Oracle con un asistente, debe utilizar el Asistente para nueva suscripción con [!INCLUDE[ssVersion2005](../../../includes/ssversion2005-md.md)] y versiones posteriores. No obstante, para las versiones anteriores de [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)], puede utilizar el procedimiento almacenado y las interfaces SQL-DMO para configurar suscripciones de extracción a publicaciones de Oracle.  
  
-   Si utiliza procedimientos almacenados para propagar los cambios a los suscriptores (valor predeterminado), tenga en cuenta que se admite la sintaxis MCALL, pero que su comportamiento es diferente cuando la publicación es de un publicador de Oracle. Normalmente MCALL proporciona un mapa de bits que muestra qué columnas se han actualizado en el publicador. Con una publicación de Oracle, el mapa de bits muestra siempre que todas las columnas han sido actualizadas. Para obtener más información sobre el uso de procedimientos almacenados, vea [especificar cómo se propagan los cambios en los artículos transaccionales](../../../relational-databases/replication/transactional/specify-how-changes-are-propagated-for-transactional-articles.md).  
  
### Compatibilidad con características de replicación transaccional  
  
-   Las publicaciones de Oracle no admiten todas las opciones de esquema que admiten las publicaciones de SQL Server. Para obtener más información sobre las opciones de esquema, consulte [sp_addarticle & #40; Transact-SQL & #41;](../../../relational-databases/system-stored-procedures/sp-addarticle-transact-sql.md).  
  
-   Los suscriptores de publicaciones de Oracle no pueden utilizar suscripciones de actualización inmediata o de actualización en cola, ni ser nodos en una topología punto a punto o bidireccional.  
  
-   Los suscriptores de publicaciones de Oracle no se pueden inicializar automáticamente desde una copia de seguridad.  
  
-   [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] admite dos tipos de validación: binaria y de recuento de filas. Los publicadores de Oracle admiten la validación de recuento de filas. Para obtener más información, consulte [Validar datos replicados](../../../relational-databases/replication/validate-replicated-data.md).  
  
-   [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] ofrece dos formatos de instantánea: modo bcp nativo y modo de carácter. Los publicadores de Oracle admiten las instantáneas en modo de carácter.  
  
-   No se admiten los cambios de esquema en las tablas de Oracle publicadas. Para realizar los cambios de esquema, quite primero la publicación, realice los cambios y vuelva a crear la publicación y todas las suscripciones.  
  
    > [!NOTE]  
    >  Si se realizan los cambios de esquema y la posterior eliminación y nueva creación de la publicación y las suscripciones cuando no se está produciendo ninguna actividad en las tablas publicadas, puede especificar la opción "solo compatibilidad con replicación" para las suscripciones. Esto les permite sincronizarse sin tener que copiar una instantánea en cada suscriptor. Para obtener más información, consulte [inicializar una suscripción transaccional sin una instantánea](../../../relational-databases/replication/initialize-a-transactional-subscription-without-a-snapshot.md).  
  
### Modelo de seguridad de replicación  
 El modelo de seguridad de la publicación de Oracle es el mismo que el de la replicación transaccional estándar, con las siguientes excepciones:  
  
-   La cuenta con la que el Agente de instantáneas y el Agente de registro del LOG realizan las conexiones del distribuidor al publicador se especifica mediante uno de los siguientes métodos:  
  
    -   El **@security_mode** parámetro de [sp_adddistpublisher & #40; Transact-SQL & #41;](../../../relational-databases/system-stored-procedures/sp-adddistpublisher-transact-sql.md) (también especifica los valores de **@login** y **@password** Si utiliza la autenticación de Oracle)  
  
    -   En el cuadro del diálogo **Conectar al servidor** en SQL Server Management Studio, que se utiliza al configurar el publicador de Oracle en el distribuidor de [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] .  
  
     En la replicación transaccional estándar, la cuenta se especifica con [sp_addpublication_snapshot & #40; Transact-SQL & #41;](../../../relational-databases/system-stored-procedures/sp-addpublication-snapshot-transact-sql.md) y [sp_addlogreader_agent & #40; Transact-SQL & #41;](../../../relational-databases/system-stored-procedures/sp-addlogreader-agent-transact-sql.md).  
  
-   No se puede cambiar la cuenta bajo la que el agente de instantáneas y el agente de lector del registro realizan conexiones con [sp_changedistpublisher & #40; Transact-SQL & #41;](../../../relational-databases/system-stored-procedures/sp-changedistpublisher-transact-sql.md) o a través de una propiedad se puede cambiar hoja, pero la contraseña.  
  
-   Si especifica un valor de 1 (autenticación integrada de Windows) para el **@security_mode** parámetro de [sp_adddistpublisher & #40; Transact-SQL & #41;](../../../relational-databases/system-stored-procedures/sp-adddistpublisher-transact-sql.md):  
  
    -   La cuenta de proceso y la contraseña usada para el agente de instantáneas y el agente de lector del registro (el **@job_login** y **@job_password** parámetros de [sp_addpublication_snapshot & #40; Transact-SQL & #41;](../../../relational-databases/system-stored-procedures/sp-addpublication-snapshot-transact-sql.md) y [sp_addlogreader_agent & #40; Transact-SQL & #41;](../../../relational-databases/system-stored-procedures/sp-addlogreader-agent-transact-sql.md)) debe ser el mismo que la cuenta y la contraseña usada para conectarse al publicador de Oracle.  
  
    -   No se puede cambiar la **@job_login** parámetro a través de [sp_changepublication_snapshot & #40; Transact-SQL & #41;](../../../relational-databases/system-stored-procedures/sp-changepublication-snapshot-transact-sql.md) o [sp_changelogreader_agent & #40; Transact-SQL & #41;](../../../relational-databases/system-stored-procedures/sp-changelogreader-agent-transact-sql.md), pero se puede cambiar la contraseña.  
  
 Para obtener más información acerca de la seguridad de replicación, consulte [seguridad y protección & #40; Replicación y nº 41;](../../../relational-databases/replication/security/security-and-protection-replication.md).  
  
## Vea también  
 [Consideraciones administrativas para los publicadores de Oracle](../../../relational-databases/replication/non-sql/administrative-considerations-for-oracle-publishers.md)   
 [Configurar un publicador de Oracle](../../../relational-databases/replication/non-sql/configure-an-oracle-publisher.md)   
 [Información general de la publicación de Oracle](../../../relational-databases/replication/non-sql/oracle-publishing-overview.md)  
  
  