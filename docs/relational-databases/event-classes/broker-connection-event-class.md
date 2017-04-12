---
title: "Classe di evento Broker:Connection | Microsoft Docs"
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
  - "Broker:Connection - classe di evento"
ms.assetid: d3e505f2-0a43-486f-aa92-9c8e49b2dfea
caps.latest.revision: 24
author: "JennieHubbard"
ms.author: "jhubbard"
manager: "jhubbard"
caps.handback.revision: 24
---
# Classe di evento Broker:Connection
  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] genera un evento **Broker:Connection** per indicare lo stato di una connessione di trasporto gestita da Service Broker.  
  
## Colonne di dati della classe di evento Broker:Connection  
  
|Colonna di dati|Tipo|Descrizione|Numero colonna|Filtrabile|  
|-----------------|----------|-----------------|-------------------|----------------|  
|**ApplicationName**|**nvarchar**|Nome dell'applicazione client in cui è stata creata la connessione a un'istanza di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Questa colonna viene popolata con i valori passati dall'applicazione e non con il nome visualizzato del programma.|10|Sì|  
|**ClientProcessID**|**int**|ID assegnato dal computer host al processo in cui è in esecuzione l'applicazione client. Questa colonna di dati viene popolata se l'ID del processo client viene fornito dal client.|9|Sì|  
|**DatabaseID**|**int**|ID del database specificato nell'istruzione USE *database* oppure ID del database predefinito, se per una determinata istanza non viene eseguita un'istruzione USE *database*. [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] visualizza il nome del database se la colonna di dati **ServerName** è acquisita nella traccia e il server è disponibile. È possibile determinare il valore per un database tramite la funzione **DB_ID**.|3|Sì|  
|**Errore**|**int**|Numero di ID del messaggio in **sys.messages** relativo al testo dell'evento. Se l'evento indica un errore, questo è il numero di errore di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].|31|No|  
|**EventClass**|**int**|Tipo di classe di evento acquisita. Per **Broker:Connection**, corrisponde sempre a **138**.|27|No|  
|**EventSequence**|**int**|Numero di sequenza dell'evento.|51|No|  
|**EventSubClass**|**nvarchar**|Stato della connessione. Per questo evento, la sottoclasse corrisponde a uno dei valori seguenti.<br /><br /> <br /><br /> **Connecting**: [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] sta iniziando una connessione di trasporto.<br /><br /> **Connected**: [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ha stabilito una connessione di trasporto.<br /><br /> **Connect Failed**: [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] non è riuscito a stabilire una connessione di trasporto.<br /><br /> **Closing**: [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] è in corso la chiusura della connessione di trasporto.<br /><br /> **Closed**: [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ha chiuso la connessione di trasporto.<br /><br /> **Accept**: [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ha accettato una connessione di trasporto da un'altra istanza.<br /><br /> **Send IO Error**: [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ha rilevato un errore di trasporto durante l'invio di un messaggio.<br /><br /> **Receive IO Error**: [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ha rilevato un errore di trasporto durante la ricezione di un messaggio.|21|Sì|  
|**GUID**|**uniqueidentifier**|ID dell'endpoint della connessione.|54|No|  
|**HostName**|**nvarchar**|Nome del computer in cui è in esecuzione il client. Questa colonna di dati viene popolata se il nome host viene fornito dal client. Per determinare il nome host, usare la funzione **HOST_NAME**.|8|Sì|  
|**IntegerData**|**int**|Numero di chiusure della connessione eseguite.|25|Sì|  
|**IsSystem**|**int**|Indica se l'evento è stato generato per un processo di sistema o un processo utente.<br /><br /> 0 = utente<br /><br /> 1 = sistema|60|No|  
|**LoginSid**|**image**|ID di sicurezza (SID) dell'utente connesso. Il SID è univoco per ogni account di accesso nel server.|41|Sì|  
|**NTDomainName**|**nvarchar**|Dominio di Windows a cui appartiene l'utente.|7|Sì|  
|**NTUserName**|**nvarchar**|Nome dell'utente proprietario della connessione che ha generato questo evento.|6|Sì|  
|**ObjectName**|**nvarchar**|Handle di conversazione del dialogo.|34|No|  
|**ServerName**|**nvarchar**|Nome dell'istanza di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] tracciata.|26|No|  
|**SPID**|**int**|ID del processo server assegnato da [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] al processo associato al client.|12|Sì|  
|**StartTime**|**datetime**|Ora di inizio dell'evento, se disponibile.|14|Sì|  
|**TextData**|**ntext**|Testo del messaggio di errore relativo all'evento. Per gli eventi che non indicano un errore, questo campo è vuoto. Può trattarsi di un messaggio di errore di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] o di Windows.|1|Sì|  
|**TransactionID**|**bigint**|ID della transazione assegnato dal sistema.|4|No|  
  
## Vedere anche  
 [SQL Server Service Broker](../../database-engine/configure-windows/sql-server-service-broker.md)  
  
  