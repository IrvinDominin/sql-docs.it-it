---
title: SESSIONPROPERTY (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.technology: t-sql
ms.topic: language-reference
f1_keywords:
- SESSIONPROPERTY
- SESSIONPROPERTY_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- SET statement, SESSIONPROPERTY function
- SESSIONPROPERTY function
- sessions [SQL Server], SET options settings
ms.assetid: 1f3730b4-1495-4d3a-af43-e57952812df9
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 36fb5844c7255aff7b8527ff5cc462ec5a573977
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 10/01/2018
ms.locfileid: "47642909"
---
# <a name="sessionproperty-transact-sql"></a>SESSIONPROPERTY (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

  Restituisce le impostazioni delle opzioni SET di una sessione.  
  
 ![Icona di collegamento a un argomento](../../database-engine/configure-windows/media/topic-link.gif "Icona di collegamento a un argomento")[Convenzioni della sintassi Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
SESSIONPROPERTY (option)  
```  
  
## <a name="arguments"></a>Argomenti  
 *opzione*  
 Impostazione corrente dell'opzione per questa sessione. *option* può essere uno dei valori seguenti.  
  
|Opzione|Descrizione|  
|------------|-----------------|  
|ANSI_NULLS|Specifica se nei confronti di valori Null viene applicato il funzionamento ISO degli operatori uguale a (=) e diverso da (<>).<br /><br /> 1 = ON<br /><br /> 0 = OFF|  
|ANSI_PADDING|Controlla la modalità di archiviazione nella colonna dei valori di dimensioni minori rispetto alle dimensioni definite per la colonna e dei valori che includono spazi vuoti finali in dati di tipo carattere e binario.<br /><br /> 1 = ON<br /><br /> 0 = OFF|  
|ANSI_WARNINGS|Specifica se in determinate situazioni, quali la divisione per zero e l'overflow aritmetico, viene applicato il funzionamento dello standard ISO che prevede la generazione di messaggi di errore o avvisi.<br /><br /> 1 = ON<br /><br /> 0 = OFF|  
|ARITHABORT|Determina se una query viene interrotta quando si verifica un errore di overflow o di divisione per zero durante l'esecuzione.<br /><br /> 1 = ON<br /><br /> 0 = OFF|  
|CONCAT_NULL_YIELDS_ NULL|Determina se i risultati della concatenazione di valori Null vengono gestiti come valori Null o valori di stringa vuota.<br /><br /> 1 = ON<br /><br /> 0 = OFF|  
|NUMERIC_ROUNDABORT|Specifica se vengono generati messaggi di errore o avvisi quando si verifica una perdita di precisione in seguito all'arrotondamento di un'espressione.<br /><br /> 1 = ON<br /><br /> 0 = OFF|  
|QUOTED_IDENTIFIER|Specifica se devono essere seguite le regole ISO sull'utilizzo delle virgolette per delimitare gli identificatori e le stringhe letterali.<br /><br /> 1 = ON<br /><br /> 0 = OFF|  
|\<Qualsiasi altra stringa>|NULL = Input non valido.|  
  
## <a name="return-types"></a>Tipi restituiti  
 **sql_variant**  
  
## <a name="remarks"></a>Remarks  
 Le opzioni SET vengono calcolate combinando opzioni a livello di server, di database e specifiche dell'utente.  
  
## <a name="examples"></a>Esempi  
 Nell'esempio seguente viene restituita l'impostazione dell'opzione `CONCAT_NULL_YIELDS_NULL`.  
  
```  
SELECT   SESSIONPROPERTY ('CONCAT_NULL_YIELDS_NULL')  
```  
  
## <a name="see-also"></a>Vedere anche  
 [sql_variant &#40;Transact-SQL&#41;](../../t-sql/data-types/sql-variant-transact-sql.md)   
 [SET ANSI_NULLS &#40;Transact-SQL&#41;](../../t-sql/statements/set-ansi-nulls-transact-sql.md)   
 [SET ANSI_PADDING &#40;Transact-SQL&#41;](../../t-sql/statements/set-ansi-padding-transact-sql.md)   
 [SET ANSI_WARNINGS &#40;Transact-SQL&#41;](../../t-sql/statements/set-ansi-warnings-transact-sql.md)   
 [SET ARITHABORT &#40;Transact-SQL&#41;](../../t-sql/statements/set-arithabort-transact-sql.md)   
 [SET CONCAT_NULL_YIELDS_NULL &#40;Transact-SQL&#41;](../../t-sql/statements/set-concat-null-yields-null-transact-sql.md)   
 [SET NUMERIC_ROUNDABORT &#40;Transact-SQL&#41;](../../t-sql/statements/set-numeric-roundabort-transact-sql.md)   
 [SET QUOTED_IDENTIFIER &#40;Transact-SQL&#41;](../../t-sql/statements/set-quoted-identifier-transact-sql.md)  
  
  
