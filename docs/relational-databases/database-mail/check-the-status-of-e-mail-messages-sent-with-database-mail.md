---
title: "Controllare lo stato di messaggi di posta elettronica inviati con Posta elettronica database | Microsoft Docs"
ms.custom: ""
ms.date: "03/14/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "database-engine"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "posta elettronica [SQL Server], informazioni sullo stato"
  - "posta [SQL Server], informazioni sullo stato"
  - "Posta elettronica database [SQL Server], stato del messaggio"
  - "informazioni sullo stato [Posta elettronica database]"
ms.assetid: eb290f24-b52f-46bc-84eb-595afee6a5f3
caps.latest.revision: 30
author: "JennieHubbard"
ms.author: "jhubbard"
manager: "jhubbard"
caps.handback.revision: 30
---
# Controllare lo stato di messaggi di posta elettronica inviati con Posta elettronica database
  In questo argomento viene illustrato come controllare lo stato del messaggio di posta elettronica inviato utilizzando Posta elettronica database in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] tramite [!INCLUDE[tsql](../../includes/tsql-md.md)].  
  
-   **Prima di iniziare:**  
  
-   **Per visualizzare lo stato della posta elettronica inviata utilizzando Posta elettronica database, utilizzando:**  [Transact-SQL](#TsqlProcedure)  
  
##  <a name="BeforeYouBegin"></a> Prima di iniziare  
 Posta elettronica database conserva copie dei messaggi di posta elettronica in uscita e le visualizza nelle viste **sysmail_allitems**, **sysmail_sentitems**, **sysmail_unsentitems** e **sysmail_faileditems** del database **msdb**. Il programma esterno Posta elettronica database registra l'attività e visualizza il log tramite il registro eventi applicazioni di Windows e la vista **sysmail_event_log** nel database **msdb**. Per controllare lo stato di un messaggio di posta elettronica, è necessario eseguire una query su questa tabella. I messaggi di posta elettronica possono avere uno dei quattro stati seguenti: **inviato**, **non inviato**, **nuovo tentativo in corso** e **non riuscito**.  
  
##  <a name="TsqlProcedure"></a> Utilizzo di Transact-SQL  
 **Per visualizzare lo stato della posta elettronica inviata utilizzando Posta elettronica**  
  
1.  Selezionare dalla tabella **sysmail_allitems** specificando i messaggi di interesse tramite **mailitem_id** o **sent_status**.  
  
2.  Per controllare lo stato restituito dal programma esterno per i messaggi di posta elettronica, unire in join **sysmail_allitems** alla vista **sysmail_event_log** nella colonna **mailitem_id**, come illustrato nella sezione seguente.  
  
     Per impostazione predefinita, il programma esterno non registra le informazioni relative ai messaggi inviati correttamente. Per registrare tutti i messaggi, impostare il livello di registrazione su dettagliato utilizzando la pagina **Configurazione parametri di sistema** di **Configurazione guidata Posta elettronica database**.  
  
###  <a name="TsqlExample"></a> Esempio (Transact-SQL)  
 Nell'esempio seguente sono elencate le informazioni relative a eventuali messaggi di posta elettronica inviati a `danw` che il programma esterno non è stato in grado di inviare correttamente. L'istruzione elenca oggetto, data e ora del mancato invio del messaggio da parte del programma esterno e il messaggio di errore dal log di Posta elettronica database.  
  
```  
USE msdb ;  
GO  
  
-- Show the subject, the time that the mail item row was last  
-- modified, and the log information.  
-- Join sysmail_faileditems to sysmail_event_log   
-- on the mailitem_id column.  
-- In the WHERE clause list items where danw was in the recipients,  
-- copy_recipients, or blind_copy_recipients.  
-- These are the items that would have been sent  
-- to danw.  
  
SELECT items.subject,  
    items.last_mod_date  
    ,l.description FROM dbo.sysmail_faileditems as items  
INNER JOIN dbo.sysmail_event_log AS l  
    ON items.mailitem_id = l.mailitem_id  
WHERE items.recipients LIKE '%danw%'    
    OR items.copy_recipients LIKE '%danw%'   
    OR items.blind_copy_recipients LIKE '%danw%'  
GO  
```  
  
## Vedere anche  
 [Controlli e registrazione di Posta elettronica database](../../relational-databases/database-mail/database-mail-log-and-audits.md)  
  
  