---
title: sp_fulltext_column (Transact-SQL) | Microsoft Docs
ms.custom: 
ms.date: 06/10/2016
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-data-warehouse
ms.service: 
ms.component: system-stored-procedures
ms.reviewer: 
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- sp_fulltext_column_TSQL
- sp_fulltext_column
dev_langs:
- TSQL
helpviewer_keywords:
- sp_fulltext_column
ms.assetid: a84cc45d-1b50-44af-85df-2ea033b8a6a9
caps.latest.revision: 
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: f1099b9ee7ebf38703701a2160e15d24b80ba859
ms.sourcegitcommit: c556eaf60a49af7025db35b7aa14beb76a8158c5
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/03/2018
---
# <a name="spfulltextcolumn-transact-sql"></a>sp_fulltext_column (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-asdw-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-asdw-xxx-md.md)]

  Specifica se una determinata colonna di una tabella viene inclusa o meno nell'indicizzazione full-text.  
  
> [!IMPORTANT]  
>  [!INCLUDE[ssNoteDepFutureAvoid](../../includes/ssnotedepfutureavoid-md.md)] Utilizzare [ALTER FULLTEXT INDEX](../../t-sql/statements/alter-fulltext-index-transact-sql.md) invece.  
  
 ![Icona di collegamento a un argomento](../../database-engine/configure-windows/media/topic-link.gif "Icona di collegamento a un argomento")[Convenzioni della sintassi Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
sp_fulltext_column [ @tabname= ] 'qualified_table_name' ,   
     [ @colname= ] 'column_name' ,   
     [ @action= ] 'action'   
     [ , [ @language= ] 'language_term' ]   
     [ , [ @type_colname= ] 'type_column_name' ]  
```  
  
## <a name="arguments"></a>Argomenti  
 [  **@tabname=** ] **'***qualified_table_name***'**  
 Nome della tabella composto da una o due parti. La tabella deve esistere nel database corrente La tabella deve disporre di un indice full-text. *qualified_table_name* è **nvarchar (517)**, senza alcun valore predefinito.  
  
 [  **@colname=** ] **'***column_name***'**  
 È il nome di una colonna in *qualified_table_name*. La colonna deve essere un carattere, **varbinary (max)** o **immagine** colonna e non può essere una colonna calcolata. *column_name* è **sysname**, non prevede alcun valore predefinito.  
  
> [!NOTE]  
>  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] creare indici full-text dei dati di testo archiviati in colonne di **varbinary (max)** o **immagine** tipo di dati. Le immagini non vengono indicizzate.  
  
 [  **@action=** ] **'***azione***'**  
 Azione da eseguire. *azione* è **varchar (20)**e non prevede alcun valore predefinito può essere uno dei valori seguenti.  
  
|Valore|Description|  
|-----------|-----------------|  
|**add**|Aggiunge *column_name* di *qualified_table_name* all'indice full-text inattivo della tabella. Questa azione abilita la colonna per l'indicizzazione full-text.|  
|**drop**|Rimuove *column_name* di *qualified_table_name* dall'indice full-text inattivo della tabella.|  
  
 [  **@language=** ] **'***language_term***'**  
 Lingua dei dati archiviati nella colonna. Per un elenco delle lingue incluse in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], vedere [Sys. fulltext_languages &#40; Transact-SQL &#41; ](../../relational-databases/system-catalog-views/sys-fulltext-languages-transact-sql.md).  
  
> [!NOTE]  
>  Se una colonna include dati in più lingue o in una lingua non supportata, utilizzare la lingua neutra. Il valore predefinito è specificato nell'opzione di configurazione "default full-text language".  
  
 [ **@type_colname =** ] **'***type_column_name***'**  
 È il nome di una colonna in *qualified_table_name* che contiene il tipo di documento *column_name*. Questa colonna deve essere **char**, **nchar**, **varchar**, o **nvarchar**. Viene utilizzato solo quando il tipo di dati *column_name* è di tipo **varbinary (max)** o **immagine**. *type_column_name* è **sysname**, non prevede alcun valore predefinito.  
  
## <a name="return-code-values"></a>Valori restituiti  
 0 (esito positivo) o 1 (esito negativo)  
  
## <a name="result-sets"></a>Set di risultati  
 Nessuno  
  
## <a name="remarks"></a>Osservazioni  
 Se l'indice full-text è attivo, l'eventuale processo di popolamento in corso viene arrestato. Inoltre, se in una tabella con indice full-text attivo è abilitato il rilevamento delle modifiche, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] assicura che l'indice sia aggiornato. Ad esempio, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] arresta l'eventuale processo di popolamento in corso nella tabella, elimina l'indice esistente e avvia un nuovo popolamento.  
  
 Se il rilevamento delle modifiche è attivato e devono essere aggiunte o eliminate colonne dall'indice full-text conservando tuttavia l'indice, è necessario disattivare la tabella, quindi aggiungere ed eliminare le colonne appropriate. In seguito a queste azioni l'indice viene bloccato. È quindi possibile attivare la tabella in un momento successivo, quando è opportuno avviare un processo di popolamento.  
  
## <a name="permissions"></a>Autorizzazioni  
 Utente deve essere un membro del **db_ddladmin** o un membro del ruolo di **db_owner** ruolo predefinito del database o il proprietario della tabella.  
  
## <a name="examples"></a>Esempi  
 Nell'esempio seguente la colonna `DocumentSummary` della tabella `Document` viene aggiunta all'indice full-text della tabella.  
  
```  
USE AdventureWorks2012;  
GO  
EXEC sp_fulltext_column 'Production.Document', DocumentSummary, 'add';  
GO  
```  
  
 Nell'esempio seguente si presuppone che sia stato creato un indice full-text nella tabella `spanishTbl`. Per aggiungere la colonna `spanishCol` all'indice full-text, eseguire la stored procedure seguente:  
  
```  
EXEC sp_fulltext_column 'spanishTbl', 'spanishCol', 'add', 0xC0A;  
GO  
```  
  
 Quando si esegue la seguente query:  
  
```  
SELECT *   
FROM spanishTbl   
WHERE CONTAINS(spanishCol, 'formsof(inflectional, trabajar)')  
```  
  
 Il set di risultati deve includere le righe contenenti forme diverse del verbo spagnolo `trabajar` (lavorare), ad esempio `trabajo`, `trabajamos` e `trabajan`.  
  
> [!NOTE]  
>  È necessario che in tutte le colonne elencate in una singola clausola di funzione per query full-text sia applicata la stessa lingua.  
  
## <a name="see-also"></a>Vedere anche  
 [OBJECTPROPERTY &#40;Transact-SQL&#41;](../../t-sql/functions/objectproperty-transact-sql.md)   
 [sp_help_fulltext_columns &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-help-fulltext-columns-transact-sql.md)   
 [sp_help_fulltext_columns_cursor &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-help-fulltext-columns-cursor-transact-sql.md)   
 [sp_help_fulltext_tables &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-help-fulltext-tables-transact-sql.md)   
 [sp_help_fulltext_tables_cursor &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-help-fulltext-tables-cursor-transact-sql.md)   
 [Stored procedure di sistema &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)   
 [Ricerca full-Text e semantica Stored procedure &#40; Transact-SQL &#41;](../../relational-databases/system-stored-procedures/full-text-search-and-semantic-search-stored-procedures-transact-sql.md)  
  
  
