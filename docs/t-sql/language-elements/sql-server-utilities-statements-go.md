---
title: GO (Transact-SQL) | Microsoft Docs
ms.custom: 
ms.date: 07/27/2017
ms.prod: sql-non-specified
ms.prod_service: sql-database
ms.service: 
ms.component: t-sql|language-elements
ms.reviewer: 
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
applies_to:
- SQL Server (starting with 2008)
f1_keywords:
- GO
- GO_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- batches [SQL Server], ending
- ending batches [SQL Server]
- GO command
ms.assetid: b2ca6791-3a07-4209-ba8e-2248a92dd738
caps.latest.revision: 
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: Active
ms.openlocfilehash: 63fe775455df2b9b25ec3abc8bb0208aa6b5dd0e
ms.sourcegitcommit: 9e6a029456f4a8daddb396bc45d7874a43a47b45
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 01/25/2018
---
# <a name="sql-server-utilities-statements---go"></a>ISTRUZIONI di utilità SQL Server-
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]vengono forniti comandi che non sono [!INCLUDE[tsql](../../includes/tsql-md.md)] istruzioni, ma che vengono riconosciuti dal **sqlcmd** e **osql** utilità e [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] Editor di codice. Questi comandi possono essere utilizzati per facilitare la leggibilità e l'esecuzione di batch e script.  
  
  GO indica la fine di un batch di [!INCLUDE[tsql](../../includes/tsql-md.md)] istruzioni per la [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] utilità.  
  
 ![Icona di collegamento a un argomento](../../database-engine/configure-windows/media/topic-link.gif "Icona di collegamento a un argomento")[Convenzioni della sintassi Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
GO [count]  
```  
  
## <a name="arguments"></a>Argomenti  
 *count*  
 Numero integer positivo. Il batch che precede GO verrà eseguito il numero specificato di volte.  
  
## <a name="remarks"></a>Osservazioni  
 GO non è un [!INCLUDE[tsql](../../includes/tsql-md.md)] istruzione, ma è un comando riconosciuto dal **sqlcmd** e **osql** utilità e [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] editor di codice.  
  
 Il comando GO viene interpretato dalle utilità di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] come un segnale per l'invio del batch corrente di istruzioni [!INCLUDE[tsql](../../includes/tsql-md.md)] a un'istanza di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Il batch di istruzioni corrente è composto da tutte le istruzioni immesse dopo l'ultima esecuzione del comando GO oppure dopo l'avvio della sessione ad hoc o dello script se si tratta della prima esecuzione di GO.  
  
 Non è possibile specificare un'istruzione [!INCLUDE[tsql](../../includes/tsql-md.md)] nella stessa riga di un comando GO. La riga, tuttavia, può includere commenti.  
  
 Gli utenti devono seguire le regole per i batch. Per l'esecuzione di una stored procedure dopo la prima istruzione di un batch, ad esempio, è necessario includere la parola chiave EXECUTE. L'ambito delle variabili locali definite dall'utente è limitato a un batch e non è possibile fare riferimento a tali variabili dopo l'esecuzione del comando GO.  
  
```  
USE AdventureWorks2012;  
GO  
DECLARE @MyMsg VARCHAR(50)  
SELECT @MyMsg = 'Hello, World.'  
GO -- @MyMsg is not valid after this GO ends the batch.  
  
-- Yields an error because @MyMsg not declared in this batch.  
PRINT @MyMsg  
GO  
  
SELECT @@VERSION;  
-- Yields an error: Must be EXEC sp_who if not first statement in   
-- batch.  
sp_who  
GO  
```  
  
 Le applicazioni di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] possono inviare più istruzioni [!INCLUDE[tsql](../../includes/tsql-md.md)] a un'istanza di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] affinché vengano eseguite come batch. Le istruzioni del batch vengono quindi compilate in un unico piano di esecuzione. I programmatori che eseguono istruzioni ad hoc nelle utilità di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] oppure compilano script di istruzioni [!INCLUDE[tsql](../../includes/tsql-md.md)] da eseguire tramite le utilità di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] utilizzano il comando GO per segnalare la fine di un batch.  
  
 Nelle applicazioni basate sulle API ODBC o OLE DB i tentativi di esecuzione del comando GO provocano un errore di sintassi. Le utilità di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] non inviano mai un comando GO al server.  
  
 Non usare un punto e virgola come carattere di terminazione dopo GO.  
  
## <a name="permissions"></a>Autorizzazioni  
 GO è un comando di utilità che non richiede autorizzazioni e può essere eseguito da qualsiasi utente.  
  
```  
-- Yields an error because ; is not permitted after GO  
SELECT @@VERSION;  
GO;  
```  
  
## <a name="examples"></a>Esempi  
 Nell'esempio seguente vengono creati due batch. Il primo contiene solo un `USE``AdventureWorks2012` istruzione per impostare il contesto di database. Nelle restanti istruzioni viene utilizzata una variabile locale. Pertanto, tutte le dichiarazioni della variabile locale devono essere raggruppate in un singolo batch. A tale scopo, è necessario inserire il comando `GO` solo dopo l'ultima istruzione che fa riferimento alla variabile.  
  
```  
USE AdventureWorks2012;  
GO  
DECLARE @NmbrPeople int  
SELECT @NmbrPeople = COUNT(*)  
FROM Person.Person;  
PRINT 'The number of people as of ' +  
      CAST(GETDATE() AS char(20)) + ' is ' +  
      CAST(@NmbrPeople AS char (10));  
GO  
```  
  
 Nell'esempio seguente vengono eseguite due volte le istruzioni del batch.  
  
```  
SELECT DB_NAME();  
SELECT USER_NAME();  
GO 2  
```  
  
  
