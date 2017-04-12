---
title: "Soft-NUMA (SQL Server) | Microsoft Docs"
ms.custom: 
  - "SQL2016_New_Updated"
ms.date: "11/16/2016"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "database-engine"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "NUMA"
  - "soft-NUMA"
helpviewer_keywords: 
  - "NUMA"
  - "acceso a memoria no uniforme"
  - "soft-NUMA"
ms.assetid: 1af22188-e08b-4c80-a27e-4ae6ed9ff969
caps.latest.revision: 53
author: "CarlRabeler"
ms.author: "carlrab"
manager: "jhubbard"
caps.handback.revision: 52
---
# Soft-NUMA (SQL Server)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx_md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Los procesadores de hoy en día tienen varios núcleos por socket. Normalmente, cada socket se representa como un solo nodo NUMA. El motor de base de datos de SQL Server crea particiones de las diversas estructuras internas y de los subprocesos de servicio por nodo NUMA.  En procesadores con 10 o más núcleos por socket, el uso de NUMA de software para dividir los nodos NUMA de hardware suele aumentar la escalabilidad y el rendimiento. Antes de SQL Server 2014 SP2, NUMA basado en software (soft-NUMA) requería modificar el Registro para agregar una máscara de afinidad de configuración de nodo y, además, se configuraba por equipo, en vez de por instancia.  Con SQL Server 2014 SP2 y SQL Server 2016, soft-NUMA se configura automáticamente en el nivel de instancia de base de datos cuando se inicia el servicio SQL Server.  
  
> [!NOTE]  
>  soft-NUMA no admite procesadores de agregado en caliente.  
  
