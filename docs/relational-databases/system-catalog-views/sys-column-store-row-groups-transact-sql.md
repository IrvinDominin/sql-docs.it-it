---
title: column_store_row_groups (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 06/10/2016
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sys.column_store_row_groups_TSQL
- column_store_row_groups
- sys.column_store_row_groups
- column_store_row_groups_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sys.column_store_row_groups catalog view
ms.assetid: 76e7fef2-d1a4-4272-a2bb-5f5dcd84aedc
author: CarlRabeler
ms.author: carlrab
manager: craigg
ms.openlocfilehash: bff4582f8bf46d094db2a1689ad8c9fd6de92185
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/01/2018
ms.locfileid: "47782899"
---
# <a name="syscolumnstorerowgroups-transact-sql"></a>sys.column_store_row_groups (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2014-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2014-xxxx-xxxx-xxx-md.md)]

  Fornisce informazioni sull'indice columnstore cluster in base a ogni segmento che aiutano l'amministratore a prendere decisioni in termini di gestione del sistema. **column_store_row_groups** dispone di una colonna per il numero totale di righe archiviate fisicamente (incluse quelle contrassegnate come eliminate) e una colonna per il numero di righe contrassegnate come eliminate. Uso **column_store_row_groups** per determinare quale riga gruppi hanno un'elevata percentuale di righe eliminate e deve essere ricompilati.  
   
|Nome colonna|Tipo di dati|Description|  
|-----------------|---------------|-----------------|  
|**object_id**|**int**|ID della tabella in cui è definito l'indice.|  
|**index_id**|**int**|ID dell'indice per la tabella che contiene questo indice columnstore.|  
|**partition_number**|**int**|ID della partizione della tabella che contiene il row_group_id del gruppo di righe. È possibile utilizzare il partition_number per creare un join di questa DMV a sys.partitions.|  
|**row_group_id**|**int**|Numero del gruppo di righe associato a questo gruppo di righe. Univoco all'interno della partizione.<br /><br /> -1 = della parte finale di una tabella in memoria.|  
|**delta_store_hobt_id**|**bigint**|Hobt_id per gruppo di righe aperto nell'archivio differenziale.<br /><br /> NULL se il gruppo di righe non è presente nell'archivio differenziale.<br /><br /> NULL per la parte finale di una tabella in memoria.|  
|**state**|**tinyint**|Numero ID associato a state_description.<br /><br /> 0 = INVISIBLE<br /><br /> 1 = OPEN<br /><br /> 2 = CLOSED<br /><br /> 3 = COMPRESSED <br /><br /> 4 = PER LA RIMOZIONE DEFINITIVA|  
|**a state_description**|**nvarchar(60)**|Descrizione dello stato persistente del gruppo di righe:<br /><br /> INVISIBLE: segmento compresso nascosto in corso di compilazione da dati in un archivio delta. Nelle azioni di lettura verrà utilizzato l'archivio delta fino al completamento del segmento compresso invisibile. Successivamente, il nuovo segmento diventa visibile e l'archivio delta di origine viene rimosso.<br /><br /> OPEN: un gruppo di righe di lettura/scrittura che accetta nuovi record. Un gruppo di righe aperto presenta ancora il formato rowstore e non è stato compresso nel formato columnstore.<br /><br /> CLOSED: un gruppo di righe riempito, ma non ancora compresso dal processo tuple-mover.<br /><br /> COMPRESSED: un gruppo di righe riempito e compresso.|  
|**total_rows**|**bigint**|Righe totali archiviate fisicamente nel gruppo di righe. È possibile che alcune siano state eliminate, ma risultano comunque archiviate. Il numero massimo di righe in un gruppo di righe è 1.048.576 (esadecimale FFFFF).|  
|**deleted_rows**|**bigint**|Righe totali nel gruppo di righe contrassegnate come eliminate. Sempre 0 per i gruppi di righe DELTA.|  
|**size_in_bytes**|**bigint**|Dimensioni in byte di tutti i dati nel gruppo di righe, esclusi i metadati o i dizionari condivisi, per i gruppi di righe DELTA e COLUMNSTORE.|  
  
## <a name="remarks"></a>Note  
 Restituisce una riga per ogni gruppo di righe columnstore per ogni tabella che dispone di un indice columnstore cluster o non cluster.  
  
 Uso **column_store_row_groups** per determinare il numero di righe incluse nel gruppo di righe e le dimensioni del gruppo di righe.  
  
 Quando il numero delle righe eliminate in un gruppo di righe diventa una percentuale elevata delle righe totali, la tabella diventa meno efficiente. Ricompilare l'indice columnstore per ridurre le dimensioni della tabella, riducendo le operazioni di I/O del disco necessarie per leggere la tabella. Per ricompilare l'indice columnstore, utilizzare il **REBUILD** opzione delle **ALTER INDEX** istruzione.  
  
 L'indice columnstore aggiornabile inserisce prima nuovi dati in un' **aperto** rowgroup, ovvero in formato rowstore e talvolta anche detta tabella delta.  Quando un rowgroup aperto è pieno, il relativo stato cambia da **CLOSED**. Un gruppo di righe chiuso viene compresso nel formato columnstore per il processo tuple-mover e lo stato diventa **COMPRESSED**.  Il processo tuple-mover è un processo in background che si riattiva periodicamente per verificare se esistano gruppi di righe chiusi pronti per essere compressi in un gruppo di righe columnstore.  Il processo tuple-mover dealloca i gruppi di righe in cui sono state eliminate tutte le righe. Gruppi di righe deallocati vengono contrassegnati come **per la rimozione definitiva**. Per eseguire immediatamente processo tuple-mover, utilizzare il **RIORGANIZZA** opzione delle **ALTER INDEX** istruzione.  
  
 Quando un gruppo di righe columnstore risulta riempito, viene compresso e non accetta più nuove righe. Quando vengono eliminate righe da un gruppo compresso, vengono contrassegnate come eliminate, ma risultano ancora presenti. Gli aggiornamenti a un gruppo compresso vengono implementati come un'eliminazione dal gruppo compresso e come un inserimento in un gruppo aperto.  
  
## <a name="permissions"></a>Permissions  
 Restituisce informazioni per una tabella se l'utente dispone **VIEW DEFINITION** autorizzazione per la tabella.  
  
 [!INCLUDE[ssCatViewPerm](../../includes/sscatviewperm-md.md)] Per altre informazioni, vedere [Metadata Visibility Configuration](../../relational-databases/security/metadata-visibility-configuration.md).  
  
## <a name="examples"></a>Esempi  
 L'esempio seguente unisce il **column_store_row_groups** tabella alle altre tabelle di sistema per restituire informazioni su tabelle specifiche. La colonna `PercentFull` calcolata è una stima dell'efficienza del gruppo di righe. Per trovare informazioni su una singola tabella, rimuovere il commento trattini davanti il **in cui** clausola e fornire un nome di tabella.  
  
```  
SELECT i.object_id, object_name(i.object_id) AS TableName,   
i.name AS IndexName, i.index_id, i.type_desc,   
CSRowGroups.*,   
100*(total_rows - ISNULL(deleted_rows,0))/total_rows AS PercentFull    
FROM sys.indexes AS i  
JOIN sys.column_store_row_groups AS CSRowGroups  
    ON i.object_id = CSRowGroups.object_id  
AND i.index_id = CSRowGroups.index_id   
--WHERE object_name(i.object_id) = '<table_name>'   
ORDER BY object_name(i.object_id), i.name, row_group_id;  
```  
  
## <a name="see-also"></a>Vedere anche  
 [Viste del catalogo dell'oggetto &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/object-catalog-views-transact-sql.md)   
 [Viste del catalogo &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/catalog-views-transact-sql.md)   
 [L'esecuzione di query nel catalogo di sistema SQL Server domande frequenti](../../relational-databases/system-catalog-views/querying-the-sql-server-system-catalog-faq.md)   
 [sys.columns &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-columns-transact-sql.md)   
 [sys.all_columns &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-all-columns-transact-sql.md)   
 [sys.computed_columns &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-computed-columns-transact-sql.md)   
 [Guida agli indici columnstore](~/relational-databases/indexes/columnstore-indexes-overview.md)     
 [sys.column_store_dictionaries &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-column-store-dictionaries-transact-sql.md)   
 [sys.column_store_segments &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-column-store-segments-transact-sql.md)  
  
  

