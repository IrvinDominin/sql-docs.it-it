---
title: MODIFICARE il catalogo full-text (Transact-SQL) | Documenti Microsoft
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database
ms.service: 
ms.component: t-sql|statements
ms.reviewer: 
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- ALTER_FULLEXT_CATALOG_TSQL
- ALTER FULLEXT CATALOG
dev_langs:
- TSQL
helpviewer_keywords:
- modifying full-text catalogs
- full-text catalogs [SQL Server], rebuilding
- accent sensitivity
- ALTER FULLTEXT CATALOG statement
- full-text catalogs [SQL Server], modifying
- full-text catalogs [SQL Server], reorganizing
ms.assetid: 31a47aaf-6c7f-48a4-a86a-d57aec66c9cb
caps.latest.revision: 
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: fa56a980fa5c5c74a1868f4c03ec791175022f76
ms.sourcegitcommit: 45e4efb7aa828578fe9eb7743a1a3526da719555
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 11/21/2017
---
# <a name="alter-fulltext-catalog-transact-sql"></a>ALTER FULLTEXT CATALOG (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

  Modifica le proprietà di un catalogo full-text.  
  
 ![Icona di collegamento a un argomento](../../database-engine/configure-windows/media/topic-link.gif "Icona di collegamento a un argomento")[Convenzioni della sintassi Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
ALTER FULLTEXT CATALOG catalog_name   
{ REBUILD [ WITH ACCENT_SENSITIVITY = { ON | OFF } ]  
| REORGANIZE  
| AS DEFAULT   
}  
```  
  
## <a name="arguments"></a>Argomenti  
 *catalog_name*  
 Specifica il nome del catalogo da modificare. Se un catalogo con il nome specificato non esiste, [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] restituisce un errore e non esegue l'operazione di modifica.  
  
 REBUILD  
 Indica a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] di ricompilare l'intero catalogo. Quando viene ricompilato un catalogo, il catalogo esistente viene eliminato e al suo posto viene creato un nuovo catalogo. Tutte le tabelle con riferimenti di indicizzazione full-text vengono associate al nuovo catalogo. La ricompilazione reimposta i metadati full-text nelle tabelle di sistema del database.  
  
 WITH ACCENT_SENSITIVITY = {ON|OFF}  
 Specifica se il catalogo da modificare supporta o meno la distinzione tra caratteri accentati e non accentati per l'esecuzione di query e l'indicizzazione full-text.  
  
 Per determinare l'impostazione della proprietà di lettura e non accentati di un catalogo full-text, utilizzare la funzione FULLTEXTCATALOGPROPERTY con il **accentsensitivity** valore di proprietà e *catalog_name*. Se la funzione restituisce '1', il catalogo full-text supporta la distinzione tra caratteri accentati e non accentati. Se la funzione restituisce '0', il catalogo non supporta la distinzione tra caratteri accentati e non accentati.  
  
 Il valore predefinito per la distinzione tra caratteri accentati e non accentati è uguale per il catalogo e il database.  
  
 REORGANIZE  
 Indica [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] per eseguire un *unione nell'indice master*, che comporta l'unione degli indici più piccoli creati durante il processo di indicizzazione in un indice di grandi dimensioni. L'unione dei frammenti di indice full-text, è possibile migliorare le prestazioni e liberare risorse di memoria e disco. Se il catalogo full-text è soggetto a modifiche frequenti, utilizzare questo comando con regolarità per riorganizzarlo.  
  
 REORGANIZE, inoltre, consente di ottimizzare le strutture interne dell'indice e del catalogo.  
  
 Tenere presente che, a seconda della quantità di dati indicizzati, un'unione nell'indice master può richiedere parecchio tempo. L'unione nell'indice master di una grande quantità di dati può comportare la creazione di una transazione con esecuzione prolungata, con il conseguente ritardo del troncamento del log delle transazioni durante il checkpoint. In questo caso, le dimensioni del log delle transazioni potrebbero aumentare notevolmente, se si utilizza il modello di recupero con registrazione completa. È consigliabile verificare che il log delle transazioni contenga spazio sufficiente per una transazione con esecuzione prolungata prima di riorganizzare un indice full-text di grandi dimensioni in un database in cui viene utilizzato il modello di recupero con registrazione completa. Per altre informazioni, vedere [Gestione delle dimensioni del file di log delle transazioni](../../relational-databases/logs/manage-the-size-of-the-transaction-log-file.md).  
  
 AS DEFAULT  
 Specifica che il catalogo è il catalogo predefinito. Quando vengono creati indici full-text senza che siano stati specificati cataloghi, viene utilizzato il catalogo predefinito. Se esiste già un catalogo full-text predefinito e si imposta AS DEFAULT per questo catalogo, il catalogo predefinito esistente verrà ignorato.  
  
## <a name="permissions"></a>Permissions  
 L'utente deve disporre dell'autorizzazione ALTER nel catalogo full-text oppure essere un membro del **db_owner**, **db_ddladmin** fissa ruoli predefiniti del database o ruolo server sysadmin.  
  
> [!NOTE]  
>  Per utilizzare ALTER FULLTEXT CATALOG AS DEFAULT, l'utente deve disporre dell'autorizzazione ALTER nel catalogo full-text e dell'autorizzazione CREATE FULLTEXT CATALOG nel database.  
  
## <a name="examples"></a>Esempi  
 Nell'esempio seguente la proprietà `accentsensitivity` del catalogo full-text predefinito viene impostata su `ftCatalog`, a indicare che il catalogo supporta la distinzione tra caratteri accentati e non accentati.  
  
```  
--Change to accent insensitive  
USE AdventureWorks2012;  
GO  
ALTER FULLTEXT CATALOG ftCatalog   
REBUILD WITH ACCENT_SENSITIVITY=OFF;  
GO  
-- Check Accentsensitivity  
SELECT FULLTEXTCATALOGPROPERTY('ftCatalog', 'accentsensitivity');  
GO  
--Returned 0, which means the catalog is not accent sensitive.  
```  
  
## <a name="see-also"></a>Vedere anche  
 [Sys. fulltext_catalogs &#40; Transact-SQL &#41;](../../relational-databases/system-catalog-views/sys-fulltext-catalogs-transact-sql.md)   
 [CREARE il catalogo full-text &#40; Transact-SQL &#41;](../../t-sql/statements/create-fulltext-catalog-transact-sql.md)   
 [ELIMINARE il catalogo full-text &#40; Transact-SQL &#41;](../../t-sql/statements/drop-fulltext-catalog-transact-sql.md)   
 [Ricerca full-text](../../relational-databases/search/full-text-search.md)  
  
  
