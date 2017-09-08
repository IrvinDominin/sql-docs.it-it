---
title: ERROR_MESSAGE (Transact-SQL) | Documenti Microsoft
ms.custom: 
ms.date: 03/16/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- ERROR_MESSAGE_TSQL
- ERROR_MESSAGE
dev_langs:
- TSQL
helpviewer_keywords:
- ERROR_MESSAGE function
- errors [SQL Server], text of
- messages [SQL Server], text of
- TRY...CATCH [SQL Server]
- CATCH block
ms.assetid: f32877a6-5f17-418c-a32c-5a1a344b3c45
caps.latest.revision: 53
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: f15d9d23726f7558f0bf73aff3f8c3c5253cb24d
ms.contentlocale: it-it
ms.lasthandoff: 09/01/2017

---
# <a name="errormessage-transact-sql"></a>ERROR_MESSAGE (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-all_md](../../includes/tsql-appliesto-ss2008-all-md.md)]

  Restituisce il testo del messaggio dell'errore che ha causato l'esecuzione del blocco CATCH di un costrutto TRY…CATCH.  
  
 ![Icona di collegamento a un argomento](../../database-engine/configure-windows/media/topic-link.gif "Icona di collegamento a un argomento")[Convenzioni della sintassi Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Sintassi  
  
```  
-- Syntax for SQL Server, Azure SQL Database, Azure SQL Data Warehouse, Parallel Data Warehouse  
  
ERROR_MESSAGE ( )   
```  
  
## <a name="return-types"></a>Tipi restituiti  
 **nvarchar(4000)**  
  
## <a name="return-value"></a>Valore restituito  
 Quando viene chiamata in un blocco CATCH, restituisce il testo completo del messaggio di errore che ha causato l'esecuzione del blocco CATCH. Il testo include i valori forniti da qualsiasi parametro sostituibile, ad esempio lunghezze, nomi di oggetti oppure orari.  
  
 Restituisce NULL se chiamata all'esterno dell'ambito di un blocco CATCH.  
  
## <a name="remarks"></a>Osservazioni  
 ERROR_MESSAGE può essere chiamata in qualsiasi punto nell'ambito di un blocco CATCH.  
  
 ERROR_MESSAGE restituisce il messaggio di errore indipendentemente da quante volte o in quale punto viene eseguita nell'ambito del blocco CATCH. Ciò si differenzia da funzioni come @@ERROR, che restituisce solo un numero di errore nell'istruzione immediatamente successiva a quella che provoca un errore o bloccare la prima istruzione di un blocco CATCH.  
  
 Nei blocchi CATCH nidificati viene restituito il messaggio di errore specifico dell'ambito del blocco CATCH contenente il riferimento a ERROR_MESSAGE. Ad esempio, il blocco CATCH di un costrutto esterno TRY...CATCH potrebbe includere un costrutto TRY...CATCH nidificato. All'interno del blocco CATCH nidificato ERROR_MESSAGE restituisce il messaggio dall'errore che ha richiamato il blocco CATCH nidificato. Se ERROR_MESSAGE viene eseguita nel blocco CATCH esterno, restituisce il messaggio dell'errore che ha richiamato tale blocco CATCH.  
  
## <a name="examples"></a>Esempi  
  
### <a name="a-using-errormessage-in-a-catch-block"></a>A. Utilizzo di ERROR_MESSAGE in un blocco CATCH  
 Nell'esempio seguente viene illustrata un'istruzione `SELECT` che genera un errore di divisione per zero. Viene restituito il messaggio dell'errore.  
  
```  
  
BEGIN TRY  
    -- Generate a divide-by-zero error.  
    SELECT 1/0;  
END TRY  
BEGIN CATCH  
    SELECT ERROR_MESSAGE() AS ErrorMessage;  
END CATCH;  
GO  
```  
  
### <a name="b-using-errormessage-in-a-catch-block-with-other-error-handling-tools"></a>B. Utilizzo di ERROR_MESSAGE in un blocco CATCH con altri strumenti di gestione degli errori  
 Nell'esempio seguente viene illustrata un'istruzione `SELECT` che genera un errore di divisione per zero. Insieme al messaggio di errore vengono restituite informazioni relative all'errore.  
  
```  
  
BEGIN TRY  
    -- Generate a divide-by-zero error.  
    SELECT 1/0;  
END TRY  
BEGIN CATCH  
    SELECT  
        ERROR_NUMBER() AS ErrorNumber  
        ,ERROR_SEVERITY() AS ErrorSeverity  
        ,ERROR_STATE() AS ErrorState  
        ,ERROR_PROCEDURE() AS ErrorProcedure  
        ,ERROR_LINE() AS ErrorLine  
        ,ERROR_MESSAGE() AS ErrorMessage;  
END CATCH;  
GO  
```  
  
## <a name="examples-includesssdwfullincludessssdwfull-mdmd-and-includesspdwincludessspdw-mdmd"></a>Esempi: [!INCLUDE[ssSDWfull](../../includes/sssdwfull-md.md)] e[!INCLUDE[ssPDW](../../includes/sspdw-md.md)]  
  
### <a name="c-using-errormessage-in-a-catch-block"></a>C. Utilizzo di ERROR_MESSAGE in un blocco CATCH  
 Nell'esempio seguente viene illustrata un'istruzione `SELECT` che genera un errore di divisione per zero. Viene restituito il messaggio dell'errore.  
  
```  
  
BEGIN TRY  
    -- Generate a divide-by-zero error.  
    SELECT 1/0;  
END TRY  
BEGIN CATCH  
    SELECT ERROR_MESSAGE() AS ErrorMessage;  
END CATCH;  
GO  
```  
  
### <a name="d-using-errormessage-in-a-catch-block-with-other-error-handling-tools"></a>D. Utilizzo di ERROR_MESSAGE in un blocco CATCH con altri strumenti di gestione degli errori  
 Nell'esempio seguente viene illustrata un'istruzione `SELECT` che genera un errore di divisione per zero. Insieme al messaggio di errore vengono restituite informazioni relative all'errore.  
  
```  
  
BEGIN TRY  
    -- Generate a divide-by-zero error.  
    SELECT 1/0;  
END TRY  
BEGIN CATCH  
    SELECT  
        ERROR_NUMBER() AS ErrorNumber  
        ,ERROR_SEVERITY() AS ErrorSeverity  
        ,ERROR_STATE() AS ErrorState  
        ,ERROR_PROCEDURE() AS ErrorProcedure  
        ,ERROR_MESSAGE() AS ErrorMessage;  
END CATCH;  
GO  
```  
  
## <a name="see-also"></a>Vedere anche  
 [sys.messages &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/messages-for-errors-catalog-views-sys-messages.md)   
 [TRY...CATCH &#40;Transact-SQL&#41;](../../t-sql/language-elements/try-catch-transact-sql.md)   
 [ERROR_LINE &#40;Transact-SQL&#41;](../../t-sql/functions/error-line-transact-sql.md)   
 [ERROR_NUMBER &#40;Transact-SQL&#41;](../../t-sql/functions/error-number-transact-sql.md)   
 [ERROR_PROCEDURE &#40;Transact-SQL&#41;](../../t-sql/functions/error-procedure-transact-sql.md)   
 [ERROR_SEVERITY &#40;Transact-SQL&#41;](../../t-sql/functions/error-severity-transact-sql.md)   
 [ERROR_STATE &#40; Transact-SQL &#41;](../../t-sql/functions/error-state-transact-sql.md)   
 [RAISERROR &#40;Transact-SQL&#41;](../../t-sql/language-elements/raiserror-transact-sql.md)   
 [@@ERROR &#40;Transact-SQL&#41;](../../t-sql/functions/error-transact-sql.md)  
  
  

