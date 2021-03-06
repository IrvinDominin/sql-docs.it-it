---
title: SET ROWCOUNT (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 03/16/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: t-sql
ms.topic: language-reference
f1_keywords:
- SET_ROWCOUNT_TSQL
- ROWCOUNT_TSQL
- SET ROWCOUNT
- ROWCOUNT
dev_langs:
- TSQL
helpviewer_keywords:
- row return limitations [SQL Server]
- SET ROWCOUNT statement
- number of rows affected by statement
- ROWCOUNT option
- counting rows
- stopping queries
- limiting rows returned
- queries [SQL Server], stopping
ms.assetid: c6966fb7-6421-47ef-98f3-82351f2f6bdc
author: CarlRabeler
ms.author: carlrab
manager: craigg
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: 539cc61e73d56d4e1de8a1710294f760d109d5d6
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 10/01/2018
ms.locfileid: "47774159"
---
# <a name="set-rowcount-transact-sql"></a>SET ROWCOUNT (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-all-md](../../includes/tsql-appliesto-ss2008-all-md.md)]

  Provoca l'arresto dell'elaborazione della query in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] dopo che è stato restituito il numero di righe specificato.  
  
 ![Icona di collegamento a un argomento](../../database-engine/configure-windows/media/topic-link.gif "Icona di collegamento a un argomento")[Convenzioni della sintassi Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Sintassi  
  
```  
SET ROWCOUNT { number | @number_var }   
```  
  
## <a name="arguments"></a>Argomenti  
 *number* | @*number_var*  
 Numero intero di righe da elaborare prima dell'arresto della query specifica.  
  
## <a name="remarks"></a>Remarks  
  
> [!IMPORTANT]  
>  L'utilizzo di SET ROWCOUNT non avrà effetto sulle istruzioni DELETE, INSERT e UPDATE in una versione futura di SQL Server. Evitare di utilizzare l'opzione SET ROWCOUNT con le istruzioni DELETE, INSERT e UPDATE in un nuovo progetto di sviluppo e prevedere interventi di modifica nelle applicazioni in cui è attualmente implementata. Per un comportamento simile, utilizzare la sintassi TOP. Per altre informazioni, vedere [TOP &#40;Transact-SQL&#41;](../../t-sql/queries/top-transact-sql.md).  
  
 Per disattivare questa opzione in modo che vengano restituite tutte le righe, specificare SET ROWCOUNT 0.  
  
 L'impostazione dell'opzione SET ROWCOUNT comporta l'arresto della maggior parte delle istruzioni [!INCLUDE[tsql](../../includes/tsql-md.md)] quando queste raggiungono il numero di righe specificato. Sono inclusi i trigger. L'opzione ROWCOUNT non ha effetto sui cursori dinamici, ma limita il set di righe dei cursori di tipo KEYSET e INSENSITIVE. Utilizzare questa opzione con cautela.  
  
 L'opzione SET ROWCOUNT è prioritaria rispetto alla parola chiave TOP dell'istruzione SELECT se il conteggio delle righe corrisponde a un valore inferiore.  
  
 L'opzione SET ROWCOUNT viene impostata in fase di esecuzione, non in fase di analisi.  
  
## <a name="permissions"></a>Permissions  
 È richiesta l'appartenenza al ruolo public.  
  
## <a name="examples"></a>Esempi  
 L'opzione SET ROWCOUNT consente di arrestare l'elaborazione dopo il numero di righe specificato. Nell'esempio seguente si noti come oltre 500 righe soddisfino i criteri di `Quantity` minore di `300`. Dopo avere applicato SET ROWCOUNT, tuttavia, si noterà come non siano state restituite tutte le righe.  
  
```  
USE AdventureWorks2012;  
GO  
SELECT count(*) AS Count  
FROM Production.ProductInventory  
WHERE Quantity < 300;  
GO  
```  
  
 [!INCLUDE[ssResult](../../includes/ssresult-md.md)]  
  
 ```
 Count 
 ----------- 
 537 
 
 (1 row(s) affected)
 ```  
  
 Impostare quindi `ROWCOUNT` su `4` e restituire tutte le righe per dimostrare come vengano restituite solo 4 righe.  
  
```  
SET ROWCOUNT 4;  
SELECT *  
FROM Production.ProductInventory  
WHERE Quantity < 300;  
GO  
  
(4 row(s) affected)
```  
  
## <a name="examples-includesssdwfullincludessssdwfull-mdmd-and-includesspdwincludessspdw-mdmd"></a>Esempi: [!INCLUDE[ssSDWfull](../../includes/sssdwfull-md.md)] e [!INCLUDE[ssPDW](../../includes/sspdw-md.md)]  
 L'opzione SET ROWCOUNT consente di arrestare l'elaborazione dopo il numero di righe specificato. Nell'esempio seguente più di 20 righe soddisfano il criterio `AccountType = 'Assets'`. Dopo avere applicato SET ROWCOUNT, tuttavia, si noterà come non siano state restituite tutte le righe.  
  
```  
-- Uses AdventureWorks  
  
SET ROWCOUNT 5;  
SELECT * FROM [dbo].[DimAccount]  
WHERE AccountType = 'Assets';  
```  
  
 Per restituire tutte le righe, impostare ROWCOUNT su 0.  
  
```  
-- Uses AdventureWorks  
  
SET ROWCOUNT 0;  
SELECT * FROM [dbo].[DimAccount]  
WHERE AccountType = 'Assets';  
```  
  
## <a name="see-also"></a>Vedere anche  
 [Istruzioni SET &#40;Transact-SQL&#41;](../../t-sql/statements/set-statements-transact-sql.md)  
  
  

