---
title: "Installazione e configurazione della ricerca semantica | Microsoft Docs"
ms.custom: ""
ms.date: "03/14/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dbe-search"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "ricerca semantica [SQL Server], installazione"
  - "ricerca semantica [SQL Server], configurazione"
ms.assetid: 2cdd0568-7799-474b-82fb-65d79df3057c
caps.latest.revision: 31
author: "douglaslMS"
ms.author: "douglasl"
manager: "jhubbard"
caps.handback.revision: 28
---
# Installazione e configurazione della ricerca semantica
  Vengono descritti i prerequisiti per la ricerca semantica statistica e viene indicato come installarli o verificarli.  
  
## Installazione della ricerca semantica  
  
###  <a name="HowToCheckInstalled"></a> Procedura: Verifica dell'installazione della ricerca semantica  
 Eseguire una query sulla proprietà **IsFullTextInstalled** della funzione per i metadati [SERVERPROPERTY &#40;Transact-SQL&#41;](../../t-sql/functions/serverproperty-transact-sql.md).  
  
 Se viene restituito il valore 1, la ricerca full-text e la ricerca semantica sono installate. Se viene restituito il valore 0, le ricerche non sono installate.  
  
```tsql  
SELECT SERVERPROPERTY('IsFullTextInstalled');  
GO  
```  
  
###  <a name="BasicsSemanticSearch"></a> Procedura: Installazione della ricerca semantica  
 Per installare la ricerca semantica, selezionare **Estrazioni full-text e semantiche per la ricerca** nella pagina **Funzionalità da installare** durante l'installazione.  
  
 La ricerca semantica statistica dipende dalla ricerca full-text. Queste due funzionalità facoltative di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] vengono installate insieme.  
  
## Installazione o rimozione del database di statistiche lingua semantica  
 La ricerca semantica dispone di una dipendenza esterna aggiuntiva denominata database di statistiche lingua semantica. Questo database contiene i modelli di lingua statistici richiesti dalla ricerca semantica. Un singolo database di statistiche lingua semantica contiene i modelli di lingua per tutte le lingue supportate per l'indicizzazione semantica.  
  
###  <a name="HowToCheckDatabase"></a> Procedura: Verifica dell'installazione del database di statistiche lingua semantica  
 Eseguire una query sulla vista del catalogo [sys.fulltext_semantic_language_statistics_database &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-fulltext-semantic-language-statistics-database-transact-sql.md).  
  
 Se il database di statistiche lingua semantica è installato e registrato per l'istanza, i risultati della query conterranno una sola riga di informazioni sul database.  
  
```tsql  
SELECT * FROM sys.fulltext_semantic_language_statistics_database;  
GO  
```  
  
