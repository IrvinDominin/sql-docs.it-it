---
title: EVENTDATA (Transact-SQL) | Documenti Microsoft
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database
ms.service: 
ms.component: t-sql|functions
ms.reviewer: 
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- EVENTDATA
- fn_event_data
- EVENTDATA_TSQL
- fn_event_data_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- server instance event data [SQL Server]
- event notifications [SQL Server], event status
- events [SQL Server], status infromation
- EVENTDATA function
- status information [SQL Server], events
- DDL triggers, returning event data
ms.assetid: 03a80e63-6f37-4b49-bf13-dc35cfe46c44
caps.latest.revision: 
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: On Demand
ms.openlocfilehash: 45f9d434e5833180320dcb3184fdcceec56c715c
ms.sourcegitcommit: 45e4efb7aa828578fe9eb7743a1a3526da719555
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 11/21/2017
---
# <a name="eventdata-transact-sql"></a>EVENTDATA (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

  Restituisce informazioni sugli eventi del server o del database. La funzione EVENTDATA viene chiamata quando viene generata una notifica degli eventi e i risultati vengono restituiti al servizio Service Broker specificato. È possibile utilizzare EVENTDATA anche nel corpo di un trigger DDL o LOGON.  
  
 ![Icona di collegamento a un argomento](../../database-engine/configure-windows/media/topic-link.gif "Icona di collegamento a un argomento")[Convenzioni della sintassi Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
EVENTDATA( )  
```  
  
## <a name="remarks"></a>Osservazioni  
 EVENTDATA restituisce dati solo se utilizzata direttamente in un trigger DDL o LOGON. EVENTDATA restituisce Null se viene chiamata da altre routine, anche se tali routine sono chiamate da un trigger DDL o LOGON.  
  
 I dati restituiti da EVENTDATA non sono validi dopo il commit o il rollback di una transazione che ha chiamato EVENTDATA, in modo implicito o esplicito.  
  
> [!CAUTION]  
>  EVENTDATA restituisce dati XML. Tali dati vengono inviati al client in formato Unicode, utilizzando 2 byte per ogni carattere. Gli elementi di codice Unicode seguenti possono essere rappresentati nel codice XML restituito da EVENTDATA:  
>   
>  `0x0009`  
>   
>  `0x000A`  
>   
>  `0x000D`  
>   
>  `>= 0x0020 && <= 0xD7FF`  
>   
>  `>= 0xE000 && <= 0xFFFD`  
>   
>  Alcuni caratteri che possono essere inclusi in identificatori e dati [!INCLUDE[tsql](../../includes/tsql-md.md)] non sono rappresentabili o consentiti in XML. Sui caratteri o i dati con elementi di codice non indicati nell'elenco precedente viene eseguito il mapping a un punto interrogativo (?).  
  
 Per proteggere la sicurezza degli account di accesso, quando vengono eseguite le istruzioni CREATE LOGIN o ALTER LOGIN, le password non vengono visualizzate.  
  
## <a name="schemas-returned"></a>Schemi restituiti  
 EVENTDATA restituisce un valore di tipo **xml**. Per impostazione predefinita, la definizione dello schema per tutti gli eventi è installata nella directory seguente: [!INCLUDE[ssInstallPath](../../includes/ssinstallpath-md.md)]Tools\Binn\schemas\sqlserver\2006\11\events\events.xsd.  
  
 In alternativa, lo schema di eventi è pubblicato nella [Microsoft SQL Server XML Schemas](http://go.microsoft.com/fwlink/?LinkID=31850) pagina Web.  
  
 Per estrarre lo schema di un evento specifico, cercare nello schema il tipo complesso `EVENT_INSTANCE_\<event_type>`. Ad esempio, per estrarre lo schema di un evento DROP_TABLE, cercare nello schema `EVENT_INSTANCE_DROP_TABLE`.  
  
## <a name="examples"></a>Esempi  
  
### <a name="a-querying-event-data-in-a-ddl-trigger"></a>A. Recupero tramite query dei dati di eventi in un trigger DDL  
 Nell'esempio seguente viene creato un trigger DDL per impedire la creazione di nuove tabelle nel database. L'istruzione [!INCLUDE[tsql](../../includes/tsql-md.md)] che attiva il trigger viene acquisita utilizzando XQuery sui dati XML generati da EVENTDATA. Per altre informazioni, vedere [Riferimento al linguaggio XQuery &#40;SQL Server&#41;](../../xquery/xquery-language-reference-sql-server.md).  
  
> [!NOTE]  
>  Quando esegue una query di `\<TSQLCommand>` elemento utilizzando **risultati in formato griglia** in [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], interruzioni di riga nel testo del comando non vengono visualizzati. Utilizzare **risultati in formato testo** invece.  
  
```  
USE AdventureWorks2012;  
GO  
CREATE TRIGGER safety   
ON DATABASE   
FOR CREATE_TABLE   
AS   
    PRINT 'CREATE TABLE Issued.'  
    SELECT EVENTDATA().value  
        ('(/EVENT_INSTANCE/TSQLCommand/CommandText)[1]','nvarchar(max)')  
   RAISERROR ('New tables cannot be created in this database.', 16, 1)   
   ROLLBACK  
;  
GO  
--Test the trigger.  
CREATE TABLE NewTable (Column1 int);  
GO  
--Drop the trigger.  
DROP TRIGGER safety  
ON DATABASE;  
GO  
```  
  
> [!NOTE]  
>  Quando si desidera restituire dati degli eventi, è consigliabile utilizzare l'espressione XQuery **Value ()** anziché il **query ()** metodo. Il **query ()** metodo restituisce-il carattere di escape e commerciale e XML e l'avanzamento di riga istanze (CR/LF) nell'output, mentre il **Value ()** metodo rende le istanze CR/LF invisibili nell'output.  
  
### <a name="b-creating-a-log-table-with-event-data-in-a-ddl-trigger"></a>B. Creazione di una tabella di log con dati di eventi in un trigger DDL  
 Nell'esempio seguente viene creata una tabella per l'archiviazione di informazioni su tutti gli eventi a livello di database e tale tabella viene popolata con un trigger DDL. Il tipo di evento e l'istruzione [!INCLUDE[tsql](../../includes/tsql-md.md)] vengono acquisiti utilizzando XQuery sui dati XML generati da `EVENTDATA`.  
  
```  
USE AdventureWorks2012;  
GO  
CREATE TABLE ddl_log (PostTime datetime, DB_User nvarchar(100), Event nvarchar(100), TSQL nvarchar(2000));  
GO  
CREATE TRIGGER log   
ON DATABASE   
FOR DDL_DATABASE_LEVEL_EVENTS   
AS  
DECLARE @data XML  
SET @data = EVENTDATA()  
INSERT ddl_log   
   (PostTime, DB_User, Event, TSQL)   
   VALUES   
   (GETDATE(),   
   CONVERT(nvarchar(100), CURRENT_USER),   
   @data.value('(/EVENT_INSTANCE/EventType)[1]', 'nvarchar(100)'),   
   @data.value('(/EVENT_INSTANCE/TSQLCommand)[1]', 'nvarchar(2000)') ) ;  
GO  
--Test the trigger.  
CREATE TABLE TestTable (a int);  
DROP TABLE TestTable ;  
GO  
SELECT * FROM ddl_log ;  
GO  
--Drop the trigger.  
DROP TRIGGER log  
ON DATABASE;  
GO  
--Drop table ddl_log.  
DROP TABLE ddl_log;  
GO  
```  
  
## <a name="see-also"></a>Vedere anche  
 [Utilizzare la funzione EVENTDATA](../../relational-databases/triggers/use-the-eventdata-function.md)   
 [Trigger DDL](../../relational-databases/triggers/ddl-triggers.md)   
 [Notifiche degli eventi](../../relational-databases/service-broker/event-notifications.md)   
 [Trigger LOGON](../../relational-databases/triggers/logon-triggers.md)  
  
  