## <a name="automatic-soft-numa"></a>soft-NUMA automático  
 Con SQL Server 2016, cada vez que el servidor de motor de base de datos detecta más de ocho núcleos físicos por nodo NUMA o socket en el inicio, se crean nodos soft-NUMA de forma automática y predeterminada. Al hacer el recuento de núcleos físicos de un nodo, no se distinguen los núcleos de procesador con Hyper-Threading.  Cuando el número de núcleos físicos detectado es superior a ocho por socket, el servicio de motor de base de datos crea nodos soft-NUMA que, idealmente, contienen ocho núcleos, pero esta cifra puede bajar a cinco o subir a nueve núcleos lógicos por nodo. El tamaño del nodo de hardware puede estar limitado por una máscara de afinidad de CPU. Vea   
            [ALTER SERVER CONFIGURATION &amp;#40;Transact-SQL&amp;#41;](../../t-sql/statements/alter-server-configuration-transact-sql.md). El número de nodos NUMA nunca superará el número máximo de nodos NUMA admitido.  
  
 soft-NUMA se puede deshabilitar o volver a habilitar con la instrucción [ALTER SERVER CONFIGURATION &#40;Transact-SQL&#41;](../../t-sql/statements/alter-server-configuration-transact-sql.md) y el argumento SET SOFTNUMA. Para que el cambio del valor de esta configuración surta efecto, hay que reiniciar el motor de base de datos.  
  
 En la siguiente imagen se muestra el tipo de información sobre soft-NUMA que aparece en el registro de errores de SQL Server cuando SQL Server detecta nodos NUMA de hardware con más de ocho núcleos físicos en cada nodo o socket.  


``2016-11-14 13:39:43.17 Server      SQL Server detected 2 sockets with 12 cores per socket and 24 logical processors per socket, 48 total logical processors; using 48 logical processors based on SQL Server licensing. This is an informational message; no user action is required.``  
  **``2016-11-14 13:39:43.35 Server      Automatic soft-NUMA was enabled because SQL Server has detected hardware NUMA nodes with greater than 8 physical cores.``**  
  ``2016-11-14 13:39:43.63 Server      Node configuration: node 0: CPU mask: 0x0000000000555555:0 Active CPU mask: 0x0000000000555555:0. This message provides a description of the NUMA configuration for this computer. This is an informational message only. No user action is required.``  
  ``2016-11-14 13:39:43.63 Server      Node configuration: node 1: CPU mask: 0x0000000000aaaaaa:0 Active CPU mask: 0x0000000000aaaaaa:0. This message provides a description of the NUMA configuration for this computer. This is an informational message only. No user action is required.``  
  ``2016-11-14 13:39:43.63 Server      Node configuration: node 2: CPU mask: 0x0000555555000000:0 Active CPU mask: 0x0000555555000000:0. This message provides a description of the NUMA configuration for this computer. This is an informational message only. No user action is required.``  
  ``2016-11-14 13:39:43.63 Server      Node configuration: node 3: CPU mask: 0x0000aaaaaa000000:0 Active CPU mask: 0x0000aaaaaa000000:0. This message provides a description of the NUMA configuration for this computer. This is an informational message only. No user action is required.``

  
## <a name="manual-soft-numa"></a>soft-NUMA manual  
 Para configurar [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] manualmente de modo que use soft-NUMA, deshabilite soft_NUMA automático y modifique el Registro para agregar una máscara de afinidad de configuración de nodo. Al usar este método, la máscara soft-NUMA se puede establecer como una entrada del Registro binaria, DWORD (hexadecimal o decimal) o QWORD (hexadecimal o decimal). Para configurar más de las primeras 32 CPU use valores del Registro QWORD o BINARY. (Los valores QWORD no se pueden usar antes de [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)]). Tras modificar el Registro, debe reiniciar el [!INCLUDE[ssDE](../../includes/ssde-md.md)] para que se aplique la configuración de soft-NUMA.  
  
> [!TIP] Las CPU se numeran a partir de 0.  

> [!WARNING] [!INCLUDE[ssNoteRegistry](../../includes/ssnoteregistry-md.md)]  
  
 Considere el ejemplo siguiente. Un equipo con ocho CPU no dispone de NUMA de hardware. Se configuran tres nodos de NUMA de software.   
La instancia A de             [!INCLUDE[ssDE](../../includes/ssde-md.md)] se configura para que use las CPU 0 a 3. Una segunda instancia de [!INCLUDE[ssDE](../../includes/ssde-md.md)] se instala y configura para que use las CPU 4 a 7. El ejemplo se puede representar visualmente como:  
  
 `CPUs          0  1  2  3  4  5  6  7`  
  
 `Soft-NUMA   <-N0--><-N1-><----N2---->`  
  
 `SQL Server  <instance A ><instance B>`  
  
 La instancia A, que experimenta actividades de E/S importantes, tiene ahora dos subprocesos de E/S y un subprocesos de escritura diferida, mientras que la instancia B, que realiza operaciones que requieren un uso intensivo del procesador, solo tiene un subproceso de E/S y un subproceso de escritura diferida. Se pueden asignar diferentes cantidades de memoria a las instancias, pero, a diferencia de lo que ocurre con el NUMA de hardware, ambas reciben memoria del mismo bloque de memoria del sistema operativo y no hay afinidad entre la memoria y el procesador.  
  
 El subproceso de escritura diferida está enlazado a la vista del sistema operativo SQL de los nodos físicos de memoria de NUMA. Por consiguiente, siempre que el hardware se presente como nodos físicos de NUMA, será igual al número de subprocesos de escritura diferida que se creen. Para obtener más información, vea   
            [How It Works: Soft NUMA, I/O Completion Thread, Lazy Writer Workers and Memory Nodes](http://blogs.msdn.com/b/psssql/archive/2010/04/02/how-it-works-soft-numa-i-o-completion-thread-lazy-writer-workers-and-memory-nodes.aspx)(Cómo funciona: soft-NUMA, subproceso de finalización de E/S, trabajos de escritura diferida y nodos de memoria).  
  
> [!NOTE] Las claves del Registro de **Soft-NUMA** no se copian al actualizar una instancia de [!INCLUDE[ssNoVersion] (../Token/ssNoVersion_md.md)].  
  
### <a name="set-the-cpu-affinity-mask"></a>Establecer la máscara de afinidad de la CPU  
 Ejecute la siguiente instrucción en la instancia A para configurarla de modo que use las CPU 0, 1, 2 y 3, y establezca la máscara de afinidad de la CPU:  
  
```  
ALTER SERVER CONFIGURATION   
SET PROCESS AFFINITY CPU=0 TO 3;  
```  
  
 Ejecute la siguiente instrucción en la instancia B para configurarla de modo que use las CPU 4, 5, 6 y 7, y establezca la máscara de afinidad de la CPU:  
  
```  
ALTER SERVER CONFIGURATION   
SET PROCESS AFFINITY CPU=4 TO 7;  
```  
  
### <a name="map-soft-numa-nodes-to-cpus"></a>Asignar nodos NUMA de software a las CPU  
 Mediante el programa Editor del Registro (regedit.exe), agregue las dos claves del Registro siguientes para asignar el nodo 0 de soft-NUMA a las CPU 0 y 1, el nodo 1 de soft-NUMA a las CPU 2 y 3, y el nodo 2 de soft-NUMA a las CPU 4, 5, 6 y 7.  
  
> [!TIP] Para especificar las CPU 60 a 63, use un valor QWORD de F000000000000000 o un valor binario de 1111000000000000000000000000000000000000000000000000000000000000.  
  
 En el ejemplo siguiente, suponga que tiene un servidor DL580 G9 con 18 núcleos por socket (en 4 sockets) y que cada socket está en su propio grupo K. La configuración NUMA de software que cree será parecida a la siguiente. (6 núcleos por nodo, 3 nodos por grupo, 4 grupos).  
  
|Ejemplo de un servidor [!INCLUDE[ssSQL15](../../includes/sssql15-md.md)] con varios grupos K|Tipo|Nombre del valor|Datos del valor|  
|-----------------------------------------------------------------------------------------------------------------|----------|----------------|----------------|  
|HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Microsoft SQL Server\130\NodeConfiguration\Node0|DWORD|CPUMask|0x3F|  
|HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Microsoft SQL Server\130\NodeConfiguration\Node0|DWORD|Grupo|0|  
|HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Microsoft SQL Server\130\NodeConfiguration\Node1|DWORD|CPUMask|0x0fc0|  
|HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Microsoft SQL Server\130\NodeConfiguration\Node1|DWORD|Grupo|0|  
|HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Microsoft SQL Server\130\NodeConfiguration\Node2|DWORD|CPUMask|0x3f000|  
|HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Microsoft SQL Server\130\NodeConfiguration\Node2|DWORD|Grupo|0|  
|HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Microsoft SQL Server\130\NodeConfiguration\Node3|DWORD|CPUMask|0x3F|  
|HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Microsoft SQL Server\130\NodeConfiguration\Node3|DWORD|Grupo|1|  
|HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Microsoft SQL Server\130\NodeConfiguration\Node4|DWORD|CPUMask|0x0fc0|  
|HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Microsoft SQL Server\130\NodeConfiguration\Node4|DWORD|Grupo|1|  
|HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Microsoft SQL Server\130\NodeConfiguration\Node5|DWORD|CPUMask|0x3f000|  
|HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Microsoft SQL Server\130\NodeConfiguration\Node5|DWORD|Grupo|1|  
|HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Microsoft SQL Server\130\NodeConfiguration\Node6|DWORD|CPUMask|0x3F|  
|HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Microsoft SQL Server\130\NodeConfiguration\Node6|DWORD|Grupo|2|  
|HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Microsoft SQL Server\130\NodeConfiguration\Node7|DWORD|CPUMask|0x0fc0|  
|HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Microsoft SQL Server\130\NodeConfiguration\Node7|DWORD|Grupo|2|  
|HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Microsoft SQL Server\130\NodeConfiguration\Node8|DWORD|CPUMask|0x3f000|  
|HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Microsoft SQL Server\130\NodeConfiguration\Node8|DWORD|Grupo|2|  
|HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Microsoft SQL Server\130\NodeConfiguration\Node9|DWORD|CPUMask|0x3F|  
|HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Microsoft SQL Server\130\NodeConfiguration\Node9|DWORD|Grupo|3|  
|HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Microsoft SQL Server\130\NodeConfiguration\Node10|DWORD|CPUMask|0x0fc0|  
|HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Microsoft SQL Server\130\NodeConfiguration\Node10|DWORD|Grupo|3|  
|HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Microsoft SQL Server\130\NodeConfiguration\Node11|DWORD|CPUMask|0x3f000|  
|HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Microsoft SQL Server\130\NodeConfiguration\Node11|DWORD|Grupo|3|  
  
## <a name="metadata"></a>Metadatos  
 Puede usar las siguientes DMV para ver el estado y configuración actuales de soft_NUMA.  
  
-   [sp_configure &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-configure-transact-sql.md): muestra el valor actual (0 o 1) para SOFTNUMA.  
  
-   [sys.dm_os_nodes &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-os-nodes-transact-sql.md): la columna node_state_desc de cada nodo NUMA indicará si el nodo fue creado o no por soft-NUMA.  
  
-   [sys.dm_os_sys_info &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-os-sys-info-transact-sql.md): las columnas softnuma y softnuma_desc mostrarán los valores de configuración.  
  
> [!NOTE] El valor actual de uso automático de soft-NUMA se puede ver con [sp_configure &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-configure-transact-sql.md), pero no se puede modificar mediante **sp_configure**. Debe usar la instrucción [ALTER SERVER CONFIGURATION &#40;Transact-SQL&#41;](../../t-sql/statements/alter-server-configuration-transact-sql.md) con el argumento SET SOFTNUMA.  
  
## <a name="see-also"></a>Vea también  
 [Asignación de puertos TCP/IP a nodos NUMA &#40;SQL Server&#41;](../../database-engine/configure-windows/map-tcp-ip-ports-to-numa-nodes-sql-server.md)   
 [affinity mask (opción de configuración del servidor)](../../database-engine/configure-windows/affinity-mask-server-configuration-option.md)   
 [ALTER SERVER CONFIGURATION &#40;Transact-SQL&#41;](../../t-sql/statements/alter-server-configuration-transact-sql.md)  
  
  