---
title: sp_help_spatial_geography_histogram (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sp_help_spatial_geography_histogram_TSQL
- sp_help_spatial_geography_histogram
dev_langs:
- TSQL
helpviewer_keywords:
- sp_help_spatial_geography_histogram
ms.assetid: 5c5bd319-055d-4cd6-8c5a-06354cc056cc
author: CarlRabeler
ms.author: carlrab
manager: craigg
ms.openlocfilehash: 98fe7a36a758eb96e4ab82c7c62a646a67dd34d5
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/01/2018
ms.locfileid: "47638192"
---
# <a name="sphelpspatialgeographyhistogram-transact-sql"></a>sp_help_spatial_geography_histogram (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2012-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2012-xxxx-xxxx-xxx-md.md)]

  Semplifica l'impostazione delle chiavi dei parametri di griglia per un indice spaziale.  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
sp_help_spatial_geography_histogram [ @tabname =] 'tabname'   
     [ , [ @colname = ] 'columnname' ]   
     [ , [ @resolution = ] 'resolution' ]  
     [ , [ @sample = ] 'tablesample' ]  
```  
  
## <a name="arguments"></a>Argomenti  
 [  **@tabname =**] **'***tabname***'**  
 Nome qualificato o non qualificato della tabella per cui è stato specificato l'indice spaziale.  
  
 Le virgolette sono necessarie solo se viene specificata una tabella qualificata. Nel caso di un nome completo, ovvero contenente un nome di database, il nome del database deve corrispondere a quello del database corrente. *TabName* viene **sysname**, non prevede alcun valore predefinito.  
  
 [  **@colname =** ] **'***columnname***'**  
 Nome della colonna spaziale specificata. *ColumnName* è un **sysname**, non prevede alcun valore predefinito.  
  
 [  **@resolution =** ] **'***risoluzione***'**  
 Risoluzione del rettangolo di selezione. I valori validi sono compresi tra 10 e 5000. *risoluzione* è un **tinyint**, non prevede alcun valore predefinito.  
  
 [  **@sample =** ] **'***esempio***'**  
 Percentuale della tabella utilizzata. I valori validi sono da 0 a 100. *TABLESAMPLE* è un **float**. Il valore predefinito è 100.  
  
## <a name="property-valuereturn-value"></a>Valore proprietà/Valore restituito  
 Viene restituito un valore di tabella. Nella griglia seguente viene descritto il contenuto delle colonne della tabella.  
  
|Nome colonna|Tipo di dati|Description|  
|-----------------|---------------|-----------------|  
|**cellid**|**int**|Rappresenta l'ID univoco di ciascuna cella, con un conteggio iniziale di 1.|  
|**cella**|**geography**|Poligono rettangolare che rappresenta ciascuna cella. La forma della cella è identica alla forma della cella utilizzata per l'indicizzazione spaziale.|  
|**row_count**|**bigint**|Indica il numero di oggetti spaziali che toccano o contengono la cella.|  
  
## <a name="permissions"></a>Permissions  
 Utente deve essere un membro del **pubblica** ruolo. È necessario disporre dell'autorizzazione READ ACCESS per il server e l'oggetto.  
  
## <a name="remarks"></a>Note  
 Nella scheda spaziale di SSMS viene illustrata una rappresentazione grafica dei risultati. È possibile eseguire una query sui risultati rispetto alla finestra spaziale per ottenere un numero approssimativo di risultati.  
  
> [!NOTE]  
>  Gli oggetti nella tabella potrebbero interessare più di una cella, pertanto la somma delle celle nella tabella potrebbe essere maggiore del numero di oggetti effettivi.  
  
 Il riquadro delimitatore per i **geografia** tipo è l'intero globo.  
  
## <a name="examples"></a>Esempi  
 Nell'esempio seguente viene chiamato **sp_help_spatial_geography_histogram** nel `Person.Address` nella tabella di [!INCLUDE[ssSampleDBnormal](../../includes/sssampledbnormal-md.md)] database.  
  
```  
EXEC sp_help_spatial_geography_histogram @tabname = Person.Address, @colname = SpatialLocation, @resolution = 64, @sample = 30;  
```  
  
## <a name="see-also"></a>Vedere anche  
 [Indice spaziale Stored procedure &#40;Transact-SQL&#41;](http://msdn.microsoft.com/library/1be0f34e-3d5a-4a1f-9299-bd482362ec7a)  
  
  
