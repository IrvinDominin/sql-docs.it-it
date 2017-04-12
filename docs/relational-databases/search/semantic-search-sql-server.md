---
title: "Ricerca semantica (SQL Server) | Microsoft Docs"
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
  - "ricerca semantica [SQL Server]"
  - "ricerca semantica [SQL Server], panoramica"
  - "ricerca semantica statistica [SQL Server]"
  - "ricerca semantica statistica [SQL Server], panoramica"
ms.assetid: cd8faa9d-07db-420d-93f4-a2ea7c974b97
caps.latest.revision: 20
author: "douglaslMS"
ms.author: "douglasl"
manager: "jhubbard"
caps.handback.revision: 18
---
# Ricerca semantica (SQL Server)
  La ricerca semantica statistica offre una visione approfondita dei documenti non strutturati archiviati in database di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] tramite l'estrazione e l'indicizzazione di *frasi chiave* statisticamente pertinenti. Le frasi chiave vengono inoltre usate per identificare e indicizzare *documenti simili o correlati*.  
  
 Per eseguire query sugli indici semantici si usano tre funzioni di set di righe Transact-SQL per recuperare i risultati come dati strutturati.  
  
##  <a name="whatcanido"></a> Funzionalità della ricerca semantica  
 La ricerca semantica è basata sulla caratteristica di ricerca full-text esistente di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], ma consente nuovi scenari che vanno oltre le ricerche di parole chiave. Mentre la ricerca full-text consente di eseguire query sulle *parole* in un documento, la ricerca semantica consente di eseguire query sul *significato* del documento. Esempi di soluzioni ora possibili includono l'estrazione automatica dei tag, l'individuazione di contenuto correlato e la navigazione gerarchica in contenuto simile. Ad esempio, è possibile eseguire una query sull'indice di frasi chiave per compilare la tassonomia per un'organizzazione o per una raccolta di documenti. In alternativa, è possibile eseguire una query sull'indice di somiglianza dei documenti per identificare i curriculum che corrispondono a un'offerta di lavoro.  
  
 Negli esempi seguenti vengono illustrate le capacità della ricerca semantica.  
  
