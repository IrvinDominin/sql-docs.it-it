---
title: SQL Server Management Studio - Log delle modifiche (SSMS) | Microsoft Docs
ms.custom: 
ms.date: 01/30/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- tools-ssms
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 3dc76cc1-3b4c-4719-8296-f69ec1b476f9
caps.latest.revision: 72
author: stevestein
ms.author: sstein
manager: jhubbard
translationtype: Human Translation
ms.sourcegitcommit: 2edcce51c6822a89151c3c3c76fbaacb5edd54f4
ms.openlocfilehash: f2144751277bb10897e0ed39ee24dbad8a32b4ce
ms.lasthandoff: 04/11/2017

---
# <a name="sql-server-management-studio---changelog-ssms"></a>SQL Server Management Studio - Changelog (SSMS)

## <a name="ssms-1653-release"></a>SSMS versione 16.5.3
Disponibile a livello generale | Numero di build: 13.0.16106.4

In questa versione sono stati risolti i problemi seguenti:

* Risolto un problema introdotto in SSMS 16.5.2 che causava l'espansione del nodo 'Tabella' quando la tabella aveva più di una colonna di tipo sparse.

* Gli utenti possono distribuire pacchetti SSIS contenenti Gestione connessione OData per connettere una risorsa Microsoft Dynamics AX/CRM Online al catalogo SSIS. Per altre informazioni, vedere [Gestione connessione OData](https://msdn.microsoft.com/library/dn584133.aspx).

* La configurazione di Always Encrypted per una tabella esistente ha esito negativo con errori per gli oggetti correlati. [ID Connect 3103181](https://connect.microsoft.com/SQLServer/feedback/details/3103181/setting-up-always-encrypted-on-an-existing-table-fails-with-errors-on-unrelated-objects)

* La configurazione di Always Encrypted per un database esistente con più schemi non funziona. [ID Connect 3109591](https://connect.microsoft.com/SQLServer/feedback/details/3109591/sql-server-2016-always-encrypted-against-existing-database-with-multiple-schemas-doesnt-work)

* La procedura guidata Always Encrypted, Colonna crittografata ha esito negativo a causa del database che contiene viste che fanno riferimento a viste di sistema. [ID Connect 3111925](https://connect.microsoft.com/SQLServer/feedback/details/3111925/sql-server-2016-always-encrypted-encrypted-column-wizard-failed-task-failed-due-to-following-error-cannot-save-package-to-file-the-model-has-build-blocking-errors)

* Durante la crittografia con Always Encrypted, gli errori derivanti dall'aggiornamento dei moduli dopo la crittografia non vengono gestiti in modo corretto.

* Il menu *Apri recenti* non mostra i file salvati di recente. [ID Connect 3113288](https://connect.microsoft.com/SQLServer/feedback/details/3113288/ssms-2016-open-recent-menu-doesnt-show-recently-saved-files)

* SSMS è lento quando si fa clic con il pulsante destro del mouse su un indice per una tabella (tramite una connessione Internet remota). [ID Connect 3114074](https://connect.microsoft.com/SQLServer/feedback/details/3114074/ssms-slow-when-right-clicking-an-index-for-a-table-over-a-remote-internet-connection)
 
* Risolto un problema con la barra di scorrimento di SQL Designer. [ID Connect 3114856](http://connect.microsoft.com/SQLServer/feedback/details/3114856/bug-in-scrollbar-on-sql-desginer-in-ssms-2016)

* Il menu di scelta rapida per le tabelle si blocca momentaneamente 
 
* SSMS in alcuni casi genera eccezioni in Monitoraggio attività e subisce un arresto anomalo. [ID Connect 697527](https://connect.microsoft.com/SQLServer/feedback/details/697527/)

* Si verifica un arresto anomalo di SSMS 2016 con l'errore "Il processo è stato terminato a causa di un errore interno del runtime .NET in IP 71AF8579 (71AE0000) con codice di uscita 80131506"


## <a name="ssms-1651-release"></a>Versione SSMS 16.5.1
Disponibile a livello generale | Numero di build: 13.0.16100.1

* Risolto un problema per cui Invoke-Sqlcmd inserisce erroneamente più righe quando si verifica il vincolo CHECK. [Argomento Microsoft Connect: 811560](https://connect.microsoft.com/SQLServer/feedback/details/811560)

* Risolto un problema in cui le versioni localizzate non ITA non funzionano completamente durante la creazione di gruppi di disponibilità.

* Risolto un problema in cui facendo clic sul'XML del piano di query non viene aperta l'interfaccia utente SSMS corretta.


## <a name="ssms-165-release"></a>Versione SSMS 16.5
Disponibile a livello generale | Numero di build: 13.0.16000.28

* È stato risolto il problema per cui potrebbe verificarsi un arresto anomalo quando è stato fatto clic su un database con nome della tabella contenente ";:".
* È stato risolto il problema per cui le modifiche apportate alla pagina Modello nella finestra delle proprietà del database tabulare AS devono creare uno script della definizione originale. 
[Argomento Microsoft Connect: 3080744](https://connect.microsoft.com/SQLServer/feedback/details/3080744) 
* È stato risolto il problema per cui i file temporanei vengono aggiunti all'elenco "File recenti".  
[Argomento Microsoft Connect: 2558789](https://connect.microsoft.com/SQLServer/feedback/details/2558789)
* È stato risolto il problema per cui la voce del menu di gestione della compressione è disabilitata per i nodi della tabella utente nell'albero Esplora oggetti.  
[Argomento Microsoft Connect: 3104616](https://connect.microsoft.com/SQLServer/feedback/details/3104616)

* È stato risolto il problema per cui l'utente non è in grado di impostare le dimensioni del carattere per Esplora oggetti, Esplora server registrati, Esplora modelli, nonché per i dettagli di Esplora oggetto. Il carattere per le finestre di esplorazione usato sarà il tipo di carattere Ambiente.  
[Argomento Microsoft Connect: 691432](https://connect.microsoft.com/SQLServer/feedback/details/691432)

* È stato risolto il problema per cui SSMS si riconnette sempre al database predefinito quando la connessione viene interrotta.  
[Argomento Microsoft Connect: 3102337](https://connect.microsoft.com/SQLServer/feedback/details/3102337)

* Sono stati risolti numerosi problemi relativi ai valori DPI alti nella gestione dei criteri e nella finestra di modifica delle query, tra cui le icone del piano di esecuzione.

* È stato risolto il problema della mancanza dell'opzione per la configurazione del carattere e dei colori degli eventi estesi.

* È stato risolto il problema degli arresti anomali di SSMS che si verificano durante la chiusura dell'applicazione o quando si tenta di visualizzare la finestra di dialogo degli errori.


## <a name="ssms-1641-september-2016-release"></a>Versione di SSMS 16.4.1 (settembre 2016)
Disponibile a livello generale | Numero di build: 13.0.15900.1

*  È stato corretto un problema per cui veniva generato un errore durante il tentativo di modifica di una stored procedure:  
[Argomento Microsoft Connect N. 3103831](https://connect.microsoft.com/SQLServer/feedback/details/3103831)

* Nuovi cmdlet 'Read-SqlTableData', 'Read-SqlViewData' e 'Write-SqlTableData' per visualizzare e scrivere dati tramite PowerShell.  
[Scheda Read-SqlTableData di Trello](https://trello.com/c/FXVUNJ8x/131-read-sqltabledata)  
[Argomento Microsoft Connect N. 2685363](https://connect.microsoft.com/SQLServer/feedback/details/2685363)
    
* Nuovo cmdlet 'Add-SqlLogin' per abilitare nuovi scenari di gestione degli account di accesso tramite PowerShell.  
[Argomento Microsoft Connect N. 2588952](https://connect.microsoft.com/SQLServer/feedback/details/2588952)
    
*  Supporto migliorato e facilità d'uso per la connessione a vari cloud nazionali da parte degli utenti.
    
    
*  È stato corretto un problema per cui veniva generata un'eccezione di tipo memoria insufficiente.  
[Argomento Microsoft Connect N. 3062914](https://connect.microsoft.com/SQLServer/feedback/details/3062914)  
[Argomento Microsoft Connect N. 3074856](https://connect.microsoft.com/SQLServer/feedback/details/3074856)
    
*  È stato corretto un problema per cui l'opzione di filtro in base allo schema non era considerata valida.  
[Argomento Microsoft Connect N. 3058105](https://connect.microsoft.com/SQLServer/feedback/details/3058105)  
[Argomento Microsoft Connect N. 3101136](https://connect.microsoft.com/SQLServer/feedback/details/3101136)
    
*  È stato corretto un problema per cui la finestra Monitoraggio per un database con estensione non risultava accessibile.
    
*  È stato corretto un problema per cui la Guida apriva sempre contenuto online. Gli utenti possono ora decidere se preferiscono la guida online oppure offline tramite "Imposta preferenza Guida" nel menu della guida.   
[Argomento Microsoft Connect N. 2826366](https://connect.microsoft.com/SQLServer/feedback/details/2826366)
    
*  È stato corretto un problema per cui l'inserimento nello script di un modello tabulare di Analysis Services di livello 1200 non rimuoveva la password per gli script, anche se la versione del server aveva [l'oggetto modello client sincronizzato prima dell'esecuzione dello script].
    
*  È stato corretto un problema per cui l'opzione 'SELEZIONA LE PRIME N RIGHE' generava sintassi deprecata per l'operatore TOP.  
[Argomento Microsoft Connect N. 3065435](https://connect.microsoft.com/SQLServer/feedback/details/3065435)
    
*  Sono stati corretti vari problemi di layout tramite SSMS, tra cui la pagina Proprietà account di accesso e le opzioni avanzate di esecuzione query.   
[Argomento Microsoft Connect N. 3058199](https://connect.microsoft.com/SQLServer/feedback/details/3058199)  
[Argomento Microsoft Connect N. 3079122](https://connect.microsoft.com/SQLServer/feedback/details/3058199)  
[Argomento Microsoft Connect N. 3071384](https://connect.microsoft.com/SQLServer/feedback/details/3071384)
    
*  È stato corretto un problema per cui una soluzione veniva creata automaticamente ogni volta che un utente apriva una nuova finestra di query.   
[Argomento Microsoft Connect N. 2924667](https://connect.microsoft.com/SQLServer/feedback/details/2924667)    
[Argomento Microsoft Connect N. 2917742](https://connect.microsoft.com/SQLServer/feedback/details/2917742)   
[Argomento Microsoft Connect N. 2612635](https://connect.microsoft.com/SQLServer/feedback/details/2612635)
    
*  È stato corretto un problema per cui le tabelle temporali non potevano essere espanse in Esplora oggetti nei database di sistema.  
[Argomento Microsoft Connect N. 2551649](https://connect.microsoft.com/SQLServer/feedback/details/2551649)
    
*  Correzione di un problema per cui SSMS esegue una query per SELECT @@trancount dopo l'esecuzione di un batch.    
[Argomento Microsoft Connect N. 3042364](https://connect.microsoft.com/SQLServer/feedback/details/3042364)
    
*  È stato corretto un problema in Analysis Services per cui la creazione di uno script dalla pagina delle proprietà di un server generava una finestra di dialogo di connessione nascosta.
    
*  È stato corretto un problema per cui CTRL+Q non selezionava la barra degli strumenti Avvio veloce.
    
*  È stato corretto un problema per cui la modifica del valore MaxSize di un database tramite la finestra di dialogo Proprietà server è stata interrotta per i database > 2 TB.  
[Argomento Microsoft Connect n. 1231091](https://connect.microsoft.com/SQLServer/feedback/details/1231091)
    
*  È stato corretto un problema per cui la procedura guidata Ripristina database non accettava nomi di file con spazio vuoto iniziale:   
[Argomento Microsoft Connect n. 2395147](https://connect.microsoft.com/SQLServer/feedback/details/2395147)



## <a name="ssms-163-august-2016-release"></a>Versione di SSMS 16.3 (agosto 2016)
Disponibile a livello generale | Numero di versione: 13.0.15700.28

* Le versioni mensili di SSMS sono ora contrassegnate numericamente.

* [Nuova opzione di autenticazione **'Autenticazione universale di Active Directory'**](https://azure.microsoft.com/documentation/articles/sql-database-ssms-mfa-authentication/). Si tratta di un meccanismo di autenticazione basato su token di Azure Active Directory che supporta autenticazione a più fattori, password e meccanismi di autenticazione integrati.

* Nuovi modelli di eventi estesi corrispondenti alla funzionalità dei modelli di SQL Server Profiler [(Argomento Microsoft Connect N. 2543925)](https://connect.microsoft.com/SQLServer/feedback/details/2543925/sql-server-extended-events-profiler-tool). Altre informazioni sui [modelli di SQL Server Profiler](https://msdn.microsoft.com/library/ms190176.aspx)inclusi.

* Nuove finestre di dialogo Crea database e Proprietà database per i database SQL di Azure.

* Nuovi cmdlet 'Get-SqlLogin' e 'Remove-SqlLogin' per la gestione degli account di accesso di SQL Server tramite PowerShell.  
*Richieste collegate a bug segnalati dai clienti:*   
[Argomento Microsoft Connect n. 2588952.](https://connect.microsoft.com/SQLServer/feedback/details/2588952/)

* Nuovo cmdlet di PowerShell 'New-SqlColumnMasterKeySettings' che aggiunge il supporto per la creazione di chiavi master della colonna per i provider arbitrari e i percorsi delle chiavi.

* Nuova finestra di dialogo 'Crea database' per semplificare la creazione di database di SQL di Azure in SSMS>

* Supporto per la funzionalità di filtro nel nodo 'Database' di Esplora oggetti di SSMS. Passare al nodo 'Database' in Esplora oggetti e fare clic sull'icona del filtro nella barra degli strumenti di Esplora oggetti per filtrare l'elenco dei database.

* Supporto per gli account di archiviazione di tipo Azure Resource Manager (ARM) nelle procedure guidate di backup e ripristino.

* [Supporto beta iniziale per schermi ad alta risoluzione](https://blogs.msdn.microsoft.com/sqlreleaseservices/ssms-highdpi-support/).  
*Richieste collegate a bug segnalati dai clienti:*   
[Argomento Microsoft Connect N. 1129301](https://connect.microsoft.com/SQLServer/feedback/details/1129301/management-studio-is-unusable-on-a-4k-display), [Argomento Microsoft Connect N. 1858763](https://connect.microsoft.com/SQLServer/feedback/details/1858763/), [Argomento Microsoft Connect N. 1852671](https://connect.microsoft.com/SQLServer/feedback/details/1852671/), [Argomento Microsoft Connect N. 1487643](https://connect.microsoft.com/SQLServer/feedback/details/1487643/),  [Argomento Microsoft Connect N. 1355641](https://connect.microsoft.com/SQLServer/feedback/details/1355641/), [Argomento Microsoft Connect N. 2161595](https://connect.microsoft.com/SQLServer/feedback/details/2161595/), [Argomento Microsoft Connect N. 1854041](https://connect.microsoft.com/SQLServer/feedback/details/1854041/), [Argomento Microsoft Connect N. 1055617](https://connect.microsoft.com/SQLServer/feedback/details/1055617/), [Argomento Microsoft Connect N. 2448774](https://connect.microsoft.com/SQLServer/feedback/details/2448774/), [Argomento Microsoft Connect N. 1521405](https://connect.microsoft.com/SQLServer/feedback/details/1521405/), [Argomento Microsoft Connect N. 2117853](https://connect.microsoft.com/SQLServer/feedback/details/2117853/), [Argomento Microsoft Connect N. 2014256](https://connect.microsoft.com/SQLServer/feedback/details/2014256/), [Argomento Microsoft Connect N. 2162218](https://connect.microsoft.com/SQLServer/feedback/details/2162218/), [Argomento Microsoft Connect N. 2344551](https://connect.microsoft.com/SQLServer/feedback/details/2344551/), [Argomento Microsoft Connect N. 1664436](https://connect.microsoft.com/SQLServer/feedback/details/1664436/), [Argomento Microsoft Connect N. 2554043](https://connect.microsoft.com/SQLServer/feedback/details/2554043/), [Argomento Microsoft Connect N. 2983216](https://connect.microsoft.com/SQLServer/feedback/details/2983216/), [Argomento Microsoft Connect N. 2021706](https://connect.microsoft.com/SQLServer/feedback/details/2021706/)

* Miglioramenti apportati a Ottimizzazione guidata motore di database per supportare la lettura automatica di un carico di lavoro dall'archivio di query di SQL Server.

* Miglioramenti apportati a Ottimizzazione guidata motore di database per la visualizzazione delle indicazioni relative agli indici per indici columnstore cluster, indici columnstore non cluster e indici rowstore.

* Supporto per l'invio di comandi DBCC (Database Console Command) tramite i cmdlet di PowerShell per SQL Server Analysis Services.

* Correzione di bug per visualizzare testo non crittografato di colonne LOB (large object) di AlwaysEncrypted decrittografate in SSMS.  
*Richieste collegate a bug segnalati dai clienti:*   
[Argomento Microsoft Connect n. 2413024](https://connect.microsoft.com/SQLServer/feedback/details/2413024/cannot-view-cleartext-of-alwaysencrypted-lob-columns-in-ssms)

* Correzione di bug nella finestra di dialogo 	Crittografia sempre attiva per correggere l'arresto anomalo quando gli stili visivi di Windows non sono abilitati (ad esempio, abilitazione della visualizzazione con contrasto elevato).

* Correzione di bug per l'errore "Impossibile trovare il metodo" che impedisce la connessione alle istanze di SQL Server.

* Correzione di bug per l'arresto anomalo di SSMS durante la creazione di una funzione di partizione con offset di datetime.

* Correzione di bug per aggiungere o rimuovere il requisito di Microsoft .NET 3.5 per l'avvio dello strumento di amministrazione Riesecuzione distribuita (DReplay.exe).

* Correzione di bug in Creazione guidata di distribuzione di Analysis Services per supportare i nomi dei server completi.

* Correzione di bug in SSMS per visualizzare le partizioni nei modelli tabulari di Analysis Services con un modello di compatibilità 2016.  
*Richieste collegate a bug segnalati dai clienti:*   
[Argomento Microsoft Connect n. 2845053](https://connect.microsoft.com/SQLServer/feedback/details/2845053/ssms-cannot-display-partitions-in-tabular-models-in-2016-compatibility-level) 

* Miglioramenti apportati alle prestazioni e correzioni di bug in modelli tabulari di Analysis Services e SQL Server Shared Management Objects (SMO). 


---
## <a name="ssms-july-2016-hotfix-update-release"></a>Versione di SSMS dell'aggiornamento hotfix di luglio 2016 
Disponibile a livello generale | Numero di versione: 13.0.15600.2

* **Correzione di bug in SSMS per abilitare le voci di menu selezionabili con il pulsate destro del mouse mancanti**.  
*Richieste collegate a bug segnalati dai clienti:*  
[Argomento Microsoft Connect n. 2883440](https://connect.microsoft.com/SQLServer/feedback/details/2883440/lost-table-design-and-edit-top-n-rows-in-tables-context-menu)  
[Argomento Microsoft Connect n. 2909644](https://connect.microsoft.com/SQLServer/feedback/details/2909644/ssms-2016-is-missing-edit-options-against-sql-express-2014)  
[Argomento Microsoft Connect n. 2924345](https://connect.microsoft.com/SQLServer/feedback/details/2924345/some-ssms-object-explorer-right-click-menu-options-missing-in-july-update)

---
## <a name="ssms-july-2016-release"></a>Versione di SSMS di luglio 2016 
Disponibile a livello generale | Numero di versione: 13.0.15500.91

* *Modifica - 5 luglio:* **è stato migliorato il supporto per i database tabulari SQL Server 2016 (livello di compatibilità 1200) nella finestra di dialogo Analysis Services Process (Processo Analysis Services) e nella Distribuzione guidata Analysis Services.**

* *Modifica - 5 luglio:* **è disponibile una nuova opzione nella finestra di dialogo Query Execution Options (Opzioni di esecuzione query) per l'impostazione di 'XACT_ABORT'. Questa opzione, abilitata per impostazione predefinita in questa versione di SSMS, indica a SQL Server di eseguire il rollback dell'intera transazione e di interrompere il batch se si verifica un errore di run-time.**

* **Supporto per Azure SQL Data Warehouse in SSMS.**

* **Aggiornamenti significativi al modulo SQL Server PowerShell. Sono inclusi un nuovo [modulo SQL PowerShell e nuovi cmdlet per Crittografia sempre attiva, SQL Agent e i log degli errori di SQL](https://blogs.technet.microsoft.com/dataplatforminsider/2016/06/30/sql-powershell-july-2016-update)**.

* **Supporto per la generazione di script PowerShell nella procedura guidata Crittografia sempre attiva**.

* **Tempi di connessione ai database SQL di Azure significativamente migliorati.**

* **Nuova finestra di dialogo Backup to URL (Backup su URL) per supportare la creazione di credenziali di archiviazione di Azure per i backup dei database di SQL Server 2016. Questo offre un'esperienza semplificata per l'archiviazione dei backup dei database in un account di archiviazione di Azure.**
 
* **Nuova finestra di dialogo di ripristino per semplificare il ripristino di un backup del database di SQL Server 2016 dal servizio di archiviazione di Microsoft Azure.**
 
* **Correzione del bug nella progettazione di query di SSMS per consentire l'aggiunta di tabelle alla progettazione nel caso in cui un utente non disponga delle autorizzazioni SELECT necessarie.**

* **Correzione di bug per l'aggiunta del supporto IntelliSense per le funzioni TRY_CAST() e TRY_CONVERT().**  
*Richieste collegate a bug segnalati dai clienti:*  
[Argomento Microsoft Connect N. 2453461](https://connect.microsoft.com/SQLServer/feedback/details/2453461/sql-server-2012-issue-with-try-cast).

* **Correzione di bug nel modulo PowerShell per abilitare il caricamento dell'estensione SQLAS di Analysis Services.**  
*Richieste collegate a bug segnalati dai clienti:*  
[Argomento Microsoft Connect N. 2544902](https://connect.microsoft.com/SQLServer/feedback/details/2544902/ssms-march-2016-refresh-sqlps-failed-to-load-the-sqlas-extension).

* **Correzione di bug nella finestra dell'editor SSMS per consentire l'apertura dei file SQL mediante trascinamento della selezione.**  
*Richieste collegate a bug segnalati dai clienti:*  
[Argomento Microsoft Connect N. 2690658](https://connect.microsoft.com/SQLServer/feedback/details/2690658/cannot-drag-sql-files-into-management-studios).

* **Correzione di bug nel profiler per correggere l'arresto anomalo di quest'ultimo al momento dell'uscita.**  
*Richieste collegate a bug segnalati dai clienti:*  
[Argomento Microsoft Connect N. 2616550](https://connect.microsoft.com/SQLServer/feedback/details/2616550/sql-server-2016-rc2-profiler-version-13-0-1300-275-wont-close-after-trace-is-started-even-after-trace-is-stopped).  
[Argomento Microsoft Connect N. 2319968](https://connect.microsoft.com/SQLServer/Feedback/Details/2319968).

* **Correzione di bug in SSMS per evitare l'arresto anomalo del sistema quando si modifica un collegamento di join in Progettazione tabelle di SSMS.**  
*Richieste collegate a bug segnalati dai clienti:*  
[Argomento Microsoft Connect N. 2721052](https://connect.microsoft.com/SQLServer/feedback/details/2721052/ssms-view-design-mode-right-click-on-join-crashes-ssms).

* **Correzione di bug in SSMS per abilitare la generazione di script di database per i membri del ruolo db_owner.**  
*Richieste collegate a bug segnalati dai clienti:*  
[Argomento Microsoft Connect N. 2869241](https://connect.microsoft.com/SQLServer/feedback/details/2869241/error-with-script-database-as-create-to-in-ssms-2008r2-and-ssms-2016-june).

* **Correzione di bug nell'editor di SSMS per rimuovere il ritardo nella chiusura di una scheda di query nel caso in cui il server sia offline.**  
*Richieste collegate a bug segnalati dai clienti:*  
[Argomento Microsoft Connect N. 2656058](https://connect.microsoft.com/SQLServer/feedback/details/2656058/ssms-2014-2016-query-tab-takes-significantly-longer-to-close-if-the-instance-it-was-connected-to-is-now-offline).

* **Correzione di bug per abilitare l'opzione di backup nei database di SQL Server Express.**  
*Richieste collegate a bug segnalati dai clienti:*  
[Argomento Microsoft Connect N. 2801910](https://connect.microsoft.com/SQLServer/feedback/details/2801910/ssms-2016-backup-option-not-appearing-in-tasks).  
[Argomento Microsoft Connect N. 2874434](https://connect.microsoft.com/SQLServer/feedback/details/2874434/backup-missing-from-tasks-context-menu-in-ssms-2016-when-you-are-connected-to-an-express-instance).

* **Correzione di bug in Analysis Services per visualizzare correttamente il provider di feed di dati per modelli Analysis Services multidimensionali.**

----
## <a name="ssms-june-2016-generally-available-release"></a>Versione di SSMS disponibile a livello generale di giugno 2016
Disponibile a livello generale | Numero di versione: 13.0.15000.23

* **SSMS è disponibile a livello generale a partire dalla versione di giugno 2016.**

* **Nuova finestra di dialogo di ricerca veloce in SSMS meglio integrata nel documento corrente che consente la ricerca tramite espressioni regolari.**  
*Richieste collegate a bug segnalati dai clienti:*  
<https://connect.microsoft.com/SQLServer/feedback/details/2735513/quick-find-replace-in-ssms-2016-rc3/>

* **Miglioramenti apportati al programma di installazione di SSMS per consentire di tenere traccia dello stato dell'installazione ed eseguire codici di uscita per installazioni automatiche tramite script.**

* **Correzione del bug nella Guida sensibile al contesto di SSMS F1 per visualizzare correttamente i documenti e gli articoli della Guida.**

* **Correzione del bug nella vista Query regredite di Archivio dati query che provocava l'arresto anomalo di SSMS durante lo scorrimento.** 

* **Correzione del bug nel connettore OLEDB di Analysis Services per Excel per consentire le connessioni da Excel 2016 a SQL Server Analysis Services.**

* **Correzione di bug nella finestra di dialogo Connessione di SSMS per visualizzare la finestra di dialogo di connessione sullo stesso monitor della finestra principale di SSMS in sistemi con più monitor.**  
*Richieste collegate a bug segnalati dai clienti:*  
<https://connect.microsoft.com/SQLServer/feedback/details/724909/connection-dialog-appears-off-screen/>
<https://connect.microsoft.com/SQLServer/feedback/details/755689/sql-server-management-studio-connect-to-server-popup-dialog/>  
<https://connect.microsoft.com/SQLServer/feedback/details/389165/sql-server-management-studio-gets-confused-dealing-with-multiple-displays/>

* **Correzioni di bug nella Crittografia sempre attiva. Bug corretto dove l'opzione di menu Crittografia sempre attiva non risultava abilitata correttamente per l'estensione database. Bug corretto anche nella procedura guidata Crittografia sempre attiva dove non veniva eseguita correttamente tramite il provider HSM SafeNet (Luna SA).**

---
## <a name="ssms-april-2016-preview"></a>Anteprima di SSMS di aprile 2016 
Numero di versione: 13.0.14000.36
  
* **Miglioramento apportato al programma di installazione di SSMS per aggiungere messaggi di errore leggibili.**  
  
* **Miglioramento apportato alla procedura guidata Estensione database per aggiungere il supporto per i predicati**.  
  
* **Miglioramento apportato al cmdlet AlwaysEncrypted di PowerShell per aggiungere le API di crittografia chiave**.  
  
* **Correzione di bug per disattivare IntelliSense nella barra degli strumenti di SSMS se è stata disabilitata nella finestra di dialogo Strumenti, Opzioni.**  
*Richieste collegate a bug segnalati dai clienti:*  
<https://connect.microsoft.com/SQLServer/feedback/details/2555163/sql-2016-rc2-turning-off-intellisense-from-options-does-not-turn-it-off-on-toolbar/>  
    
* **Miglioramenti e correzioni di bug nell'interfaccia utente di confronto Showplan per ridurre la spaziatura usata dai piani di query prolungati**.  
  
* **Correzioni di bug in SSMS per risolvere i problemi che causano l'arresto anomalo all'uscita da SSMS**.   
  
* **Correzioni di bug della procedura guidata Crittografia sempre attiva per mantenere le autorizzazioni utente durante la crittografia e consentire le operazioni di scollegamento del database al completamento della procedura guidata**.  
  
* **Correzione di bug nella finestra di dialogo Crittografia sempre attiva, Nuova colonna, Chiave master per offrire commenti e suggerimenti nel tentativo di generare una chiave tramite un provider di algoritmo di crittografia non supportato.**  
  
---  
## <a name="ssms-march-2016-preview-refresh"></a>Aggiornamento anteprima di SSMS di marzo 2016
Numero di versione: 13.0.13000.55
  
* **SSMS usa Visual Studio 2015 Isolated Shell.**  
*Richieste collegate a bug segnalati dai clienti:*  
<https://connect.microsoft.com/SQLServer/feedback/details/2390544/update-ssms-to-use-visual-studio-2015-dependencies/>  
  
* **Nuova barra degli strumenti di avvio veloce che consente di trovare rapidamente voci di menu e opzioni. (VS 2015 Isolated Shell)**  
  
* **Miglioramenti apportati alle opzioni del tema di SSMS per aggiungere supporto per un tema chiaro di SSMS. (VS 2015 Isolated Shell)**  
  
* **Correzione di bug dell'opzione di menu Strumenti di SSMS per reimpostare correttamente i collegamenti di query se viene premuto il pulsante "Ripristina predefiniti".**  
  
* **Correzione di bug nei nuovi modelli di progetto di SSMS per visualizzare i nomi di modello facilmente leggibili.**  
  
* **Errore risolto con la visualizzazione della cronologia dei processi di SQL Agent in SSMS.**  
*Richieste collegate a bug segnalati dai clienti:*  
<https://connect.microsoft.com/SQLServer/feedback/details/2458860/error-viewing-job-history-microsoft-datawarehouse-sqm/>  
    
* **Correzione di bug per consentire l'installazione offline di SSMS. Ciò consente di eseguire l'installazione senza la necessità di una connessione Internet. (VS 2015 Isolated Shell)**  
*Richieste collegate a bug segnalati dai clienti:*  
<https://connect.microsoft.com/SQLServer/feedback/details/2497178/cannot-install-ssms-when-server-has-no-internet-access/>  
    
* **Correzione di bug per mantenere la directory corrente dell'utente quando viene importato il modulo SQL Server PowerShell (SQLPS).**  
*Richieste collegate a bug segnalati dai clienti:*  
<https://connect.microsoft.com/SQLServer/feedback/details/2434605/loading-sqlps-module-changes-current-directory-to-ps-sqlserver/>  
    
* **Correzione di bug nel modulo SQL Server PowerShell (SQLPS) per usare i verbi di PowerShell approvati.**  
*Richieste collegate a bug segnalati dai clienti:*  
<https://connect.microsoft.com/SQLServer/feedback/details/2432891/sqlps-module-uses-unapproved-powershell-verbs/>  
    
* **Correzione di bug nel modulo SQL Server PowerShell (SQLPS) per caricare i moduli più rapidamente.**  
*Richieste collegate a bug segnalati dai clienti:*  
<https://connect.microsoft.com/SQLServer/feedback/details/2429153/sqlps-module-is-slow-to-load/>  
    
* **Correzione di bug nei passaggi del processo di SQL Agent per consentire la modifica di un passaggio del processo.**  
*Richieste collegate a bug segnalati dai clienti:*  
<https://connect.microsoft.com/SQLServer/feedback/details/2453996/issues-with-agent-in-ssms-2016-rc0-13-0-12000-65/>  
    
* **Correzione di bug in Esplora oggetti di SSMS per elencare le tabelle in ordine alfabetico.**  
*Richieste collegate a bug segnalati dai clienti:*  
<https://connect.microsoft.com/SQLServer/feedback/details/2424718/sql-server-2016-ssms-table-list-confusing/>  
    
* **Correzione di bug nel menu a discesa "Database disponibili" per visualizzare un elenco accurato di nomi di database quando viene modificata una connessione di SQL Server.**  
*Richieste collegate a bug segnalati dai clienti:*  
<https://connect.microsoft.com/SQLServer/feedback/details/2513420/available-databases-drop-down-box-does-not-update-when-connection-changes-in-ssms/>  
    
* **Correzione di bug nei tasti di scelta rapida di SSMS per spostare lo stato attivo su "Database disponibili" se viene premuta la combinazione di tasti "CTRL+U".**  
*Richieste collegate a bug segnalati dai clienti:*  
<https://connect.microsoft.com/SQLServer/feedback/details/2534820/ssms-ctrl-u-doesnt-work/>  
  
---  
## <a name="ssms-march-2016-preview"></a>Anteprima di SSMS di marzo 2016 
Numero di versione: 13.0.12500.29 
  
* **Miglioramento apportato all'installazione guidata Web di SSMS per consentire lo spostamento mediante tasti.**  
  
* **Miglioramento apportato alla procedura guidata Crittografia sempre attiva per supportare i tipi di dati alias per la crittografia.**  
  
* **Correzione di bug nella procedura guidata "Nuovo gruppo di disponibilità" AlwaysOn per visualizzare il numero massimo corretto di destinazioni di failover automatico.**  
*Richieste collegate a bug segnalati dai clienti:* <https://connect.microsoft.com/SQLServer/feedback/details/2333670/ssms-is-showing-the-wrong-number-of-maximum-automatic-failover-targets/>  
    
* **Correzione di bug nel programma di installazione Web di SSMS per correggere gli errori di installazione.**  
*Richieste collegate a bug segnalati dai clienti:*  
<https://connect.microsoft.com/SQLServer/feedback/details/2181548/sql-server-2016-ctp-3-2-management-studio-setup/>  
    
* **Correzione di bug nella versione di anteprima di SSMS per consentire il salvataggio dei piani di manutenzione in SQL Server 2012 e versioni precedenti.**  
      
* **Correzioni di bug nella creazione guidata Backup per consentire la personalizzazione di più nomi di backup per i backup con striping e per visualizzare il nome di file di backup appropriato se viene immesso un nuovo nome dopo aver selezionato una credenziale di archiviazione.**  
  
---  
## <a name="ssms-february-2016-preview"></a>Anteprima di SSMS di febbraio 2016 
Numero di versione: 13.0.12000.65
  
* **Miglioramento apportato al monitoraggio delle attività per visualizzare le opzioni di testo quando sono abilitate le impostazioni di contrasto elevato in SSMS.**  
  
* **Miglioramento apportato alla finestra di dialogo della procedura guidata Crittografia sempre attiva per visualizzare un avviso se le regole di confronto per una colonna vengono modificate durante il processo di crittografia.**  
  
* **Miglioramento apportato alla gestione dei criteri per aggiungere il supporto per la creazione di condizioni nelle chiavi di crittografia colonna, nei valori delle chiavi di crittografia colonna e nelle chiavi master di colonna.**  
  
* **Correzione di bug per migliorare l'usabilità della finestra di dialogo di pulizia della chiave master di Crittografia sempre attiva e dei messaggi di errore di Crittografia sempre attiva.**  
  
* **Correzione di bug per disabilitare la rotazione della chiave master della colonna se esiste solo una chiave.**  
  
* **Correzione di bug per correggere l'errore relativo all'inizializzatore di tipo che si verifica se la finestra di dialogo Crittografia sempre attiva viene avviata tramite la versione di gennaio di SSMS o la versione di SSMS abbinata al supporto di SQL Server RC0.**  
  
---  
## <a name="ssms-january-2016-preview"></a>Anteprima di SSMS di gennaio 2016 
Numero di versione: 13.0.11000.78 
  
* **Correzione di bug in SSMS per consentire l'eliminazione delle sessioni Eventi estesi (XEvent).**  
  
* **Correzione di bug per aprire la finestra delle proprietà per un gruppo di disponibilità di SQL Server 2014.**  
 *Richieste collegate a bug segnalati dai clienti:*  
 <https://connect.microsoft.com/SQLServer/feedback/details/1609719/>  
     
* **Correzione di bug per consentire l'aggiunta di una replica di Azure a un gruppo di disponibilità.**  
 *Richieste collegate a bug segnalati dai clienti:*  
 <https://connect.microsoft.com/SQLServer/feedback/details/2029135/>  
     
* **Correzione di bug per aprire la finestra delle proprietà per i database di SQL Server 2014.**  
 *Richieste collegate a bug segnalati dai clienti:*  
 <https://connect.microsoft.com/SQLServer/feedback/details/2080209/>  
     
* **Correzione di bug per rimuovere le colonne duplicate che vengono visualizzate per ogni tabella quando si è connessi a un database SQL di Azure.**  
 *Richieste collegate a bug segnalati dai clienti:*  
 <https://connect.microsoft.com/SQLServer/feedback/details/2103116/>  
---  
## <a name="ssms-december-2015-preview"></a>Anteprima di SSMS di dicembre 2015 
Numero di versione: 13.0.900.73
  
* **Miglioramenti al confronto dello showplan per consentire il confronto del piano di esecuzione di query corrente con uno salvato in un file.**  
  
* **Miglioramento del supporto IntelliSense per gli indici columnstore inline di SSMS.**  
  
* **Correzione di bug nella creazione guidata della sessione di eventi estesi per consentire la selezione dei modelli quando si è connessi alla versione 12 di un server di Azure.**  
  
* **Nuove tabulazioni nelle finestre di dialogo "Crea controllo" e "Nuovo account accesso" nella cartella Sicurezza per consentire una navigazione da tastiera più semplice.**  
  
* **Correzione di bug per abilitare la funzionalità per passare alla scheda dei risultati dopo l'esecuzione di una query se SSMS è impostato per la visualizzazione dei risultati in formato griglia.**   
 *Richieste collegate a bug segnalati dai clienti:*  
  <https://connect.microsoft.com/SQLServer/feedback/details/1390296/switch-to-results-tab-after-query-execution-grid-mode-in-ssms-2016>  
  
* **Correzione di bug per visualizzare le intestazioni di colonna non troncate se SSMS è impostato per la visualizzazione dei risultati in formato griglia.**  
 *Richieste collegate a bug segnalati dai clienti:*  
  <https://connect.microsoft.com/SQLServer/feedback/details/2004111/bugbash-column-headers-in-grid-mode-truncated-with-courier-new-8>  
      
* **Correzioni di bug per consentire l'installazione del programma di installazione Web di SSMS.**  
 *Richieste collegate a bug segnalati dai clienti:*  
<https://connect.microsoft.com/SQLServer/feedback/details/2003865/ssms-october-preview-incoherent-error-message>  
<https://connect.microsoft.com/SQLServer/feedback/details/2079557/unable-to-instal-sql-server-update-13-0-800-111-over-13-0-700-242-error-code-2711>  
  
---  
## <a name="ssms-november-2015-preview"></a>Anteprima di SSMS di novembre 2015
Numero di versione: 13.0.800.111
  
* **Supporto del ridimensionamento delle bitmap per visualizzazioni a DPI elevato in SSMS.**  
  
* **Miglioramenti all'interfaccia utente delle procedure guidate e delle finestre di dialogo AlwaysEncrypted per semplificare il processo di creazione delle chiavi di crittografia del database.**  
  
* **Nuova opzione nel menu di scelta rapida visualizzato facendo clic con il pulsante destro del mouse nell'elenco "Processi" in Monitoraggio attività per visualizzare Statistiche query dinamiche.**  
  
* **Correzione di bug per consentire una corretta disinstallazione delle versioni di anteprima di SSMS nei computer client.**  
  *Richieste collegate a bug segnalati dai clienti:*  
  <https://connect.microsoft.com/SQLServer/feedback/details/1868474/ssms-2016-preview-can-be-installed-but-not-uninstalled>  
  
* **Correzione di bug per consentire la modifica dei passaggi del processo in SQL Agent anche quando manca un file**.  
  *Richieste collegate a bug segnalati dai clienti:*  
  <https://connect.microsoft.com/SQLServer/feedback/details/1769778/management-studio-2016-sql-job-agent>  
    <https://connect.microsoft.com/SQLServer/feedback/details/1502100/ssms-preview-error>  
      
* **Correzione di bug nell'opzione di menu "View Target Data" (Visualizza dati di destinazione) per una sessione di eventi estesi in un database in esecuzione in una macchina virtuale di Azure.**  
  *Richieste collegate a bug segnalati dai clienti*:  
  <https://connect.microsoft.com/SQLServer/feedback/details/1769778/management-studio-2016-sql-job-agent>  
***  

## <a name="ssms-october-2015-preview"></a>Anteprima di SSMS di ottobre 2015 
Numero di versione: 13.0.700.242  
* **Nuovo programma di installazione Web moderno e leggero che semplifica il download e il processo di installazione di SSMS.**  
  
* **Nuova procedura guidata per la Crittografia sempre attiva delle colonne che abilita la crittografia sul lato client e la decrittografia delle colonne selezionate.**  
  
* **Nuova finestra di dialogo di rotazione della chiave master di colonna per i database con Crittografia sempre attiva che semplifica il processo di rotazione delle chiavi di crittografia per proteggere i dati.**  
  
* **Nuovo monitoraggio del database di estensione che consente di risolvere i problemi ed eseguire il monitoraggio dello stato di migrazione dei dati nel cloud di Azure.**  
  
* **Miglioramenti apportati alla procedura guidata di abilitazione della funzionalità di estensione del database per consentire la selezione di un server di Microsoft Azure diverso da quello della sottoscrizione predefinita di Microsoft Azure.**  
  *Richieste collegate a bug segnalati dai clienti:*  
  <https://connect.microsoft.com/SQLServer/feedback/details/1687063/cannot-choose-from-multiple-microsoft-azure-subscriptions>  
* **Correzione di bug per consentire la visualizzazione corretta del piano di esecuzione dinamico in SSMS.**  
  *Richieste collegate a bug segnalati dai clienti:*  
<https://connect.microsoft.com/SQLServer/feedback/details/1774446/viewing-live-execution-plan-from-activity-monitor-crashes-ssms>    
* **Correzione di bug per rimuovere le opzioni non valide nello scripting di snapshot del database in SSMS.**  
  *Richieste collegate a bug segnalati dai clienti:*  
<https://connect.microsoft.com/SQLServer/feedback/details/1515168/ssms-scripting-of-database-snapshots-includes-invalid-options>  
* **Correzione di bug nell'interfaccia utente di Archivio dati query per visualizzare i dettagli nel riquadro "Prime query per consumo di risorse".**  
  *Richieste collegate a bug segnalati dai clienti:*  
<https://connect.microsoft.com/SQLServer/feedback/details/1737185/sql-server-2016-overall-resource-consumption-query-store-pane-issue>  
***  

## <a name="ssms-september-2015-preview"></a>Anteprima di SSMS di settembre 2015 
Numero di versione: 13.0.600.65  
* **Nuova finestra di dialogo Regola del firewall che semplifica il processo di connessione a un database SQL di Azure.**      
    
* **Aggiornamento della finestra di dialogo "Nuovo indice" che consente la creazione di indici non cluster rowstore anche quando è presente un indice columnstore cluster. Questa funzionalità è disponibile a partire da SQL 2016.**      
  *Richieste collegate a bug segnalati dai clienti:*    
  <https://connect.microsoft.com/SQLServer/feedback/details/1552617/creation-of-nc-index-when-clustered-columnstore-index>  
      
* **Correzione di bug per consentire la visualizzazione e la modifica dei passaggi del processo di SQL Agent nelle versioni di anteprima di SSMS in esecuzione in Windows 7.**      
  *Richieste collegate a bug segnalati dai clienti:*    
  <https://connect.microsoft.com/SQLServer/feedback/details/1548140/cannot-view-or-edit-any-sql-agent-job-step>,    
  <https://connect.microsoft.com/SQLServer/feedback/details/1626895/unable-to-load-dll-dts>,    
  <https://connect.microsoft.com/SQLServer/feedback/details/1576662/error-creating-new-job-step>     
      
* **Correzione di bug per visualizzare nodi trigger in SSMS per SQL Server 2014 e versioni successive.**      
  *Richieste collegate a bug segnalati dai clienti:*    
  <https://connect.microsoft.com/SQLServer/feedback/details/1617533/trigger-node-missing>   
      
* **Correzioni di bug nell'interfaccia utente standard della creazione report server e database per escludere le informazioni sulla versione dall'intestazione.**      
  *Richieste collegate a bug segnalati dai clienti:*    
  <https://connect.microsoft.com/SQLServer/feedback/details/1387471/report-headings-wrongly-named>  
      
* **Correzione di bug per evitare che un nodo Statistiche query dinamiche venga visualizzato come completo quando è incompleto.**      
  *Richieste collegate a bug segnalati dai clienti:*    
  <https://connect.microsoft.com/SQLServer/feedback/details/1589096/live-query-statistics-node-shows-as-completed>  
  
***      
## <a name="ssms-august-2015-preview"></a>Anteprima di SSMS di agosto 2015 
Numero di versione: 13.0.500.53
  
* **Aggiornamenti di Esplora oggetti per ridurre il ritardo del caricamento in presenza di un numero elevato di database.**  
  
* **Miglioramenti apportati all'installazione di SSMS in computer Windows 10.**  
  
* **Correzioni di bug e aggiornamenti apportati a Gestione configurazione SQL Server e all'interfaccia utente dei report utente di SSMS**    
***  
  
## <a name="ssms-july-2015-preview"></a>Anteprima di SSMS di luglio 2015
Numero di versione: 13.0.400.91
  
* **Diagrammi di database per Database SQL di Azure (V12).**  
  
* **Miglioramento del supporto di IntelliSense per la nuova sintassi della tabella temporale.**  
  
* **Aggiornamento della libreria DacFx per supportare le funzionalità più recenti dei database SQL di Azure, inclusa la sicurezza a livello di riga e l'autenticazione di Azure Active Directory.**  
  
* **Correzioni di bug: aggiornamento dell'interfaccia utente del controllo aggiornamenti, correzione dell'interfaccia utente nell'elenco "Livello di compatibilità" e altro ancora.**  
***  
  
## <a name="ssms-june-2015-preview"></a>Anteprima di SSMS di giugno 2015 
Numero di versione: 13.0.300.44
  
* **Nuovo programma di installazione leggero tramite Web di SSMS.**  
  
* **Verifica automatica degli aggiornamenti disponibili.**  
  
* **Aggiunta del supporto per la ricerca full-text per il database SQL di Azure (V12).**  
  
* **Principali richieste dei clienti soddisfatte:**  
  * Opzione 'Modifica le prime 200 righe' abilitata per tabelle e viste di Esplora oggetti.  
  * Abilitazione di Progettazione tabelle per il database SQL di Azure (V12).  
  * Abilitazione delle finestre di dialogo delle proprietà di database e tabelle per il database SQL di Azure (V12).  
    
 * **Nuova opzione per ignorare il prompt relativo al salvataggio dei file T-SQL.**  
   
 * **Supporto dell'Importazione/Esportazione guidata per nuovi livelli di servizi del database SQL di Azure (Basic, Standard, Premium).**  
   
 * **Numerose correzioni di bug: scenari di scripting, abilitazione del rilevamento delle modifiche per i database SQL e altro ancora.**   
     
  
  
  
  
  
  
    
