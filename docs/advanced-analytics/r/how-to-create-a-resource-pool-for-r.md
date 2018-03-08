---
title: Creare un pool di risorse per machine learning | Documenti Microsoft
ms.custom: 
ms.date: 11/13/2017
ms.reviewer: 
ms.suite: sql
ms.prod: machine-learning-services
ms.prod_service: machine-learning-services
ms.component: r
ms.technology: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: c7f7f6e4-774d-4b45-b94a-f06c51718475
caps.latest.revision: 
author: jeannt
ms.author: jeannt
manager: cgronlund
ms.workload: Inactive
ms.openlocfilehash: dc7a1c26f38cb63cf678f71ec6b889f6051f5387
ms.sourcegitcommit: 99102cdc867a7bdc0ff45e8b9ee72d0daade1fd3
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/11/2018
---
# <a name="create-a-resource-pool-for-machine-learning"></a>Creare un pool di risorse per machine learning
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

In questo argomento viene descritto come creare un pool di risorse in modo specifico per la gestione dei carichi di lavoro di machine learning in SQL Server. Si presuppone di aver installato e abilitato di machine learning, funzionalità e si desidera riconfigurare l'istanza per supportare più granulari per le gestione delle risorse utilizzate da un processo esterno, ad esempio R o Python.

Il processo include più passaggi:

1.  Esaminare lo stato di tutti i pool di risorse esistente. È importante comprendere i servizi utilizzano le risorse esistenti.
2.  Modificare il pool di risorse server.
3.  Creare un nuovo pool di risorse per i processi esterni.
4.  Creare una funzione di classificazione per identificare richieste dello script esterno.
5.  Verificare che il nuovo pool di risorse esterno esegue l'acquisizione processi R o Python dagli account o di client specificati.

**Si applica a:** [!INCLUDE[sssql15-md](../../includes/sssql15-md.md)] [!INCLUDE[rsql-productname-md](../../includes/rsql-productname-md.md)] e [!INCLUDE[sscurrent-md](../../includes/sscurrent-md.md)] [!INCLUDE[rsql-productnamenew-md](../../includes/rsql-productnamenew-md.md)]

##  <a name="bkmk_ReviewStatus"></a> Esaminare lo stato dei pool di risorse esistenti
  
1.  Utilizzare un'istruzione come illustrato di seguito per controllare le risorse allocate per il pool predefinito per il server.
  
    ```sql
    SELECT * FROM sys.resource_governor_resource_pools WHERE name = 'default'
    ```

    **Risultati di esempio**

    |pool_id|name|min_cpu_percent|max_cpu_percent|min_memory_percent|max_memory_percent|cap_cpu_percent|min_iops_per_volume|max_iops_per_volume|
    |-|-|-|-|-|-|-|-|-|
    |2|predefiniti|0|100|0|100|100|0|0|

2.  Controllare le risorse allocate al pool di risorse **esterno** predefinito.
  
    ```sql
    SELECT * FROM sys.resource_governor_external_resource_pools WHERE name = 'default'
    ```

    **Risultati di esempio**

    |external_pool_id|name|max_cpu_percent|max_memory_percent|max_processes|version|
    |-|-|-|-|-|-|
    |2|predefiniti|100|20|0|2|
 
3.  In queste impostazioni predefinite del server, il runtime esterno avrà probabilmente risorse insufficienti per completare la maggior parte delle attività. Per ovviare a questa situazione, è necessario modificare l'utilizzo delle risorse del server in questo modo:
  
    -   Ridurre la memoria massima che può essere usata dal motore di database.
  
    -   Aumentare la memoria massima che può essere utilizzata per il processo esterno.

## <a name="modify-server-resource-usage"></a>Modificare l'utilizzo delle risorse del server

1.  In [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)] eseguire l'istruzione seguente per limitare l'utilizzo della memoria di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] al **60%** del valore specificato nell'impostazione 'max server memory'.

    ```sql
    ALTER RESOURCE POOL "default" WITH (max_memory_percent = 60);
    ```
  
