---
title: COLUMNPROPERTY (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 07/24/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.service: ''
ms.component: t-sql|functions
ms.reviewer: ''
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- COLUMNPROPERTY
- COLUMNPROPERTY_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- column properties [SQL Server]
- parameters [SQL Server], properties
- COLUMNPROPERTY function
ms.assetid: 2408c264-6eca-4120-bb71-df043c7c2792
caps.latest.revision: 44
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: On Demand
ms.openlocfilehash: 5c26df937a654289c6a5313631a612bfbd386cc6
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
---
# <a name="columnproperty-transact-sql"></a>COLUMNPROPERTY (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

Restituisce informazioni su una colonna o un parametro.
  
![Icona di collegamento a un argomento](../../database-engine/configure-windows/media/topic-link.gif "Icona di collegamento a un argomento")[Convenzioni della sintassi Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)
  
## <a name="syntax"></a>Sintassi  
  
```sql
COLUMNPROPERTY ( id , column , property )   
```  
  
## <a name="arguments"></a>Argomenti  
*id*  
[Espressione](../../t-sql/language-elements/expressions-transact-sql.md) che include l'identificatore (ID) della tabella o procedura.
  
*column*  
Espressione che include il nome di colonna o di parametro.
  
*property*  
Espressione che indica le informazioni da restituire per *id*. I possibili valori sono i seguenti.
  
|valore|Description|Valore restituito|  
|---|---|---|
|**AllowsNull**|Ammette valori Null.|1 = TRUE<br /><br /> 0 = FALSE<br /><br /> NULL = Input non valido.|  
|**ColumnId**|Valore di ID di colonna corrispondente a **sys.columns.column_id**.|ID colonna<br /><br /> **Nota:** quando si eseguono query su più colonne, potrebbero apparire spazi vuoti nella sequenza dei valori di ID di colonna.|  
|**FullTextTypeColumn**|TYPE COLUMN nella tabella in cui sono contenute le informazioni sui tipi di documenti di *column*.|ID di TYPE COLUMN full-text per la colonna passata come secondo parametro della proprietà.|  
|**IsComputed**|La colonna è una colonna calcolata.|1 = TRUE<br /><br /> 0 = FALSE<br /><br /> NULL = Input non valido.|  
|**IsCursorType**|Il parametro di procedura è di tipo CURSOR.|1 = TRUE<br /><br /> 0 = FALSE<br /><br /> NULL = Input non valido.|  
|**IsDeterministic**|La colonna è tipo deterministico. Questa proprietà viene applicata solo alle colonne calcolate e alle colonne di una vista.|1 = TRUE<br /><br /> 0 = FALSE<br /><br /> NULL = Input non valido. Non si tratta di una colonna calcolata o di una colonna di vista.|  
|**IsFulltextIndexed**|La colonna è stata registrata per un'indicizzazione full-text.|1 = TRUE<br /><br /> 0 = FALSE<br /><br /> NULL = Input non valido.|  
|**IsIdentity**|La colonna utilizza la proprietà IDENTITY.|1 = TRUE<br /><br /> 0 = FALSE<br /><br /> NULL = Input non valido.|  
|**IsIdNotForRepl**|La colonna controlla l'impostazione IDENTITY_INSERT.|1 = TRUE<br /><br /> 0 = FALSE<br /><br /> NULL = Input non valido.|  
|**IsIndexable**|La colonna può essere indicizzata.|1 = TRUE<br /><br /> 0 = FALSE<br /><br /> NULL = Input non valido.|  
|**IsOutParam**|Il parametro di procedura è di output.|1 = TRUE<br /><br /> 0 = FALSE NULL = input non valido.|  
|**IsPrecise**|La colonna è precisa. Questa proprietà viene applicata solo a colonne di tipo deterministico.|1 = TRUE<br /><br /> 0 = FALSE NULL = input non valido. Non si tratta di una colonna di tipo deterministico.|  
|**IsRowGuidCol**|La colonna è di tipo dati **uniqueidentifier** e viene definita con la proprietà ROWGUIDCOL.|1 = TRUE<br /><br /> 0 = FALSE<br /><br /> NULL = Input non valido.|  
|**IsSystemVerified**|Le proprietà di determinismo e precisione della colonna possono essere verificate dal [!INCLUDE[ssDE](../../includes/ssde-md.md)]. Questa proprietà è applicabile solo alle colonne calcolate e alle colonne di viste.|1 = TRUE<br /><br /> 0 = FALSE<br /><br /> NULL = Input non valido.|  
|**IsXmlIndexable**|La colonna XML può essere utilizzata in un indice XML|1 = TRUE<br /><br /> 0 = FALSE<br /><br /> NULL = Input non valido.|  
|**Precisione**|Lunghezza del tipo di dati della colonna o del parametro.|Lunghezza del tipo di dati specificato per la colonna.<br /><br /> -1 = **xml** o tipi di dati per valori di grandi dimensioni<br /><br /> NULL = Input non valido.|  
|**Scala**|Scala del tipo di dati della colonna o del parametro.|Valore della scala<br /><br /> NULL = Input non valido.|  
|**StatisticalSemantics**|La colonna è abilitata per l'indicizzazione semantica.|1 = TRUE<br /><br /> 0 = FALSE|  
|**SystemDataAccess**|La colonna deriva da una funzione che accede ai dati nei cataloghi di sistema o nelle tabelle virtuali di sistema di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Questa proprietà è applicabile solo alle colonne calcolate e alle colonne di viste.|1 = TRUE (accesso di sola lettura).<br /><br /> 0 = FALSE<br /><br /> NULL = Input non valido.|  
|**UserDataAccess**|La colonna deriva da una funzione che accede ai dati nelle tabelle utente, incluse le tabelle temporanee e le viste, archiviate nell'istanza locale di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Questa proprietà è applicabile solo alle colonne calcolate e alle colonne di viste.|1 = TRUE (accesso di sola lettura).<br /><br /> 0 = FALSE<br /><br /> NULL = Input non valido.|  
|**UsesAnsiTrim**|In fase di creazione della tabella l'opzione ANSI_PADDING era impostata su ON. Questa proprietà viene applicata solo alle colonne o ai parametri di tipo **char** o **varchar**.|1= TRUE<br /><br /> 0= FALSE<br /><br /> NULL = Input non valido.|  
|**IsSparse**|La colonna è una colonna di tipo sparse. Per altre informazioni, vedere [Usare le colonne di tipo sparse](../../relational-databases/tables/use-sparse-columns.md).|1= TRUE<br /><br /> 0= FALSE<br /><br /> NULL = Input non valido.|  
|**IsColumnSet**|La colonna è un set di colonne. Per altre informazioni, vedere [Usare set di colonne](../../relational-databases/tables/use-column-sets.md).|1= TRUE<br /><br /> 0= FALSE<br /><br /> NULL = Input non valido.|  
|**GeneratedAlwaysType**|Valore di colonna generato dal sistema. Corrisponde a **sys.columns.generated_always_type**|**Si applica a**: [!INCLUDE[ssSQL15](../../includes/sssql15-md.md)] tramite [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].<br /><br /> 0 = GENERATED ALWAYS non presente<br /><br /> 1 = GENERATED ALWAYS AS ROW START<br /><br /> 2 = GENERATED ALWAYS AS ROW END|  
|**IsHidden**|Valore di colonna generato dal sistema. Corrisponde a **sys.columns.is_hidden**|**Si applica a**: [!INCLUDE[ssCurrentLong](../../includes/sscurrentlong-md.md)] tramite [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].<br /><br /> 0 = HIDDEN non presente<br /><br /> 1 = HIDDEN|  
  
## <a name="return-types"></a>Tipi restituiti
 **int**  
  
## <a name="exceptions"></a>Eccezioni  
Restituisce NULL in caso di errore o se un chiamante non dispone dell'autorizzazione necessaria per visualizzare l'oggetto.
  
Un utente può visualizzare esclusivamente i metadati delle entità a sicurezza diretta di cui è proprietario o per cui ha ricevuto un'autorizzazione. Di conseguenza, le funzioni predefinite di creazione dei metadati come COLUMNPROPERTY possono restituire NULL se l'utente non dispone di alcuna autorizzazione per l'oggetto. Per altre informazioni, vedere [Metadata Visibility Configuration](../../relational-databases/security/metadata-visibility-configuration.md).
  
## <a name="remarks"></a>Remarks  
Durante il controllo della proprietà deterministica di una colonna, è innanzitutto necessario verificare se la colonna è calcolata. **IsDeterministic** restituisce NULL per le colonne non calcolate. È possibile specificare le colonne calcolate come colonne di indice.
  
## <a name="examples"></a>Esempi  
Nell'esempio seguente viene restituita la lunghezza della colonna `LastName`.
  
```sql
USE AdventureWorks2012;  
GO  
SELECT COLUMNPROPERTY( OBJECT_ID('Person.Person'),'LastName','PRECISION')AS 'Column Length';  
GO  
```  
  
[!INCLUDE[ssResult](../../includes/ssresult-md.md)]
  
```
Column Length
-------------
50
```  
  
## <a name="see-also"></a>Vedere anche
[Funzioni per i metadati &#40;Transact-SQL&#41;](../../t-sql/functions/metadata-functions-transact-sql.md)  
[TYPEPROPERTY &#40;Transact-SQL&#41;](../../t-sql/functions/typeproperty-transact-sql.md)
  
  
