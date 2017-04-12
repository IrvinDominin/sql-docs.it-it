---
title: "Istruzioni SELECT e JOIN da viste di sistema per eventi estesi in SQL Server | Microsoft Docs"
ms.custom: ""
ms.date: "08/02/2016"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "database-engine"
  - "xevents"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 04521d7f-588c-4259-abc2-1a2857eb05ec
caps.latest.revision: 6
author: "MightyPen"
ms.author: "genemi"
manager: "jhubbard"
caps.handback.revision: 6
---
# Istruzioni SELECT e JOIN da viste di sistema per eventi estesi in SQL Server
[!INCLUDE[tsql-appliesto-ss2014-asdb-xxxx-xxx_md](../../includes/tsql-appliesto-ss2014-asdb-xxxx-xxx-md.md)]


In questo articolo vengono spiegati i due set di viste di sistema correlate agli eventi estesi in Microsoft SQL Server e nel servizio cloud del database SQL di Azure. L'articolo illustra:

- Come unire diverse viste di sistema con l'istruzione JOIN.
- Come selezionare tipi particolari di informazioni di viste di sistema con l'istruzione SELECT.
- In che modo le stesse informazioni di una sessione evento vengono rappresentate dal punto di vista di tecnologie diverse. Ciò consente di approfondire la comprensione di ciascun punto di vista.


La maggior parte degli esempi è scritta per SQL Server ma con qualche semplice modifica può funzionare anche nel database SQL di Azure.



## A. Informazioni di base


Per gli eventi estesi sono disponibili due set di viste di sistema:


#### Viste del catalogo:

- In queste viste sono archiviate informazioni sulla *definizione* di ogni sessione evento creata da [CREATE EVENT SESSION](../../t-sql/statements/create-event-session-transact-sql.md) o da un comando equivalente dell'interfaccia utente di SSMS. Queste viste, però, non hanno informazioni su eventuali sessioni in esecuzione.
    - Ad esempio, se **Esplora oggetti** di SSMS indica che non sono definite sessioni evento, un'istruzione SELECT sulla vista *sys.server_event_session_targets* restituirebbe zero righe.


- Prefissi nomi:
    - *sys.server\_event\_session\** è il prefisso nome per SQL Server.
    - *sys.database\_event\_session\** è il prefisso nome per il database SQL.


#### Viste a gestione dinamica (DMV, Dynamic Management View):

- Archiviano informazioni relative all'*attività corrente* di sessioni evento in esecuzione. Queste DMV, tuttavia, hanno poche informazioni sulla definizione delle sessioni.
    - Anche se tutte le sessioni evento sono arrestate, un'istruzione SELECT dalla vista *sys.dm_xe_packages* restituirebbe comunque un certo numero di righe, perché all'avvio del server nella memoria attiva vengono caricati diversi pacchetti.
    - Per lo stesso motivo anche *sys.dm_xe_objects* *sys.dm_xe_object_columns* restituirebbe un certo numero di righe.


- Prefisso nome per DMV di eventi estesi:
    - *sys.dm\_xe\_\** è il prefisso nome per SQL Server.
    - *sys.dm\_xe\_database\_\** è in genere il prefisso nome per il database SQL.


#### Autorizzazioni:


Per eseguire istruzioni SELECT dalle viste di sistema, è necessaria l'autorizzazione seguente:

- VIEW SERVER STATE nel caso di Microsoft SQL Server.
- VIEW DATABASE STATE nel caso del database SQL di Azure.


<a name="section_B_catalog_views"></a>

## B. Vista del catalogo


In questa sezione vengono abbinati e messi in correlazione i punti di vista di tre tecnologie diverse nella stessa sessione evento. La sessione è definita e visibile in **Esplora oggetti** di SQL Server Management Studio (SSMS.exe) ma non è in esecuzione.

