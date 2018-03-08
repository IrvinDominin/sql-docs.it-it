---
title: sp_fulltext_keymappings (Transact-SQL) | Microsoft Docs
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine, pdw
ms.service: 
ms.component: system-stored-procedures
ms.reviewer: 
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- sp_fulltext_keymappings_TSQL
- sp_fulltext_keymappings
dev_langs:
- TSQL
helpviewer_keywords:
- full-text indexes [SQL Server], key column
- sp_fulltext_keymappings
- full-text indexes [SQL Server], troubleshooting
ms.assetid: 2818fa42-072d-4664-a2f7-7ec363b51d81
caps.latest.revision: 
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 9d0a2bb541e1984e8d992ae00303d47838204ed5
ms.sourcegitcommit: c556eaf60a49af7025db35b7aa14beb76a8158c5
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/03/2018
---
# <a name="spfulltextkeymappings-transact-sql"></a>sp_fulltext_keymappings (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-pdw-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-pdw-md.md)]

  Restituisce i mapping tra gli identificatori del documento (DocIds) e i valori della chiave full-text. La colonna DocId contiene valori per un **bigint** numero intero che esegue il mapping a un determinato valore chiave full-text in una tabella con indicizzazione full-text. I valori DocId che soddisfano una condizione di ricerca vengono passati dal motore di ricerca full-text al Motore di database dove vengono sottoposti al mapping ai valori della chiave full-text della tabella di base su cui viene eseguita la query. La colonna chiave full-text rappresenta l'indice univoco necessario in una colonna della tabella.  
  
 ![Icona di collegamento a un argomento](../../database-engine/configure-windows/media/topic-link.gif "Icona di collegamento a un argomento")[Convenzioni della sintassi Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
sp_fulltext_keymappings { table_id | table_id, docid | table_id, NULL, key }  
```  
  
#### <a name="parameters"></a>Parametri  
 *table_id*  
 ID oggetto della tabella con indicizzazione full-text. Se si specifica un oggetto non valido *table_id*, viene restituito un errore. Per informazioni su come ottenere l'ID di oggetto di una tabella, vedere [OBJECT_ID &#40; Transact-SQL &#41; ](../../t-sql/functions/object-id-transact-sql.md).  
  
 *docid*  
 Identificatore interno del documento (DocID) corrispondente al valore della chiave. Se si specifica un valore *docid* non valido, non viene restituito alcun risultato.  
  
 *key*  
 Valore di chiave full-text dalla tabella specificata. Se si specifica un valore *key* non valido, non viene restituito alcun risultato. Per informazioni sui valori chiave full-text, vedere [gestire indici Full-Text](http://msdn.microsoft.com/library/28ff17dc-172b-4ac4-853f-990b5dc02fd1).  
  
> [!IMPORTANT]  
>  Per informazioni sull'utilizzo di uno, due o tre parametri, vedere la sezione "Osservazioni" più avanti in questo argomento.  
  
## <a name="return-code-values"></a>Valori restituiti  
 Nessuno  
  
## <a name="result-sets"></a>Set di risultati  
  
|Nome colonna|Tipo di dati|Description|  
|-----------------|---------------|-----------------|  
|DocId|**bigint**|Colonna dell'identificatore interno del documento (DocID) corrispondente al valore della chiave.|  
|Key|*|Valore di chiave full-text dalla tabella specificata.<br /><br /> Se nella tabella di mapping non esiste alcuna chiave full-text, viene restituito un set di righe vuoto.|  
  
 <sup>*</sup>Il tipo di dati per la chiave è corrisponde al tipo di dati della colonna chiave full-text nella tabella di base.  
  
## <a name="permissions"></a>Autorizzazioni  
 Questa funzione è pubblica e non richiede autorizzazioni speciali.  
  
## <a name="remarks"></a>Osservazioni  
 Nella tabella seguente viene descritto l'effetto ottenuto nel caso si utilizzino uno, due o tre parametri.  
  
|Elenco parametri|Risultato|  
|--------------------------|----------------------|  
|*table_id*|Quando viene richiamato solo con il *table_id* , sp_fulltext_keymappings restituisce tutti i valori chiave full-text (Key) della tabella di base specificata, nonché il valore DocId corrispondente a ogni chiave. Le chiavi in sospeso vengono eliminate.<br /><br /> Questa funzione consente di risolvere numerosi problemi ed è particolarmente utile per visualizzare il contenuto dell'indice full-text quando il tipo di dati della chiave full-text selezionata non è Integer. Ciò comporta l'aggiunta dei risultati di sp_fulltext_keymappings con i risultati di **Sys.dm fts_index_keywords_by_document**. Per ulteriori informazioni, vedere [Sys.dm fts_index_keywords_by_document &#40; Transact-SQL &#41; ](../../relational-databases/system-dynamic-management-views/sys-dm-fts-index-keywords-by-document-transact-sql.md).<br /><br /> In generale, quando possibile, è consigliabile tuttavia eseguire sp_fulltext_keymappings con parametri che indicano una chiave full-text o un valore DocId specifico Questa operazione risulta molto più efficiente rispetto alla restituzione di un'intera mappa di chiavi, soprattutto per una tabella di dimensioni elevate per cui il costo in termini di prestazioni della restituzione dell'intera mappa di chiavi potrebbe essere significativo.|  
|*table_id*, *docid*|Se solo il *table_id* e *docid* vengono specificati, *docid* deve essere diverso da null e specificare un valore DocId valido nella tabella specificata. Questa funzione è utile per isolare la chiave full-text personalizzata della tabella di base corrispondente al valore DocId di un determinato indice full-text.|  
|*table_id*, NULL, *key*|Se sono presenti tre parametri, il secondo parametro deve essere NULL, e *chiave* deve essere diverso da null e specificare un valore di chiave full-text valido dalla tabella specificata. Questa funzione è utile per isolare il valore DocId corrispondente a una chiave full-text specifica della tabella di base.|  
  
 Se si verifica una delle condizioni seguenti, viene restituito un errore:  
  
-   Specificare un oggetto non valido *table_id*.  
  
-   La tabella non è una tabella con indicizzazione full-text.  
  
-   Viene rilevato il valore NULL per un parametro che può essere diverso da NULL.  
  
## <a name="examples"></a>Esempi  
  
> [!NOTE]  
>  Gli esempi in questa sezione utilizzano il `Production.ProductReview` sommario il [!INCLUDE[ssSampleDBnormal](../../includes/sssampledbnormal-md.md)] database di esempio. È possibile creare questo indice eseguendo l'esempio fornito per il `ProductReview` tabella [CREATE FULLTEXT INDEX &#40; Transact-SQL &#41; ](../../t-sql/statements/create-fulltext-index-transact-sql.md).  
  
### <a name="a-obtaining-all-the-key-and-docid-values"></a>A. Recupero di tutti i valori Key e DocId  
 Nell'esempio seguente viene utilizzato un [DECLARE](../../t-sql/language-elements/declare-local-variable-transact-sql.md) istruzione per creare una variabile locale, `@table_id` e assegnare l'ID del `ProductReview` tabella come relativo valore. Nell'esempio viene eseguita **sp_fulltext_keymappings** specificando `@table_id` per il *table_id* parametro.  
  
> [!NOTE]  
>  Utilizzando **sp_fulltext_keymappings** solo con il *table_id* parametro è adatto per le piccole tabelle.  
  
```  
USE AdventureWorks2012;  
GO  
DECLARE @table_id int = OBJECT_ID(N'Production.ProductReview');  
EXEC sp_fulltext_keymappings @table_id;  
GO  
  
```  
  
 In questo esempio vengono restituite tutte i valori di DocId e le chiavi full-text dalla tabella come segue:  
  
||||  
|-|-|-|  
||`docid`|`key`|  
|`1`|`1`|`1`|  
|`2`|`2`|`2`|  
|`3`|`3`|`3`|  
|`4`|`4`|`4`|  
  
### <a name="b-obtaining-the-docid-value-for-a-specific-key-value"></a>B. Acquisizione del valore DocId per un valore Key specifico  
 Nell'esempio seguente viene utilizzata un'istruzione DECLARE per creare una variabile locale, `@table_id`, e assegnare l'ID della tabella `ProductReview` come valore. Nell'esempio viene eseguita **sp_fulltext_keymappings** specificando `@table_id` per il *table_id* parametro NULL per il *docid* parametro e 4 per il *chiave* parametro.  
  
> [!NOTE]  
>  Utilizzando **sp_fulltext_keymappings** solo con il *table_id* parametro adatto per le piccole tabelle.  
  
```  
USE AdventureWorks2012;  
GO  
DECLARE @table_id int = OBJECT_ID(N'Production.ProductReview');  
EXEC sp_fulltext_keymappings @table_id, NULL, 4;  
GO  
  
```  
  
 Nell'esempio vengono restituiti i risultati seguenti.  
  
||||  
|-|-|-|  
||`docid`|`key`|  
|`4`|`4`|`4`|  
  
## <a name="see-also"></a>Vedere anche  
 [Ricerca full-Text e semantica Stored procedure &#40; Transact-SQL &#41;](../../relational-databases/system-stored-procedures/full-text-search-and-semantic-search-stored-procedures-transact-sql.md)  
  
  
