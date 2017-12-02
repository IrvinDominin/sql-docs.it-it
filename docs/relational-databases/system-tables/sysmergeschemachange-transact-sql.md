---
title: sysmergeschemachange (Transact-SQL) | Documenti Microsoft
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: system-tables
ms.reviewer: 
ms.suite: sql
ms.technology: replication
ms.tgt_pltfrm: 
ms.topic: language-reference
applies_to: SQL Server
f1_keywords:
- sysmergeschemachange_TSQL
- sysmergeschemachange
dev_langs: TSQL
helpviewer_keywords: sysmergeschemachange system table
ms.assetid: ae9ce16e-6ee9-4c7c-8210-a9bf2c7efdf0
caps.latest.revision: "26"
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: f42fbeba8639216d5a95414430099fbd5bde0b07
ms.sourcegitcommit: 45e4efb7aa828578fe9eb7743a1a3526da719555
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/21/2017
---
# <a name="sysmergeschemachange-transact-sql"></a>sysmergeschemachange (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Contiene informazioni sugli articoli pubblicati generati dall'agente snapshot. Questa tabella è archiviata nei database di pubblicazione e di sottoscrizione.  
  
|Nome colonna|Tipo di dati|Description|  
|-----------------|---------------|-----------------|  
|**pubid**|**uniqueidentifier**|ID della pubblicazione.|  
|**artid**|**uniqueidentifier**|ID dell'articolo.|  
|**attributo SchemaVersion**|**int**|Numero dell'ultima modifica dello schema.|  
|**SchemaGuid**|**uniqueidentifier**|ID univoco dell'ultimo schema.|  
|**SchemaType**|**int**|Tipo di modifica dello schema:<br /><br /> **-1** = non valido.<br /><br /> **1** = comando SQL.<br /><br /> **2** = script dello schema.<br /><br /> **3** = utilità native programma di copia bulk (BCP).<br /><br /> **4** = bcp in modalità carattere.<br /><br /> **5** = ultima generazione registrata.<br /><br /> **6** = ultima generazione inviata.<br /><br /> **7** = directory.<br /><br /> **8** = priorità.<br /><br /> **9** = periodo di memorizzazione.<br /><br /> **10** = script di trigger.<br /><br /> **11** = Alter table.<br /><br /> **12** = reinizializza tutto.<br /><br /> **13** = Modifica tabella (non -[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]).<br /><br /> **14** = reinizializza con caricamento.<br /><br /> **15** = script di indice e vincolo.<br /><br /> **16** = pulizia dei metadati.<br /><br /> **17** = Aggiorna ultima generazione inviata.<br /><br /> **18** = livello di compatibilità con le versioni precedenti.<br /><br /> **19** = convalida informazioni sul sottoscrittore.<br /><br /> **20** = con partizionamento efficiente.<br /><br /> **21** = sistema di risoluzione personalizzato.<br /><br /> **22** = ordine di elaborazione degli articoli.<br /><br /> **23** = pubblicata in una pubblicazione transazionale.<br /><br /> **24** = compensa per gli errori.<br /><br /> **25** = cartella snapshot alternativa.<br /><br /> **26** = solo download.<br /><br /> **27** = rilevamento delle eliminazioni.<br /><br /> **40** = script pre-snapshot.<br /><br /> **45** = script post-snapshot.<br /><br /> **46** = script utente su richiesta.<br /><br /> **50** = intestazione dello snapshot iniziare.<br /><br /> **51** = fine dell'intestazione dello snapshot.<br /><br /> **52** = trailer dello snapshot.<br /><br /> **53** = indirizzo FTP file Transfer Protocol ().<br /><br /> **54** = porta FTP.<br /><br /> **55** = sottodirectory FTP.<br /><br /> **56** = snapshot compresso.<br /><br /> **57** = account di accesso FTP.<br /><br /> **58** = password FTP.<br /><br /> **60** = script di creazione preliminare al sistema.<br /><br /> **61** = schema di Stored procedure.<br /><br /> **62** = schema della vista.<br /><br /> **63** = schema di funzione definita dall'utente.<br /><br /> **64** = indici di vista.<br /><br /> **65** = proprietà estese.<br /><br /> **66** = convalida.<br /><br /> **67** = comando SQL pre-snapshot.<br /><br /> **71** = convalida di snapshot dinamico.<br /><br /> **80** sistema = BCP 9.0 in modalità nativa di tabella.<br /><br /> **81** = BCP 9.0 in formato carattere per tabelle di sistema.<br /><br /> **82** = sistema tabella native BCP 9.0 (solo globale).<br /><br /> **83** = BCP 9.0 (solo globale) carattere per tabelle di sistema.<br /><br /> **84** = sistema tabella 9.0 BCP in modalità nativa (lightweight).<br /><br /> **85** = BCP 9.0 (lightweight) carattere per tabelle di sistema.<br /><br /> **128** = BCP dinamico (bit).<br /><br /> **131** = BCP nativa dinamica.<br /><br /> **132** = dinamico BCP in formato carattere.<br /><br /> **208** dinamico = BCP 9.0 in modalità nativa per tabelle di sistema.<br /><br /> **209** = BCP 9.0 in formato carattere per tabelle di sistema dinamico.<br /><br /> **210** = dinamica per tabelle di sistema nativo BCP 9.0 (solo globale).<br /><br /> **211** = carattere per tabelle di sistema dinamico BCP 9.0 (solo globale).<br /><br /> **212** = dinamica per tabelle di sistema 9.0 BCP in modalità nativa (lightweight).<br /><br /> **213** = carattere per tabelle di sistema dinamico BCP 9.0 (lightweight).<br /><br /> **300** = azioni data Definition Language (DDL).<br /><br /> **1024** = controllo dello snapshot incrementale.<br /><br /> **1049** = cartella snapshot incrementale.<br /><br /> **1074** = incrementale intestazione inizio dello snapshot.<br /><br /> **1075** = intestazione di fine dello snapshot incrementale.<br /><br /> **1076** = trailer dello snapshot incrementale.<br /><br /> **1077** = indirizzo FTP incrementale.<br /><br /> **1078** = porta FTP incrementale.<br /><br /> **1079** = sottodirectory FTP incrementale.<br /><br /> **1080** = snapshot compresso incrementale.<br /><br /> **1081** = account di accesso FTP incrementale.<br /><br /> **1082** = password FTP incrementale.|  
|**schematext**|**nvarchar(2000)**|Nome del file di script o comando che include un nome di file.|  
|**schemastatus**|**tinyint**|Specifica se è in sospeso una modifica dello schema per l'articolo. I possibili valori sono i seguenti:<br /><br /> **0** = inattivo.<br /><br /> **1** = attivo.<br /><br /> Quando una modifica dello schema in sospeso, questo valore è impostato su **1**.|  
|**schemasubtype**|**int**|Sottotipo di modifica dello schema:<br /><br /> **1** = ADDCOLUMN<br /><br /> **2** = DROPCOLUMN<br /><br /> **3** = ALTERCOLUMN<br /><br /> **4** = ADDPRIMARYKEY<br /><br /> **5** = ADDUNIQUE<br /><br /> **6** = ADDREFERENCE<br /><br /> **7** = DROPCONSTRAINT<br /><br /> **8** = ADDDEFAULT<br /><br /> **9** = ADDCHECK<br /><br /> **10** = DISABLETRIGGER<br /><br /> **11** = ENABLETRIGGER<br /><br /> **12** = DISABLETRIGGER<br /><br /> **13** = ENABLETRIGGER<br /><br /> **14** = ENABLECONSTRAINT<br /><br /> **15** = DISABLECONSTRAINT<br /><br /> **16** = ENABLECONSTRAINT<br /><br /> **17** = DISABLECONSTRAINT|  
  
## <a name="see-also"></a>Vedere anche  
 [Tabelle di replica &#40; Transact-SQL &#41;](../../relational-databases/system-tables/replication-tables-transact-sql.md)   
 [Viste della replica &#40;Transact-SQL&#41;](../../relational-databases/system-views/replication-views-transact-sql.md)  
  
  