Ogni mese è consigliabile [installare l'aggiornamento più recente di SSMS](http://msdn.microsoft.com/library/mt238290.aspx), per evitare errori imprevisti.


La documentazione di riferimento sulle viste del catalogo per gli eventi estesi è in [Viste del catalogo degli eventi estesi (Transact-SQL)](../../relational-databases/system-catalog-views/extended-events-catalog-views-transact-sql.md).


&nbsp;



#### Sequenza della sezione B:


- [B.1 Punto di vista dell'interfaccia utente di SSMS](#section_B_1_SSMS_UI_perspective)
    - Creare la definizione della sessione evento tramite l'interfaccia utente di SSMS. Sono riportati screenshot dettagliati.


- [B. 2 Punto di vista di Transact-SQL](#section_B_2_TSQL_perspective)
    - Usare il menu di scelta rapida di SSMS per decompilare la sessione evento definita nell'istruzione Transact-SQL equivalente **CREATE EVENT SESSION**. Il codice T-SQL illustra una corrispondenza esatta con le scelte visualizzate negli screenshot di SSMS.


- [B.3 Punto di vista di SELECT JOIN UNION della vista del catalogo](#section_B_3_Catalog_view_S_J_UNION)
    - Eseguire un'istruzione T-SQL SELECT dalle viste del catalogo di sistema per la sessione evento. I risultati corrispondono alle specifiche dell'istruzione **CREATE EVENT SESSION**.


&nbsp;



<a name="section_B_1_SSMS_UI_perspective"></a>

### B.1 Punto di vista dell'interfaccia utente di SSMS


In **Esplora oggetti** di SSMS è possibile avviare la finestra di dialogo **Nuova sessione**. A tale scopo espandere **Gestione** > **Eventi estesi** e quindi fare clic con il pulsante destro del mouse su **Sessioni** > **Nuova sessione**.

Nella finestra di dialogo **Nuova sessione**, nella prima sezione, **Generale**, è selezionata l'opzione **Avviare la sessione eventi all'avvio del server**.

![Nuova sessione > Generale, Avviare la sessione eventi all'avvio del server.](../../relational-databases/extended-events/media/xevents-ssms-ac105-eventname-startup.png)


Quindi, nella sezione **Eventi** è stato scelto l'evento **lock_deadlock**. Per questo evento sono state selezionate tre **Azioni**. Ciò significa che il pulsante **Configura** è stato selezionato. Il pulsante, infatti, ora è disabilitato.

![Nuova sessione > Eventi, Campi globali (azioni)](../../relational-databases/extended-events/media/xevents-ssms-ac110-actions-global.png)


<a name="resource_type_PAGE_cat_view"></a>

Quindi, sempre nella sezione **Eventi** > **Configura**, è possibile vedere che [**resource_type** è stato impostato su **PAGE**](#resource_type_dmv_actual_row). Ciò significa che i dati eventi non verranno inviati dal motore degli eventi alla destinazione se il valore **resource_type** è diverso da **PAGE**.

È anche possibile vedere altri predicati di filtri per il nome del database e per un contatore.

![Nuova sessione > Eventi, campi dei predicati dei filtri (Azioni)](../../relational-databases/extended-events/media/xevents-ssms-ac115-predicate-db.png)


Quindi, nella sezione **Archiviazione dati** è possibile vedere che **event_file** è stato scelto come destinazione. È anche possibile vedere che è stata selezionata l'opzione **Consenti rollover dei file**.

![Nuova sessione > Archiviazione dati, eventfile_enablefileroleover](../../relational-databases/extended-events/media/xevents-ssms-ac120-target-eventfile.png)


Infine, nella sezione **Avanzate** è possibile vedere che il valore **Latenza di recapito massima** è stato ridotto a 4 secondi.

![Nuova sessione > Avanzate, Latenza di recapito massima](../../relational-databases/extended-events/media/xevents-ssms-ac125-latency4.png)


E questo è tutto per quanto riguarda il punto di vista dell'interfaccia di SSMS sulla definizione di sessioni eventi.


<a name="section_B_2_TSQL_perspective"></a>

### B. 2 Punto di vista di Transact-SQL


Indipendentemente dalla modalità di creazione della definizione di una sessione evento, dall'interfaccia utente di SSMS la sessione può essere decompilata in uno script Transact-SQL perfettamente corrispondente. È possibile esaminare gli screenshot precedenti della finestra di dialogo Nuova sessione e confrontare le specifiche visibili con le clausole dello script T-SQL **CREATE EVENT SESSION** generato riportato di seguito.

Per decompilare una sessione evento, in **Esplora oggetti** è possibile fare clic con il pulsante destro del mouse sul nodo della sessione e quindi scegliere **Crea script per sessione** > **CREATE to** (Crea in)  > **Appunti**.

Lo script T-SQL seguente è stato creato tramite decompilazione con SSMS. Quindi lo script è stato abbellito manualmente manipolando in modo strategico solo gli spazi.


```tsql
CREATE EVENT SESSION [event_session_test3]
    ON SERVER  -- Or, if on Azure SQL Database, ON DATABASE.

    ADD EVENT sqlserver.lock_deadlock
    (
        SET
            collect_database_name = (1)
        ACTION
        (
            package0  .collect_system_time,
            package0  .event_sequence,
            sqlserver .client_hostname
        )
        WHERE
        (
            [database_name]           = N'InMemTest2'
            AND [package0].[counter] <= (16)
            AND [resource_type]       = (6)
        )
    )

    ADD TARGET package0.event_file
    (
        SET
            filename           = N'C:\Junk\event_session_test3_EF.xel',
            max_file_size      = (20),
            max_rollover_files = (2)
    )

    WITH
    (
        MAX_MEMORY            = 4096 KB,
        EVENT_RETENTION_MODE  = ALLOW_SINGLE_EVENT_LOSS,
        MAX_DISPATCH_LATENCY  = 4 SECONDS,
        MAX_EVENT_SIZE        = 0 KB,
        MEMORY_PARTITION_MODE = NONE,
        TRACK_CAUSALITY       = OFF,
        STARTUP_STATE         = ON
    );
```


E questo è tutto per quanto riguarda il punto di vista di T-SQL.


<a name="section_B_3_Catalog_view_S_J_UNION"></a>

### B.3 Punto di vista di SELECT JOIN UNION della vista del catalogo


Niente paura, l'istruzione T-SQL SELECT è lunga solo perché contiene diverse istruzioni UNION che uniscono diverse istruzioni SELECT più brevi. Ognuna delle istruzioni SELECT più brevi può essere eseguita separatamente. Le istruzioni SELECT più brevi illustrano come devono essere unite tramite JOIN le diverse viste del catalogo di sistema.


```tsql
SELECT
        s.name        AS [Session-Name],
        '1_EVENT'     AS [Clause-Type],
        'Event-Name'  AS [Parameter-Name],
        e.name        AS [Parameter-Value]
    FROM
              sys.server_event_sessions         AS s
        JOIN  sys.server_event_session_events   AS e

            ON  e.event_session_id = s.event_session_id
    WHERE
        s.name = 'event_session_test3'

UNION ALL
SELECT
        s.name         AS [Session-Name],
        '2_EVENT_SET'  AS [Clause-Type],
        f.name         AS [Parameter-Name],
        f.value        AS [Parameter-Value]
    FROM
              sys.server_event_sessions         AS s
        JOIN  sys.server_event_session_events   AS e

            ON  e.event_session_id = s.event_session_id

        JOIN  sys.server_event_session_fields   As f

            ON  f.event_session_id = s.event_session_id
            AND f.object_id        = e.event_id
    WHERE
        s.name = 'event_session_test3'

UNION ALL
SELECT
        s.name              AS [Session-Name],
        '3_EVENT_ACTION'    AS [Clause-Type],

        e.package + '.' + a.name
                            AS [Parameter-Name],

        '(Not_Applicable)'  AS [Parameter-Value]
    FROM
              sys.server_event_sessions         AS s
        JOIN  sys.server_event_session_events   AS e

            ON  e.event_session_id = s.event_session_id

        JOIN  sys.server_event_session_actions  As a

            ON  a.event_session_id = s.event_session_id
            AND a.event_id         = e.event_id
    WHERE
        s.name = 'event_session_test3'

UNION ALL
SELECT
        s.name                AS [Session-Name],
        '4_EVENT_PREDICATES'  AS [Clause-Type],
        e.predicate           AS [Parameter-Name],
        '(Not_Applicable)'    AS [Parameter-Value]
    FROM
              sys.server_event_sessions         AS s
        JOIN  sys.server_event_session_events   AS e

            ON  e.event_session_id = s.event_session_id
    WHERE
        s.name = 'event_session_test3'

UNION ALL
SELECT
        s.name              AS [Session-Name],
        '5_TARGET'          AS [Clause-Type],
        t.name              AS [Parameter-Name],
        '(Not_Applicable)'  AS [Parameter-Value]
    FROM
              sys.server_event_sessions         AS s
        JOIN  sys.server_event_session_targets  AS t

            ON  t.event_session_id = s.event_session_id
    WHERE
        s.name = 'event_session_test3'

UNION ALL
SELECT
        s.name          AS [Session-Name],
        '6_TARGET_SET'  AS [Clause-Type],
        f.name          AS [Parameter-Name],
        f.value         AS [Parameter-Value]
    FROM
              sys.server_event_sessions         AS s
        JOIN  sys.server_event_session_targets  AS t

            ON  t.event_session_id = s.event_session_id

        JOIN  sys.server_event_session_fields   As f

            ON  f.event_session_id = s.event_session_id
            AND f.object_id        = t.target_id
    WHERE
        s.name = 'event_session_test3'

UNION ALL
SELECT
        s.name               AS [Session-Name],
        '7_WITH_MAX_MEMORY'  AS [Clause-Type],
        'max_memory'         AS [Parameter-Name],
        s.max_memory         AS [Parameter-Value]
    FROM
              sys.server_event_sessions  AS s
    WHERE
        s.name = 'event_session_test3'

UNION ALL
SELECT
        s.name                  AS [Session-Name],
        '7_WITH_STARTUP_STATE'  AS [Clause-Type],
        'startup_state'         AS [Parameter-Name],
        s.startup_state         AS [Parameter-Value]
    FROM
              sys.server_event_sessions  AS s
    WHERE
        s.name = 'event_session_test3'

ORDER BY
    [Session-Name],
    [Clause-Type],
    [Parameter-Name]
;
```


#### Output


Di seguito è riportato l'output effettivo dell'esecuzione dell'istruzione SELECT JOIN UNION precedente. I nomi dei parametri di output e i valori corrispondono a ciò che è chiaramente visibile nell'istruzione CREATE EVENT SESSION precedente.


```
Session-Name          Clause-Type            Parameter-Name                  Parameter-Value
------------          -----------            --------------                  ---------------
event_session_test3   1_EVENT                Event-Name                      lock_deadlock
event_session_test3   2_EVENT_SET            collect_database_name           1
event_session_test3   3_EVENT_ACTION         sqlserver.client_hostname       (Not_Applicable)
event_session_test3   3_EVENT_ACTION         sqlserver.collect_system_time   (Not_Applicable)
event_session_test3   3_EVENT_ACTION         sqlserver.event_sequence        (Not_Applicable)
event_session_test3   4_EVENT_PREDICATES     ([sqlserver].[equal_i_sql_unicode_string]([database_name],N'InMemTest2') AND [package0].[counter]<=(16))   (Not_Applicable)
event_session_test3   5_TARGET               event_file                      (Not_Applicable)
event_session_test3   6_TARGET_SET           filename                        C:\Junk\event_session_test3_EF.xel
event_session_test3   6_TARGET_SET           max_file_size                   20
event_session_test3   6_TARGET_SET           max_rollover_files              2
event_session_test3   7_WITH_MAX_MEMORY      max_memory                      4096
event_session_test3   7_WITH_STARTUP_STATE   startup_state                   1
```


E questo è tutto per quanto riguarda la sezione sulle viste del catalogo.



<a name="section_C_DMVs"></a>

## C. Viste a gestione dinamica (DMV)


Si passerà ora a parlare delle DMV. In questa sezione vengono illustrate diverse istruzioni SELECT Transact-SQL, ognuna con uno scopo utile per le attività aziendali. Le istruzioni SELECT illustrano anche come unire le DMV con JOIN per eventuali altri usi voluti.


La documentazione di riferimento per le DMV è disponibile in [Viste a gestione dinamica degli eventi estesi](../../relational-databases/system-dynamic-management-views/extended-events-dynamic-management-views.md)


Se non diversamente specificato, in questo articolo le righe di output effettivo delle istruzioni SELECT che seguono sono generate da SQL Server 2016.


Ecco l'elenco delle istruzioni SELECT presenti in questa sezione C, dedicata alle DMV:

- [C.1 Elenco di tutti i pacchetti](#section_C_1_list_packages)
- [C.2 Numero dei tipi di oggetto](#section_C_2_count_object_type)
- [C.3 Istruzione SELECT per selezionare tutti gli elementi disponibili ordinati per tipo](#section_C_3_select_all_available_objects)
- [C.4 Campi di dati disponibili per l'evento](#section_C_4_data_fields)
- [C.5 *sys.dm_xe_map_values* e campi evento](#section_C_5_map_values_fields)
- [C.6 Parametri per le destinazioni](#section_C_6_parameters_targets)
- [C.7 Istruzione SELECT di DMV con cast della colonna target_data in XML](#section_C_7_dmv_select_target_data_column)
- [C.8 Istruzione SELECT da una funzione che recupera dati event_file dall'unità disco](#section_C_8_select_function_disk)



<a name="section_C_1_list_packages"></a>

### C.1 Elenco di tutti i pacchetti


Tutti gli oggetti che è possibile usare nell'area degli eventi estesi provengono da pacchetti caricati nel sistema. In questa sezione sono elencati tutti i pacchetti e le relative descrizioni.


```tsql
SELECT  --C.1
        p.name         AS [Package],
        p.description  AS [Package-Description]
    FROM
        sys.dm_xe_packages  AS p
    ORDER BY
        p.name;
```


#### Output

Ecco l'elenco dei pacchetti.


```
/***  (The unique p.guid values are not shown.)
Package        Package-Description
-------        -------------------
filestream     Extended events for SQL Server FILESTREAM and FileTable
package0       Default package. Contains all standard types, maps, compare operators, actions and targets
qds            Extended events for Query Store
SecAudit       Security Audit Events
sqlclr         Extended events for SQL CLR
sqlos          Extended events for SQL Operating System
SQLSatellite   Extended events for SQL Satellite
sqlserver      Extended events for Microsoft SQL Server
sqlserver      Extended events for Microsoft SQL Server
sqlserver      Extended events for Microsoft SQL Server
sqlsni         Extended events for Microsoft SQL Server
ucs            Extended events for Unified Communications Stack
XtpCompile     Extended events for the XTP Compile
XtpEngine      Extended events for the XTP Engine
XtpRuntime     Extended events for the XTP Runtime
***/
```


*Definizioni degli acronimi riportati qui sopra:*

- clr = Common Language Runtime (.NET)
- qds = Query Data Store (archivio dati query)
- sni = Server Network Interface (interfaccia di rete del server)
- ucs = Unified Communications Stack (stack delle comunicazioni unificate)
- xtp = Extreme Transaction Processing


<a name="section_C_2_count_object_type"></a>

### C.2 Numero dei tipi di oggetto


In questa sezione è illustrato il tipo degli oggetti contenuti nei pacchetti eventi. È visualizzato l'elenco completo di tutti i tipi di oggetto presenti in *sys.dm\_xe\_objects*, nonché il numero per ciascun tipo.


```tsql
SELECT  --C.2
        Count(*)  AS [Count-of-Type],
        o.object_type
    FROM
        sys.dm_xe_objects  AS o
    GROUP BY
        o.object_type
    ORDER BY
        1  DESC;
```


#### Output

Di seguito è riportato il numero di oggetti per ogni tipo di oggetto. Sono presenti circa 1915 oggetti.


```
/***  Actual output, sum is about 1915:

Count-of-Type   object_type
-------------   -----------
1303            event
351             map
84              message
77              pred_compare
53              action
46              pred_source
28              type
17              target
***/
```


<a name="section_C_3_select_all_available_objects"></a>

### C.3 Istruzione SELECT per selezionare tutti gli elementi disponibili ordinati per tipo


L'istruzione SELECT seguente restituisce circa 1915 righe, una per ogni oggetto.



```tsql
SELECT  --C.3
        o.object_type  AS [Type-of-Item],
        p.name         AS [Package],
        o.name         AS [Item],
        o.description  AS [Item-Description]
    FROM
             sys.dm_xe_objects  AS o
        JOIN sys.dm_xe_packages AS p  ON o.package_guid = p.guid
    WHERE
        o.object_type IN ('action' , 'target' , 'pred_source')
        AND
        (
            (o.capabilities & 1) = 0
            OR
            o.capabilities IS NULL
        )
    ORDER BY
        [Type-of-Item],
        [Package],
        [Item];
```


#### Output

Per risvegliare l'interesse, di seguito è riportato un campione arbitrario degli oggetti restituiti dall'istruzione SELECT precedente.


```
/***
Type-of-Item   Package        Item                          Item-Description
------------   -------        ----                          ----------------
action         package0       callstack                     Collect the current call stack
action         package0       debug_break                   Break the process in the default debugger
action         sqlos          task_time                     Collect current task execution time
action         sqlserver      sql_text                      Collect SQL text
event          qds            query_store_aprc_regression   Fired when Query Store detects regression in query plan performance
event          SQLSatellite   connection_accept             Occurs when a new connection is accepted. This event serves to log all connection attempts.
event          XtpCompile     cgen                          Occurs at start of C code generation.
map            qds            aprc_state                    Query Store Automatic Plan Regression Correction state
message        package0       histogram_event_required      A value is required for the parameter 'filtering_event_name' when source type is 0.
pred_compare   package0       equal_ansi_string             Equality operator between two ANSI string values
pred_compare   sqlserver      equal_i_sql_ansi_string       Equality operator between two SQL ANSI string values
pred_source    sqlos          task_execution_time           Get current task execution time
pred_source    sqlserver      client_app_name               Get the current client application name
target         package0       etw_classic_sync_target       Event Tracing for Windows (ETW) Synchronous Target
target         package0       event_counter                 Use the event_counter target to count the number of occurrences of each event in the event session.
target         package0       event_file                    Use the event_file target to save the event data to an XEL file, which can be archived and used for later analysis and review. You can merge multiple XEL files to view the combined data from separate event sessions.
target         package0       histogram                     Use the histogram target to aggregate event data based on a specific event data field or action associated with the event. The histogram allows you to analyze distribution of the event data over the period of the event session.
target         package0       pair_matching                 Pairing target
target         package0       ring_buffer                   Asynchronous ring buffer target.
type           package0       xml                           Well formed XML fragment
***/
```



<a name="section_C_4_data_fields"></a>

### C.4 Campi di dati disponibili per l'evento


L'istruzione SELECT seguente restituisce tutti i campi dati specifici di un particolare tipo di evento.

- Si noti l'elemento della clausola WHERE: *column_type = 'data'*.
- È anche necessario modificare il valore della clausola WHERE in *o.name =*.


```tsql
SELECT  -- C.4
        p.name         AS [Package],
        c.object_name  AS [Event],
        c.name         AS [Column-for-Predicate-Data],
        c.description  AS [Column-Description]
    FROM
              sys.dm_xe_object_columns  AS c
        JOIN  sys.dm_xe_objects         AS o

            ON  o.name = c.object_name

        JOIN  sys.dm_xe_packages        AS p

            ON  p.guid = o.package_guid
    WHERE
        c.column_type = 'data'
        AND
        o.object_type = 'event'
        AND
        o.name        = '<EVENT-NAME-HERE!>'  --'lock_deadlock'
    ORDER BY
        [Package],
        [Event],
        [Column-for-Predicate-Data];
```


#### Output

Le righe seguenti sono state restituite dall'istruzione SELECT, WHERE precedente `o.name = 'lock_deadlock'`:

- Ogni riga rappresenta un filtro facoltativo per l'evento *sqlserver.lock_deadlock*.
- La colonna *\[Column-Description\]* è stata omessa dalla visualizzazione seguente. Il valore di questa colonna corrisponde spesso a NULL.


```
/***
Actual output, except for the omitted Description column which is often NULL.
These rows are where object_type = 'lock_deadlock'.

Package     Event           Column-for-Predicate-Data
-------     -----           -------------------------
sqlserver   lock_deadlock   associated_object_id
sqlserver   lock_deadlock   database_id
sqlserver   lock_deadlock   database_name
sqlserver   lock_deadlock   deadlock_id
sqlserver   lock_deadlock   duration
sqlserver   lock_deadlock   lockspace_nest_id
sqlserver   lock_deadlock   lockspace_sub_id
sqlserver   lock_deadlock   lockspace_workspace_id
sqlserver   lock_deadlock   mode
sqlserver   lock_deadlock   object_id
sqlserver   lock_deadlock   owner_type
sqlserver   lock_deadlock   resource_0
sqlserver   lock_deadlock   resource_1
sqlserver   lock_deadlock   resource_2
sqlserver   lock_deadlock   resource_description
sqlserver   lock_deadlock   resource_type
sqlserver   lock_deadlock   transaction_id
***/
```



<a name="section_C_5_map_values_fields"></a>

### C.5 *sys.dm_xe_map_values* e campi evento


L'istruzione SELECT seguente inserisce una clausola JOIN in una vista complessa, *sys.dm_xe_map_values*.

Lo scopo dell'istruzione SELECT è di visualizzare i numerosi campi che è possibile scegliere per la sessione evento. I campi evento possono essere usati in due modi:

- Per scegliere i valori dei campi da scrivere nella destinazione per ogni occorrenza dell'evento.
- Per filtrare le occorrenze dell'evento da inviare e quelle da non inviare alla destinazione.


```tsql
SELECT  --C.5
        dp.name         AS [Package],
        do.name         AS [Object],
        do.object_type  AS [Object-Type],
        'o--c'     AS [O--C],
        dc.name         AS [Column],
        dc.type_name    AS [Column-Type-Name],
        dc.column_type  AS [Column-Type],
        dc.column_value AS [Column-Value],
        'c--m'     AS [C--M],
        dm.map_value    AS [Map-Value],
        dm.map_key      AS [Map-Key]
    FROM
              sys.dm_xe_objects         AS do
        JOIN  sys.dm_xe_object_columns  AS dc

            ON  dc.object_name = do.name

        JOIN  sys.dm_xe_map_values      AS dm

            ON  dm.name = dc.type_name

        JOIN  sys.dm_xe_packages        AS dp

            ON  dp.guid = do.package_guid
    WHERE
        do.object_type = 'event'
        AND
        do.name        = '<YOUR-EVENT-NAME-HERE!>'  --'lock_deadlock'
    ORDER BY
        [Package],
        [Object],
        [Column],
        [Map-Value];
```


#### Output

<a name="resource_type_dmv_actual_row"></a>

Di seguito è riportato un campione delle 153 righe effettive di output dell'istruzione SELECT T-SQL precedente. La riga per **resource_type** è [pertinente](#resource_type_PAGE_cat_view) al filtro predicato usato nell'esempio **event_session_test3** in un altro punto di questo articolo.


```
/***  5 sampled rows from the actual 153 rows returned.
    NOTE:  'resource_type' under 'Column'.

Package     Object          Object-Type   O--C   Column          Column-Type-Name     Column-Type   Column-Value   C--M   Map-Value        Map-Key
-------     ------          -----------   ----   ------          ----------------     -----------   ------------   ----   ---------        -------
sqlserver   lock_deadlock   event         o--c   CHANNEL         etw_channel          readonly      2              c--m   Operational      4
sqlserver   lock_deadlock   event         o--c   KEYWORD         keyword_map          readonly      16             c--m   access_methods   1024
sqlserver   lock_deadlock   event         o--c   mode            lock_mode            data          NULL           c--m   IX               8
sqlserver   lock_deadlock   event         o--c   owner_type      lock_owner_type      data          NULL           c--m   Cursor           2
sqlserver   lock_deadlock   event         o--c   resource_type   lock_resource_type   data          NULL           c--m   PAGE             6

Therefore, on your CREATE EVENT SESSION statement, in its ADD EVENT WHERE clause,
you could put:
    WHERE( ... resource_type = 6 ...)  -- Meaning:  6 = PAGE.
***/
```


<a name="section_C_6_parameters_targets"></a>

### C.6 Parametri per le destinazioni


L'istruzione SELECT seguente restituisce ogni parametro per la destinazione. Ogni parametro è contrassegnato come obbligatorio o meno. I valori assegnati ai parametri influiscono sul comportamento della destinazione.

- Si noti l'elemento della clausola WHERE: *object_type = 'customizable'*.
- È anche necessario modificare il valore della clausola WHERE in *o.name =*.


```tsql
SELECT  --C.6
        p.name        AS [Package],
        o.name        AS [Target],
        c.name        AS [Parameter],
        c.type_name   AS [Parameter-Type],

        CASE c.capabilities_desc
            WHEN 'mandatory' THEN 'YES_Mandatory'
            ELSE 'Not_mandatory'
        END  AS [IsMandatoryYN],

        c.description AS [Parameter-Description]
    FROM
              sys.dm_xe_objects   AS o
        JOIN  sys.dm_xe_packages  AS p

            ON  o.package_guid = p.guid

        LEFT OUTER JOIN  sys.dm_xe_object_columns  AS c

            ON  o.name        = c.object_name
            AND c.column_type = 'customizable'  -- !
    WHERE
        o.object_type = 'target'
        AND
        o.name     LIKE '%'    -- Or '<YOUR-TARGET-NAME-HERE!>'.
    ORDER BY
        [Package],
        [Target],
        [IsMandatoryYN]  DESC,
        [Parameter];
```


#### Output

Le righe di parametri seguenti rappresentano un subset di quelle restituite dall'istruzione SELECT precedente in SQL Server 2016.


```
/***  Actual output, all rows, where target name = 'event_file'.
Package    Target       Parameter            Parameter-Type       IsMandatoryYN   Parameter-Description
-------    ------       ---------            --------------       -------------   ---------------------
package0   event_file   filename             unicode_string_ptr   YES_Mandatory   Specifies the location and file name of the log
package0   event_file   increment            uint64               Not_mandatory   Size in MB to grow the file
package0   event_file   lazy_create_blob     boolean              Not_mandatory   Create blob upon publishing of first event buffer, not before.
package0   event_file   max_file_size        uint64               Not_mandatory   Maximum file size in MB
package0   event_file   max_rollover_files   uint32               Not_mandatory   Maximum number of files to retain
package0   event_file   metadatafile         unicode_string_ptr   Not_mandatory   Not used
***/
```


<a name="section_C_7_dmv_select_target_data_column"></a>

### C.7 Istruzione SELECT di DMV con cast della colonna target_data in XML


Questa istruzione SELECT di DMV restituisce righe di dati provenienti dalla destinazione della sessione evento attiva. Viene eseguito il cast dei dati in XML. In questo modo è possibile fare clic sulla cella restituita per visualizzarla in modo semplice in SSMS.

- Se la sessione evento viene arrestata, l'istruzione SELECT restituirà zero righe.
- È necessario modificare il valore della clausola WHERE in *s.name =*.


```tsql
SELECT  --C.7
        s.name,
        t.target_name,
        CAST(t.target_data AS XML)  AS [XML-Cast]
    FROM
              sys.dm_xe_session_targets  AS t
        JOIN  sys.dm_xe_sessions         AS s

            ON s.address = t.event_session_address
    WHERE
        s.name = '<Your-Session-Name-Here!>';
```


#### Output: l'unica riga, inclusa la cella XML

Di seguito è riportata l'unica riga di output dell'istruzione SELECT precedente. La colonna *XML-Cast* contiene una stringa XML riconosciuta come tale da SSMS. SSMS quindi comprende che la cella XML-Cast deve essere resa selezionabile.


Per questa esecuzione:

- Il valore *s.name =* è stato impostato su una sessione per l'evento *checkpoint_begin*.
- La destinazione era un *ring_buffer*.


```XML
name                              target_name   XML-Cast
----                              -----------   --------
checkpoint_session_ring_buffer2   ring_buffer   <RingBufferTarget truncated="0" processingTime="0" totalEventsProcessed="2" eventCount="2" droppedCount="0" memoryUsed="104"><event name="checkpoint_begin" package="sqlserver" timestamp="2016-07-09T01:28:23.508Z"><data name="database_id"><type name="uint32" package="package0" /><value>5</value></data></event><event name="checkpoint_begin" package="sqlserver" timestamp="2016-07-09T01:28:26.975Z"><data name="database_id"><type name="uint32" package="package0" /><value>5</value></data></event></RingBufferTarget>
```


#### Output: codice XML abbellito quando si fa clic sulla cella


Quando si fa clic sulla cella XML-Cast, compare la visualizzazione abbellita seguente.


```xml
<RingBufferTarget truncated="0" processingTime="0" totalEventsProcessed="2" eventCount="2" droppedCount="0" memoryUsed="104">
  <event name="checkpoint_begin" package="sqlserver" timestamp="2016-07-09T01:28:23.508Z">
    <data name="database_id">
      <type name="uint32" package="package0" />
      <value>5</value>
    </data>
  </event>
  <event name="checkpoint_begin" package="sqlserver" timestamp="2016-07-09T01:28:26.975Z">
    <data name="database_id">
      <type name="uint32" package="package0" />
      <value>5</value>
    </data>
  </event>
</RingBufferTarget>
```


<a name="section_C_8_select_function_disk"></a>

### C.8 Istruzione SELECT da una funzione che recupera dati event_file dall'unità disco


Si supponga che la sessione evento abbia raccolto alcuni dati e in seguito sia stata arrestata. Se la definizione della sessione prevede l'uso della destinazione event_file, è comunque possibile recuperare i dati chiamando la funzione *sys.fn_xe_target_read_file*.

- Prima di eseguire questa istruzione SELECT è necessario modificare il percorso e il nome file nel parametro della chiamata della funzione.
    - Non è necessario prestare attenzione alle cifre aggiuntive che il sistema SQL incorpora nei nomi file con estensione XEL effettivi ogni volta che si riavvia la sessione. È sufficiente specificare il nome radice e l'estensione normali.


```tsql
SELECT  --C.8
        f.module_guid,
        f.package_guid,
        f.object_name,
        f.file_name,
        f.file_offset,
        CAST(f.event_data AS XML)  AS [Event-Data-As-XML]
    FROM
        sys.fn_xe_file_target_read_file(

            '<YOUR-PATH-FILE-NAME-ROOT-HERE!>*.xel',
            --'C:\Junk\Checkpoint_Begins_ES*.xel',  -- Example.

            NULL, NULL, NULL
        )  AS f;
```


#### Output: righe restituite dalla funzione SELECT FROM


Di seguito sono riportate le righe restituite dalla funzione SELECT FROM precedente. La colonna con il codice XML, all'estrema destra, contiene i dati specifici dell'occorrenza dell'evento.


```
module_guid                            package_guid                           object_name        file_name                                                           file_offset   Event-Data-As-XML
-----------                            ------------                           -----------        ---------                                                           -----------   -----------------
D5149520-6282-11DE-8A39-0800200C9A66   03FDA7D0-91BA-45F8-9875-8B6DD0B8E9F2   checkpoint_begin   C:\Junk\Checkpoint_Begins_ES_20160615bb-_0_131125086091700000.xel   5120          <event name="checkpoint_begin" package="sqlserver" timestamp="2016-07-09T03:30:14.023Z"><data name="database_id"><value>5</value></data><action name="session_id" package="sqlserver"><value>60</value></action><action name="database_id" package="sqlserver"><value>5</value></action></event>
D5149520-6282-11DE-8A39-0800200C9A66   03FDA7D0-91BA-45F8-9875-8B6DD0B8E9F2   checkpoint_end     C:\Junk\Checkpoint_Begins_ES_20160615bb-_0_131125086091700000.xel   5120          <event name="checkpoint_end" package="sqlserver" timestamp="2016-07-09T03:30:14.025Z"><data name="database_id"><value>5</value></data></event>
D5149520-6282-11DE-8A39-0800200C9A66   03FDA7D0-91BA-45F8-9875-8B6DD0B8E9F2   checkpoint_begin   C:\Junk\Checkpoint_Begins_ES_20160615bb-_0_131125086091700000.xel   5632          <event name="checkpoint_begin" package="sqlserver" timestamp="2016-07-09T03:30:17.704Z"><data name="database_id"><value>5</value></data><action name="session_id" package="sqlserver"><value>60</value></action><action name="database_id" package="sqlserver"><value>5</value></action></event>
D5149520-6282-11DE-8A39-0800200C9A66   03FDA7D0-91BA-45F8-9875-8B6DD0B8E9F2   checkpoint_end     C:\Junk\Checkpoint_Begins_ES_20160615bb-_0_131125086091700000.xel   5632          <event name="checkpoint_end" package="sqlserver" timestamp="2016-07-09T03:30:17.709Z"><data name="database_id"><value>5</value></data></event>
```


#### Output: una cella di XML


Di seguito è riportato il contenuto della prima cella di XML, dal set di righe restituito in precedenza.


```xml
<event name="checkpoint_begin" package="sqlserver" timestamp="2016-07-09T03:30:14.023Z">
  <data name="database_id">
    <value>5</value>
  </data>
  <action name="session_id" package="sqlserver">
    <value>60</value>
  </action>
  <action name="database_id" package="sqlserver">
    <value>5</value>
  </action>
</event>
```
