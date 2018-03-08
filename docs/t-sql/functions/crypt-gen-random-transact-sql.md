---
title: CRYPT_GEN_RANDOM (Transact-SQL) | Documenti Microsoft
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
ms.topic: language-reference
f1_keywords:
- CRYPT_GEN_RANDOM_TSQL
- CRYPT_GEN_RANDOM
dev_langs:
- TSQL
helpviewer_keywords:
- CRYPT_GEN_RANDOM function
ms.assetid: b74bd9d4-758e-4b94-89a0-76dcda6d8c42
caps.latest.revision: 
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 695af04a3ee411392cf00be6b6483c9338a4c989
ms.sourcegitcommit: 45e4efb7aa828578fe9eb7743a1a3526da719555
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 11/21/2017
---
# <a name="cryptgenrandom-transact-sql"></a>CRYPT_GEN_RANDOM (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

Restituisce un numero casuale di crittografia generato da CryptoAPI (CAPI). L'output è un numero esadecimale del numero di byte specificato.
  
![Icona di collegamento a un argomento](../../database-engine/configure-windows/media/topic-link.gif "Icona di collegamento a un argomento")[Convenzioni della sintassi Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)
  
## <a name="syntax"></a>Sintassi  
  
```sql
CRYPT_GEN_RANDOM ( length [ , seed ] )   
```  
  
## <a name="arguments"></a>Argomenti  
*length*  
Lunghezza del numero creato. Il valore massimo è 8000. *lunghezza* è di tipo **int**.
  
*valore di inizializzazione*  
Dati facoltativi da utilizzare come valore di inizializzazione casuale.  Deve esserci almeno *lunghezza* byte di dati. *valore di inizializzazione* è **varbinary (8000)**.
  
## <a name="returned-types"></a>Tipi restituiti  
**varbinary (8000)**
  
## <a name="permissions"></a>Permissions  
Questa funzione è pubblica e non richiede autorizzazioni speciali.
  
## <a name="examples"></a>Esempi  
  
### <a name="a-generating-a-random-number"></a>A. Generazione di un numero casuale  
Nell'esempio seguente viene generato un numero casuale con una lunghezza pari a 50 byte.
  
```sql
SELECT CRYPT_GEN_RANDOM(50) ;  
```  
  
Nell'esempio seguente viene generato un numero casuale con una lunghezza pari a 4 byte, utilizzando un valore di inizializzazione di 4 byte.
  
```sql
SELECT CRYPT_GEN_RANDOM(4, 0x25F18060) ;  
```  
  
## <a name="see-also"></a>Vedere anche
[RAND &#40; Transact-SQL &#41;](../../t-sql/functions/rand-transact-sql.md)
  
  