2.  Analogamente, eseguire l'istruzione seguente per limitare l'uso di memoria da parte dei processi esterni al **40%** delle risorse totali del computer.
  
    ```sql
    ALTER EXTERNAL RESOURCE POOL "default" WITH (max_memory_percent = 40);
    ```
  
3.  Per applicare queste modifiche, è necessario riconfigurare e riavviare Resource Governor in questo modo:
  
    ```sql
    ALTER RESOURCE GOVERNOR RECONFIGURE;
    ```
  
    > [!NOTE]
    >  Queste sono le impostazioni suggerite solo avviare con; è necessario valutare i machine learning attività alla luce di altri processi del server per determinare il giusto per l'ambiente e il carico di lavoro.

## <a name="create-a-user-defined-external-resource-pool"></a>Creare un pool di risorse esterno definito dall'utente
  
1.  Qualsiasi modifica apportata alla configurazione di Resource Governor viene applicata al server complessivamente e influisce sui carichi di lavoro che usano i pool predefiniti per il server, nonché su quelli che usano i pool esterni.
  
     Di conseguenza, per fornire un controllo con granularità più fine sui carichi di lavoro che devono avere la precedenza, è possibile creare un nuovo pool di risorse esterno definito dall'utente. È anche consigliabile definire una funzione di classificazione e assegnarla al pool di risorse esterno. Il **esterno** (parola chiave) è una novità.
  
     Per iniziare, creare un nuovo *pool di risorse esterno definito dall'utente*. Nell'esempio seguente il pool si chiama **ds_ep**.
  
    ```sql
    CREATE EXTERNAL RESOURCE POOL ds_ep WITH (max_memory_percent = 40);
    ```

