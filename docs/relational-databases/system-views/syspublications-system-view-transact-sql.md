---
title: syspublications (vista di sistema) (Transact-SQL) | Documenti Microsoft
ms.custom: 
ms.date: 03/17/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: system-views
ms.reviewer: 
ms.suite: sql
ms.technology:
- replication
ms.tgt_pltfrm: 
ms.topic: language-reference
applies_to:
- SQL Server
f1_keywords:
- syspublications
- syspublications_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- syspublications view
ms.assetid: e5f57c32-efc0-4455-a74f-684dc2ae51f8
caps.latest.revision: 
author: stevestein
ms.author: sstein
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 6b67197861029cbd9b16e1c829e4570540ca377f
ms.sourcegitcommit: c556eaf60a49af7025db35b7aa14beb76a8158c5
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/03/2018
---
# <a name="syspublications-system-view-transact-sql"></a>syspublications (vista di sistema) (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Il **syspublications** Vista espone informazioni sulla pubblicazione. Questa vista è archiviata nel database di distribuzione.  
  
|Nome colonna|Tipo di dati|Description|  
|-----------------|---------------|-----------------|  
|**description**|**nvarchar(255)**|Voce descrittiva per la pubblicazione.|  
|**name**|**sysname**|Nome univoco associato alla pubblicazione.|  
|**pubid**|**int**|Colonna Identity che include un ID univoco per la pubblicazione.|  
|**repl_freq**|**tinyint**|Frequenza della replica:<br /><br /> **0** = basata sulle transazioni (transazionale).<br /><br /> **1** = aggiornamento di tabella pianificato (snapshot).|  
|**status**|**tinyint**|Stato della pubblicazione:<br /><br /> **0** = inattivo.<br /><br /> **1** = attivo.|  
|**sync_method**|**tinyint**|Metodo di sincronizzazione:<br /><br /> **0** = utilità per copia bulk in modalità nativa (BCP).<br /><br /> **1** = bcp in modalità carattere.<br /><br /> **3** = simultanea, il che significa che viene utilizzata la modalità BCP nativa, ma durante lo snapshot non vengono bloccate le tabelle.<br /><br /> **4** = Concurrent_c, ovvero che carattere viene utilizzata, ma le tabelle non vengono bloccate durante lo snapshot.|  
|**snapshot_jobid**|**binary(16)**|Identifica il processo di agente pianificato per la generazione dello snapshot iniziale.|  
|**independent_agent**|**bit**|Specifica se per la pubblicazione è disponibile un agente di distribuzione autonomo.<br /><br /> **0** = la pubblicazione utilizza un agente di distribuzione condiviso, e ogni coppia database del server di pubblicazione/sottoscrizione di database ha un solo agente condiviso.<br /><br /> **1** = è disponibile un agente di distribuzione autonomo per la pubblicazione.|  
|**immediate_sync**|**bit**|Indica se i file di sincronizzazione vengono creati o ricreati ogni volta che viene eseguito l'agente Snapshot, in cui **1** significa che vengono creati ogni volta che viene eseguito l'agente.|  
|**enabled_for_internet**|**bit**|Indica se i file di sincronizzazione per la pubblicazione vengono esposti a Internet tramite il protocollo file transfer protocol (FTP) e altri servizi, in cui **1** significa che è possibile accedere da Internet.|  
|**allow_push**|**bit**|Indica se le sottoscrizioni push sono consentite per la pubblicazione in cui **1** significa che sono consentiti.|  
|**allow_pull**|**bit**|Indica se le sottoscrizioni pull sono consentite per la pubblicazione in cui **1** significa che sono consentiti.|  
|**allow_anonymous**|**bit**|Indica se le sottoscrizioni anonime sono consentite per la pubblicazione in cui **1** significa che sono consentiti.|  
|**immediate_sync_ready**|**bit**|Indica se lo snapshot è stato generato dall'agente snapshot e se è pronto per l'utilizzo nelle nuove sottoscrizioni. Questo valore risulta significativo solo per le pubblicazioni ad aggiornamento immediato. **1** indica che lo snapshot è pronto.|  
|**allow_sync_tran**|**bit**|Specifica se è consentito creare sottoscrizioni ad aggiornamento immediato per la pubblicazione. **1** significa che le sottoscrizioni ad aggiornamento immediato sono consentite.|  
|**autogen_sync_procs**|**bit**|Specifica se la stored procedure di sincronizzazione per sottoscrizioni ad aggiornamento immediato viene generata nel server di pubblicazione. **1** significa che viene generato nel server di pubblicazione.|  
|**retention**|**int**|Periodo di tempo, espresso in ore, per cui le modifiche della pubblicazione vengono mantenute nel database di distribuzione.|  
|**allow_queued_tran**|**bit**|Specifica se disabilitare l'inserimento in coda delle modifiche apportate nel Sottoscrittore finché non è possibile applicarle al server di pubblicazione. Se **1**, le modifiche nel Sottoscrittore vengono accodate.|  
|**snapshot_in_defaultfolder**|**bit**|Specifica se i file di snapshot sono archiviati nella cartella predefinita. Se **0**, i file di snapshot sono stati archiviati nella posizione alternativa specificata da *alternate_snapshot_folder*. Se è 1, i file di snapshot sono disponibili nella cartella predefinita.|  
|**alt_snapshot_folder**|**nvarchar(510)**|Specifica la posizione della cartella alternativa per lo snapshot.|  
|**pre_snapshot_script**|**nvarchar(510)**|Specifica un puntatore a un **SQL** percorso del file. L'agente di distribuzione esegue lo script pre-snapshot prima dell'esecuzione degli script di oggetti replicati in fase di applicazione di uno snapshot in un Sottoscrittore.|  
|**post_snapshot_script**|**nvarchar(510)**|Specifica un puntatore a un **SQL** percorso del file. L'agente di distribuzione esegue lo script post-snapshot dopo l'applicazione di tutti gli altri script di oggetti replicati e dei dati durante una sincronizzazione iniziale.|  
|**compress_snapshot**|**bit**|Specifica che lo snapshot viene scritto il *alt_snapshot_folder* percorso è deve essere compresso nel [!INCLUDE[msCoName](../../includes/msconame-md.md)] formato CAB. **1** indica che lo snapshot verrà compresso.|  
|**ftp_address**|**sysname**|Indirizzo di rete del servizio FTP per il server di distribuzione. Specifica la posizione in cui i file di snapshot della pubblicazione possono essere prelevati dall'agente di distribuzione.|  
|**ftp_port**|**int**|Numero di porta del servizio FTP per il server di distribuzione. Specifica la posizione in cui i file di snapshot della pubblicazione possono essere prelevati dall'agente di distribuzione.|  
|**ftp_subdirectory**|**nvarchar(510)**|Specifica la posizione in cui i file di snapshot possono essere prelevati dall'agente di distribuzione se la pubblicazione supporta la propagazione degli snapshot tramite FTP.|  
|**ftp_login**|**nvarchar(256)**|Nome utente utilizzato per la connessione al servizio FTP.|  
|**ftp_password**|**nvarchar(1048)**|Password dell'utente utilizzata per la connessione al servizio FTP.|  
|**allow_dts**|**bit**|Specifica se la pubblicazione consente trasformazioni [!INCLUDE[ssVersion2000](../../includes/ssversion2000-md.md)] Data Transformation Services (DTS). **1** indica che le trasformazioni DTS sono consentite.|  
|**allow_subscription_copy**|**bit**|Specifica se la funzionalità che consente di copiare i database di sottoscrizione che sottoscrivono la pubblicazione è abilitata. **1** indica che la copia è consentita.|  
|**centralized_conflicts**|**bit**|Specifica se i record dei conflitti vengono archiviati nel server di pubblicazione:<br /><br /> **0** = i record dei conflitti vengono archiviati nel server di pubblicazione e nel Sottoscrittore che ha causato il conflitto.<br /><br /> **1** = i record dei conflitti vengono archiviati nel server di pubblicazione.|  
|**conflict_retention**|**int**|Specifica il periodo di memorizzazione dei record dei conflitti espresso in giorni.|  
|**conflict_policy**|**int**|Specifica i criteri di risoluzione dei conflitti adottati quando viene utilizzata l'opzione per Sottoscrittori ad aggiornamento in coda. I possibili valori sono i seguenti:<br /><br /> **1** = prevale il conflitto.<br /><br /> **2** = prevale il sottoscrittore il conflitto.<br /><br /> **3** = sottoscrizione viene reinizializzata.|  
|**queue_type**|**int**|Specifica il tipo di coda da utilizzare. I possibili valori sono i seguenti:<br /><br /> **1** = .msmq, che utilizza [!INCLUDE[msCoName](../../includes/msconame-md.md)] Accodamento messaggi per archiviare le transazioni.<br /><br /> **2** = SQL, che utilizza [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] per archiviare le transazioni.<br /><br /> Nota: L'utilizzo [!INCLUDE[msCoName](../../includes/msconame-md.md)] Accodamento messaggi è stato deprecato e non è più supportata.|  
|**ad_guidname**|**sysname**|Specifica se la pubblicazione è pubblicata in [!INCLUDE[msCoName](../../includes/msconame-md.md)] Active Directory. Un valore GUID valido indica che la pubblicazione è pubblicata in Active Directory e il GUID è l'objectGUID dell'oggetto pubblicazione di Active Directory corrispondente. Se è NULL, la pubblicazione non è pubblicata in Active Directory.<br /><br /> Nota: La pubblicazione in Active Directory non è più supportata.|  
|**backward_comp_level**|**int**|Livello di compatibilità del database. I possibili valori sono i seguenti:<br /><br /> **90** = [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)].<br /><br /> **100** = [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)].|  
|**allow_initialize_from_backup**|**bit**|Indica se i Sottoscrittori possono inizializzare una sottoscrizione della pubblicazione da un backup anziché da uno snapshot iniziale. **1** significa che le sottoscrizioni possono essere inizializzate da un backup, e **0** significa che è possibile. Per altre informazioni, vedere [Initialize a Transactional Subscription Without a Snapshot](../../relational-databases/replication/initialize-a-transactional-subscription-without-a-snapshot.md).|  
|**min_autonosync_lsn**|**binary(1)**|[!INCLUDE[ssInternalOnly](../../includes/ssinternalonly-md.md)]|  
|**replicate_ddl**|**int**|Indica se per la pubblicazione è supportata la replica dello schema.<br /><br /> **1** = DDL istruzioni eseguite nel server di pubblicazione vengono replicate.<br /><br /> **0** = indica che le istruzioni DDL non vengono replicate. Per altre informazioni, vedere [Apportare modifiche allo schema nei database di pubblicazione](../../relational-databases/replication/publish/make-schema-changes-on-publication-databases.md).|  
|**options**|**int**|Mappa di bit che specifica le opzioni di pubblicazione aggiuntive. I possibili valori bit per bit sono i seguenti:<br /><br /> **0x1** : abilitato per la replica peer-to-peer.<br /><br /> **0x2** -pubblicare solo le modifiche locali per la replica peer-to-peer.<br /><br /> **0x4** - enabled per non[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] i sottoscrittori.<br /><br /> **0x8** : abilitato per il rilevamento dei conflitti peer-to-peer.|  
|**originator_id**|**smallint**|Identifica ogni nodo in una topologia di replica peer-to-peer per consentire il rilevamento dei conflitti. Per altre informazioni, vedere [Conflict Detection in Peer-to-Peer Replication](../../relational-databases/replication/transactional/peer-to-peer-conflict-detection-in-peer-to-peer-replication.md).|  
  
## <a name="see-also"></a>Vedere anche  
 [Tabelle di replica &#40; Transact-SQL &#41;](../../relational-databases/system-tables/replication-tables-transact-sql.md)   
 [Stored procedure per la replica &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/replication-stored-procedures-transact-sql.md)   
 [sp_addpublication &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-addpublication-transact-sql.md)   
 [sp_changepublication &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-changepublication-transact-sql.md)   
 [sp_helppublication &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-helppublication-transact-sql.md)  
  
  
