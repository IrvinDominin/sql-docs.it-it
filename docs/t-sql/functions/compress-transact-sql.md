---
title: COMPRIMI (Transact-SQL) | Documenti Microsoft
ms.custom: 
ms.date: 07/24/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database
ms.service: 
ms.component: t-sql|functions
ms.reviewer: 
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- COMPRESS
- COMPRESS_TSQL
helpviewer_keywords:
- COMPRESS function
ms.assetid: c2bfe9b8-57a4-48b4-b028-e1a3ed5ece88
caps.latest.revision: 
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: On Demand
ms.openlocfilehash: 01500cd6560fd60dda2cb9060c2968d7c010d8e2
ms.sourcegitcommit: 45e4efb7aa828578fe9eb7743a1a3526da719555
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 11/21/2017
---
# <a name="compress-transact-sql"></a>COMPRIMI (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2016-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2016-asdb-xxxx-xxx-md.md)]

Comprime l'espressione di input utilizzando l'algoritmo GZIP. Il risultato della compressione è la matrice di byte di tipo **varbinary (max)**.
  
![Icona di collegamento a un argomento](../../database-engine/configure-windows/media/topic-link.gif "Icona di collegamento a un argomento")[Convenzioni della sintassi Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)
  
## <a name="syntax"></a>Sintassi  
  
```sql
COMPRESS ( expression )  
```  
  
## <a name="arguments"></a>Argomenti  
*espressione*  
È un **nvarchar (***n***)**, **nvarchar (max)**, **varchar (**  *n*  **)**, **varchar (max)**, **varbinary (**  *n*  **)**, **varbinary (max)**, **char (***n***)**, **(nchar**   *n*  **)**, o **binario (***n***)** espressione. Per altre informazioni, vedere [Espressioni &#40;Transact-SQL&#41;](../../t-sql/language-elements/expressions-transact-sql.md).
  
## <a name="return-types"></a>Tipi restituiti
Restituisce il tipo di dati di **varbinary (max)** che rappresenta il contenuto compresso di input.
  
## <a name="remarks"></a>Osservazioni  
I dati compressi non possono essere indicizzati.
  
La funzione COMPRESS comprime i dati forniti come espressione di input e deve essere richiamata per ogni sezione di dati deve essere compresso. Per la compressione automatica a livello di riga o di pagina durante l'archiviazione, vedere [la compressione dei dati](../../relational-databases/data-compression/data-compression.md).
  
## <a name="examples"></a>Esempi  
  
### <a name="a-compress-data-during-the-table-insert"></a>A. Comprimere i dati durante l'inserimento di tabella  
Nell'esempio seguente viene illustrato come comprimere i dati inseriti nella tabella:
  
```sql
INSERT INTO player (name, surname, info )  
VALUES (N'Ovidiu', N'Cracium',   
        COMPRESS(N'{"sport":"Tennis","age": 28,"rank":1,"points":15258, turn":17}'));  
  
INSERT INTO player (name, surname, info )  
VALUES (N'Michael', N'Raheem', compress(@info));  
```  
  
### <a name="b-archive-compressed-version-of-deleted-rows"></a>B. Archiviazione compressa di righe eliminate  
L'istruzione seguente Elimina vecchi record di lettore dal `player` tabella e archivia i record di `inactivePlayer` tabella in un formato compresso per risparmiare spazio.
  
```sql
DELETE player  
WHERE datemodified < @startOfYear  
OUTPUT id, name, surname datemodifier, COMPRESS(info)   
INTO dbo.inactivePlayers ;  
```  
  
## <a name="see-also"></a>Vedere anche
[Funzioni stringa &#40; Transact-SQL &#41;](../../t-sql/functions/string-functions-transact-sql.md)  
[DECOMPRIMERE &#40; Transact-SQL &#41;](../../t-sql/functions/decompress-transact-sql.md)
  
  