###  <a name="find1"></a> Trovare frasi chiave in un documento  
 Nella query seguente vengono ottenute le frasi chiave identificate nel documento di esempio. Presenta i risultati in ordine decrescente in base al punteggio di classificazione della rilevanza statistica di ogni frase chiave. Questa query chiama la funzione [semantickeyphrasetable &#40;Transact-SQL&#41;](../../relational-databases/system-functions/semantickeyphrasetable-transact-sql.md).  
  
```tsql  
SET @Title = 'Sample Document.docx'  
  
SELECT @DocID = DocumentID  
    FROM Documents  
    WHERE DocumentTitle = @Title  
  
SELECT @Title AS Title, keyphrase, score  
    FROM SEMANTICKEYPHRASETABLE(Documents, *, @DocID)  
    ORDER BY score DESC  
  
```  
  
 [Contenuto dell'argomento](#TOP)  
  
###  <a name="find2"></a> Trovare documenti simili o correlati  
 Nella query seguente vengono ottenuti i documenti identificati come simili o correlati al documento di esempio. Presenta i risultati in ordine decrescente in base al punteggio di classificazione della somiglianza dei 2 documenti. Questa query chiama la funzione [semanticsimilaritytable &#40;Transact-SQL&#41;](../../relational-databases/system-functions/semanticsimilaritytable-transact-sql.md).  
  
```vb  
SET @Title = 'Sample Document.docx'  
  
SELECT @DocID = DocumentID  
    FROM Documents  
    WHERE DocumentTitle = @Title  
  
SELECT @Title AS SourceTitle, DocumentTitle AS MatchedTitle,  
        DocumentID, score  
    FROM SEMANTICSIMILARITYTABLE(Documents, *, @DocID)  
    INNER JOIN Documents ON DocumentID = matched_document_key  
    ORDER BY score DESC  
  
```  
  
 [Contenuto dell'argomento](#TOP)  
  
###  <a name="find3"></a> Identificare le frasi chiave che indicano la somiglianza o la correlazione dei documenti  
 Nella query seguente vengono ottenute le frasi chiavi indicanti la somiglianza o la correlazione tra due documenti di esempio. Presenta i risultati in ordine decrescente in base al punteggio di classificazione del peso di ogni frase chiave. Questa query chiama la funzione [semanticsimilaritydetailstable &#40;Transact-SQL&#41;](../../relational-databases/system-functions/semanticsimilaritydetailstable-transact-sql.md).  
  
```tsql  
SET @SourceTitle = 'first.docx'  
SET @MatchedTitle = 'second.docx'  
  
SELECT @SourceDocID = DocumentID FROM Documents WHERE DocumentTitle = @SourceTitle  
SELECT @MatchedDocID = DocumentID FROM Documents WHERE DocumentTitle = @MatchedTitle  
  
SELECT @SourceTitle AS SourceTitle, @MatchedTitle AS MatchedTitle, keyphrase, score  
    FROM semanticsimilaritydetailstable(Documents, DocumentContent,  
        @SourceDocID, DocumentContent, @MatchedDocID)  
    ORDER BY score DESC  
  
```  
  
 [Contenuto dell'argomento](#TOP)  
  
##  <a name="store"></a> Archiviazione di documenti in SQL Server  
 Per poter indicizzare documenti con la ricerca semantica, è necessario archiviarli in un database di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
 La funzionalità FileTable in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] consente di inserire perfettamente file e documenti non strutturati nel database relazionale. Di conseguenza, gli sviluppatori di database possono modificare documenti insieme a dati strutturati in operazioni basate su set Transact-SQL.  
  
 Per altre informazioni sulla caratteristica FileTable, vedere [FileTables &#40;SQL Server&#41;](../../relational-databases/blob/filetables-sql-server.md). Per informazioni sulla caratteristica FILESTREAM, ovvero un'altra opzione per l'archiviazione di documenti nel database vedere [FILESTREAM &#40;SQL Server&#41;](../../relational-databases/blob/filestream-sql-server.md).  
  
 [Contenuto dell'argomento](#TOP)  
  
##  <a name="reltasks"></a> Attività correlate  
 [Installazione e configurazione della ricerca semantica](../../relational-databases/search/install-and-configure-semantic-search.md)  
 Vengono descritti i prerequisiti per la ricerca semantica statistica e viene indicato come installarli o verificarli.  
  
 [Abilitare la ricerca semantica in tabelle e colonne](../../relational-databases/search/enable-semantic-search-on-tables-and-columns.md)  
 Viene descritto come abilitare o disabilitare l'indicizzazione semantica statistica in colonne selezionate contenenti documenti o testo.  
  
 [Trovare frasi chiave nei documenti mediante ricerca semantica](../../relational-databases/search/find-key-phrases-in-documents-with-semantic-search.md)  
 Viene descritto come individuare le frasi chiave nei documenti o nelle colonne di testo configurati per l'indicizzazione semantica statistica.  
  
 [Trovare documenti simili e correlati tramite la ricerca semantica](../../relational-databases/search/find-similar-and-related-documents-with-semantic-search.md)  
 Viene descritto come reperire documenti o valori di testo simili o correlati, nonché informazioni relative alla somiglianza o correlazione, in colonne configurate per l'indicizzazione semantica statistica.  
  
 [Gestire e monitorare la ricerca semantica](../../relational-databases/search/manage-and-monitor-semantic-search.md)  
 Vengono descritti il processo di indicizzazione semantica e le attività correlate al monitoraggio e alla gestione degli indici.  
  
##  <a name="relcontent"></a> Contenuto correlato  
 [DDL di ricerca semantica, funzioni, stored procedure e viste](../../relational-databases/search/semantic-search-ddl-functions-stored-procedures-and-views.md)  
 Sono elencati le istruzioni Transact-SQL e gli oggetti di database di SQL Server aggiunti o modificati per supportare la ricerca semantica statistica.  
  
  