2.  Creare un gruppo di carico di lavoro denominato `ds_wg` da usare per la gestione delle richieste di sessione. Per le query SQL verrà usato il pool predefinito, mentre per tutti i processi esterni le query useranno il pool `ds_ep`.
  
    ```sql
    CREATE WORKLOAD GROUP ds_wg WITH (importance = medium) USING "default", EXTERNAL "ds_ep";
    ```
  
     Le richieste vengono assegnate al gruppo predefinito ogni volta che la richiesta non può essere classificata o se si è verificato un altro errore di classificazione.
  
     Per altre informazioni, vedere [Gruppo di carico di lavoro di Resource Governor](../../relational-databases/resource-governor/resource-governor-workload-group.md) e [CREATE WORKLOAD GROUP &#40;Transact-SQL&#41;](../../t-sql/statements/create-workload-group-transact-sql.md).
  
## <a name="create-a-classification-function-for-machine-learning"></a>Creare una funzione di classificazione per machine learning
  
Una funzione di classificazione esamina le attività in ingresso e determina se l'attività possa essere eseguita usando il pool di risorse corrente. Le attività che non soddisfano i criteri della funzione di classificazione vengono riassegnate al pool di risorse predefinito del server.
  
1. Iniziare specificando una funzione di classificazione deve essere utilizzata da Resource Governor per determinare i pool di risorse. È possibile assegnare un **null** come segnaposto per la funzione di classificazione.
  
    ```sql
    ALTER RESOURCE GOVERNOR WITH (classifier_function = NULL);
    ALTER RESOURCE GOVERNOR RECONFIGURE;
    ```
  
     Per altre informazioni, vedere [ALTER RESOURCE GOVERNOR &#40;Transact-SQL&#41;](../../t-sql/statements/alter-resource-governor-transact-sql.md).
  
2.  Nella funzione di classificazione per ogni pool di risorse, definire il tipo di istruzioni o le richieste in ingresso che devono essere assegnate al pool di risorse.
  
     Ad esempio, la funzione seguente restituisce il nome dello schema assegnato al pool di risorse esterno definito dall'utente se l'applicazione che ha inviato la richiesta è 'Microsoft R Host' o 'RStudio'. In caso contrario, restituisce il pool di risorse predefinito.
  
    ```sql
    USE master
    GO
    CREATE FUNCTION is_ds_apps()
    RETURNS sysname
    WITH schemabinding
    AS
    BEGIN
        IF program_name() in ('Microsoft R Host', 'RStudio') RETURN 'ds_wg';
        RETURN 'default'
        END;
    GO
    ```
  
3.  Dopo la creazione della funzione, riconfigurare il gruppo di risorse in modo da assegnare la nuova funzione di classificazione al gruppo di risorse esterno definito in precedenza.
  
    ```sql
    ALTER RESOURCE GOVERNOR WITH  (classifier_function = dbo.is_ds_apps);
    ALTER RESOURCE GOVERNOR WITH reconfigure;
    GO
    ```

## <a name="verify-new-resource-pools-and-affinity"></a>Verificare i nuovi pool di risorse e l'affinità

Per verificare che le modifiche sono state apportate, controllare la configurazione di memoria del server e della CPU per ognuno dei gruppi del carico di lavoro associati a questi pool di risorse di istanza:

+ il pool predefinito per il [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] server
+ pool di risorse predefinito per i processi esterni
+ il pool definiti dall'utente per processi esterni

1. Eseguire l'istruzione seguente per visualizzare tutti i gruppi di carico di lavoro:

    ```sql
    SELECT * FROM sys.resource_governor_workload_groups;
    ```

    **Risultati di esempio**

    |group_id|name|importance|request_max_memory_grant_percent|request_max_cpu_time_sec|request_memory_grant_timeout_sec|max_dop|group_max_requests pool_id|pool_idd|external_pool_id|
    |-|-|-|-|-|-|-|-|-|-|
    |1|interno|Media|25|0|0|0|0|1|2|
    |2|predefiniti|Media|25|0|0|0|0|2|2|
    |256|ds_wg|Media|25|0|0|0|0|2|256|
  
2.  Utilizzare la nuova vista del catalogo, [Sys. resource_governor_external_resource_pools &#40; Transact-SQL &#41; ](../../relational-databases/system-catalog-views/sys-resource-governor-external-resource-pools-transact-sql.md), per visualizzare tutti i pool di risorse esterne.
  
    ```sql
    SELECT * FROM sys.resource_governor_external_resource_pools;
    ```

    **Risultati di esempio**
    
    |external_pool_id|name|max_cpu_percent|max_memory_percent|max_processes|version|
    |-|-|-|-|-|-|
    |2|predefiniti|100|20|0|2|
    |256|ds_ep|100|40|0|1|
  
     Per altre informazioni, vedere [Viste del catalogo di Resource Governor &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/resource-governor-catalog-views-transact-sql.md).
  
3.  Eseguire l'istruzione seguente per restituire le informazioni sulle risorse di computer sono di affinità con il pool di risorse esterne, se applicabile:
  
    ```sql
    SELECT * FROM sys.resource_governor_external_resource_pool_affinity;
    ```
  
     In questo caso, poiché i pool sono stati creati con affinità AUTO, non viene visualizzata alcuna informazione. Per altre informazioni, vedere [sys.dm_resource_governor_resource_pool_affinity &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-resource-governor-resource-pool-affinity-transact-sql.md).

## <a name="see-also"></a>Vedere anche

Per ulteriori informazioni sulla gestione delle risorse di server, vedere:

+  [Resource Governor](../../relational-databases/resource-governor/resource-governor.md) 
+ [Viste a gestione dinamica &#40; relative a Resource Governor Transact-SQL &#41;](../../relational-databases/system-dynamic-management-views/resource-governor-related-dynamic-management-views-transact-sql.md)

Per una panoramica di governance delle risorse per machine learning, vedere:

+  [Governance delle risorse per servizi di Machine Learning](../../advanced-analytics/r/resource-governance-for-r-services.md)