###  <a name="HowToInstallModel"></a> Procedura: Installazione, collegamento e registrazione del database di statistiche lingua semantica  
 Il database di statistiche lingua semantica non viene installato dal programma di installazione di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] . Per configurare il database di statistiche lingua semantica come prerequisito per l'indicizzazione semantica, effettuare le operazioni seguenti:  
  
 **1. Installare il database di statistiche lingua semantica.**  
 1.  Individuare il database di statistiche lingua semantica sui supporti di installazione di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] o scaricarlo dal Web.  
  
    -   Individuare il pacchetto di Windows Installer denominato **SemanticLanguageDatabase.msi** sui supporti di installazione di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .  
  
    -   Scaricare il pacchetto di installazione dalla pagina [Microsoft® SQL Server® 2014 Semantic Language Statistics](http://go.microsoft.com/fwlink/?LinkID=296743) nell'Area download [!INCLUDE[msCoName](../../includes/msconame-md.md)] .  
  
2.  Eseguire il pacchetto di Windows Installer **SemanticLanguageDatabase.msi** per estrarre il database e il file di log.  
  
     Se lo si desidera, è possibile modificare la directory di destinazione. Per impostazione predefinita, il programma di installazione estrae i file in una cartella denominata **Microsoft Semantic Language Database** nella cartella Programmi. Il file MSI contiene un file di database compresso e un file di log.  
  
3.  Spostare il file di database estratto e il file di log in un percorso appropriato nel file system.  
  
     Se i file vengono lasciati nel percorso predefinito, non sarà possibile estrarre un'altra copia del database per un'altra istanza di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
> [!IMPORTANT]  
>  Quando viene estratto il database di statistiche lingua semantica, al file di database e al file di log nel percorso predefinito del file system vengono assegnate autorizzazioni limitate. Si potrebbe pertanto non disporre dell'autorizzazione per collegare il database se lo si lascia nel percorso predefinito. Se viene generato un errore quando si tenta di collegare il database, spostare i file o verificare e correggere le autorizzazioni del file system nel modo appropriato.  
  
 **2. Collegare il database di statistiche lingua semantica.**  
 Collegare il database all'istanza di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] usando [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)] o chiamando [CREATE DATABASE &#40;SQL Server Transact-SQL&#41;](../../t-sql/statements/create-database-sql-server-transact-sql.md) con la sintassi **FOR ATTACH**. Per altre informazioni, vedere [Collegamento e scollegamento di un database &#40;SQL Server&#41;](../../relational-databases/databases/database-detach-and-attach-sql-server.md).  
  
 Per impostazione predefinita, il nome del database è **semanticsdb**. Facoltativamente è possibile fornire un nome diverso per il database al momento del collegamento. Tale nome dovrà essere fornito al momento di registrare il database nel passaggio successivo.  
  
```tsql  
CREATE DATABASE semanticsdb  
            ON ( FILENAME = 'C:\Microsoft Semantic Language Database\semanticsdb.mdf' )  
            LOG ON ( FILENAME = 'C:\Microsoft Semantic Language Database\semanticsdb_log.ldf' )  
            FOR ATTACH;  
GO  
```  
  
 In questo esempio di codice si presuppone che il database sia stato spostato dal percorso predefinito in un nuovo percorso.  
  
 **3. Registrare il database di statistiche lingua semantica.**  
 Chiamare la stored procedure [sp_fulltext_semantic_register_language_statistics_db &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-fulltext-semantic-register-language-statistics-db-transact-sql.md) e specificare il nome assegnato al database al momento del collegamento.  
  
```tsql  
EXEC sp_fulltext_semantic_register_language_statistics_db @dbname = N'semanticsdb';  
GO  
```  
  
###  <a name="HowToUnregister"></a> Procedura: Scollegamento e rimozione del database di statistiche lingua semantica annullandone la registrazione  
 **Annullare la registrazione del database di statistiche lingua semantica.**  
 Chiamare la stored procedure [sp_fulltext_semantic_unregister_language_statistics_db &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-fulltext-semantic-unregister-language-statistics-db-transact-sql.md). Poiché un'istanza può includere un solo database di statistiche lingua semantica, non è necessario fornire il nome del database.  
  
```tsql  
EXEC sp_fulltext_semantic_unregister_language_statistics_db;  
GO  
```  
  
 **Scollegare il database di statistiche lingua semantica.**  
 Chiamare la stored procedure [sp_detach_db &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-detach-db-transact-sql.md) e indicare il nome del database.  
  
```tsql  
USE master;  
GO  
  
EXEC sp_detach_db @dbname = N'semanticsdb';  
GO  
```  
  
 **Rimuovere il database di statistiche lingua semantica.**  
 Dopo avere annullato la registrazione del database e averlo scollegato, è possibile eliminare semplicemente il file di database. Non è disponibile alcun programma di disinstallazione e non è presente alcuna voce in **Programmi e funzionalità** nel Pannello di controllo.  
  
###  <a name="reqinstall"></a> Requisiti e restrizioni per l'installazione e la rimozione del database di statistiche lingua semantica  
  
-   È possibile collegare e registrare un solo database di statistiche lingua semantica in un'istanza di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
     Ogni istanza di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] in un solo computer richiede una copia fisica separata del database di statistiche lingua semantica. Allegare una copia a ciascuna istanza.  
  
-   Non è possibile scollegare un database di statistiche lingua semantica valido e registrato e sostituirlo con un database arbitrario che abbia lo stesso nome. In questo caso, i popolamenti dell'indice attivi o successivi non riusciranno.  
  
-   Il database di statistiche lingua semantica è di sola lettura. Non è possibile personalizzare questo database. Se si modifica il contenuto del database in qualsiasi modo, i risultati per le successive indicizzazioni semantiche saranno non deterministici. Per ripristinare lo stato originale di questi dati, è possibile eliminare il database modificato e scaricare e collegare una nuova copia non modificata del database.  
  
-   È possibile scollegare o eliminare il database di statistiche lingua semantica. Se ad alcune operazioni di indicizzazione attive sono applicati blocchi in lettura per il database, lo scollegamento o l'eliminazione non riuscirà o si verificherà un timeout. Questo aspetto è coerente con il comportamento esistente. In seguito alla rimozione del database, qualsiasi operazione di indicizzazione semantica non riuscirà.  
  
## Installazione del supporto facoltativo per i tipi di documento più nuovi  
  
###  <a name="office"></a> Procedura: Installazione dei filtri più recenti per tipi di documento di Microsoft Office e altri documenti Microsoft  
 In questa versione di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] vengono installati i word breaker e gli stemmer [!INCLUDE[msCoName](../../includes/msconame-md.md)] più recenti, ma non vengono installati i filtri più recenti per i documenti di [!INCLUDE[msCoName](../../includes/msconame-md.md)] Office e altri tipi di documento [!INCLUDE[msCoName](../../includes/msconame-md.md)] . Questi filtri sono necessari per l'indicizzazione di documenti creati con le versioni recenti di [!INCLUDE[msCoName](../../includes/msconame-md.md)] Office e di altre applicazioni [!INCLUDE[msCoName](../../includes/msconame-md.md)] . Per scaricare i filtri più recenti, vedere [Microsoft Office 2010 Filter Pack](http://go.microsoft.com/fwlink/?LinkId=218293).  
  
  