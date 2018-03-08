---
title: ERROR_STATE (Transact-SQL) | Documenti Microsoft
ms.custom: 
ms.date: 03/16/2017
ms.prod: sql-non-specified
ms.prod_service: sql-data-warehouse, pdw, sql-database
ms.service: 
ms.component: t-sql|functions
ms.reviewer: 
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- ERROR_STATE_TSQL
- ERROR_STATE
dev_langs:
- TSQL
helpviewer_keywords:
- messages [SQL Server], state
- ERROR_STATE function
- errors [SQL Server], state
- TRY...CATCH [SQL Server]
- CATCH block
- states [SQL Server], error numbers
ms.assetid: 6059af00-83fe-409f-ab7c-daad111bc671
caps.latest.revision: 
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: On Demand
ms.openlocfilehash: 07caa8a60512f507c9ad1003c864680e82d48870
ms.sourcegitcommit: 45e4efb7aa828578fe9eb7743a1a3526da719555
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 11/21/2017
---
# <a name="errorstate-transact-sql"></a>ERROR_STATE (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-asdw-pdw-md](../../includes/tsql-appliesto-ss2008-xxxx-asdw-pdw-md.md)]

  Restituisce il numero di stato dell'errore che ha attivato l'esecuzione del blocco CATCH di un costrutto TRY…CATCH.  
  
 ![Icona di collegamento a un argomento](../../database-engine/configure-windows/media/topic-link.gif "Icona di collegamento a un argomento")[Convenzioni della sintassi Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Sintassi  
  
```  
ERROR_STATE ( )  
```  
  
## <a name="return-types"></a>Tipi restituiti  
 **int**  
  
## <a name="return-value"></a>Valore restituito  
 Se richiamata in un blocco CATCH, questa istruzione restituisce il numero di stato del messaggio di errore che ha attivato l'esecuzione del blocco CATCH.  
  
 Restituisce NULL se chiamata all'esterno dell'ambito di un blocco CATCH.  
  
## <a name="remarks"></a>Osservazioni  
 Alcuni messaggi di errore possono essere generati in più punti del codice per il [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssDE](../../includes/ssde-md.md)]. L'errore 1105, ad esempio, può essere generato in risposta a numerose condizioni. A ogni condizione specifica che genera l'errore viene assegnato un codice di stato univoco.  
  
 Durante la visualizzazione di database contenenti la trattazione di problemi noti, ad esempio la [!INCLUDE[msCoName](../../includes/msconame-md.md)] Knowledge Base, è possibile utilizzare il numero di stato per determinare se il problema registrato è uguale all'errore rilevato. Se, ad esempio, in un articolo della Knowledge Base viene trattato il messaggio di errore 1105 con stato 2 e il messaggio di errore 1105 restituito è associato allo stato 3, è possibile che la causa dell'errore rilevato sia diversa da quella descritta nell'articolo.  
  
 Il codice di stato di un errore consente al personale del Supporto Tecnico Clienti Microsoft per [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] di individuare la posizione del codice sorgente in cui è stato generato l'errore e di ottenere pertanto indicazioni aggiuntive utili per la diagnostica del problema.  
  
 È possibile richiamare ERROR_STATE da un qualsiasi punto nell'ambito di un blocco CATCH.  
  
 ERROR_STATE restituisce lo stato dell'errore indipendentemente dal numero di esecuzioni oppure dalla sua posizione di esecuzione nell'ambito del blocco CATCH. Ciò si differenzia da funzioni come @@ERROR, che restituisce solo il numero di errore nell'istruzione immediatamente successiva a quella che provoca un errore oppure nella prima istruzione di un blocco CATCH.  
  
 Nei blocchi CATCH nidificati l'istruzione ERROR_STATE restituisce lo stato di errore specifico dell'ambito del blocco CATCH contenente il riferimento a essa. Ad esempio, il blocco CATCH di un costrutto esterno TRY...CATCH potrebbe includere un costrutto TRY...CATCH nidificato. Nel blocco CATCH nidificato ERROR_STATE restituisce lo stato dell'errore che ha richiamato il blocco CATCH nidificato. Se ERROR_STATE viene eseguito in un blocco CATCH esterno, restituisce lo stato dell'errore che ha richiamato tale blocco CATCH.  
  
## <a name="examples"></a>Esempi  
  
### <a name="a-using-errorstate-in-a-catch-block"></a>A. Utilizzo di ERROR_STATE in un blocco CATCH  
 Nell'esempio seguente viene illustrata un'istruzione `SELECT` che genera un errore di divisione per zero. Viene restituito lo stato dell'errore.  
  
```  
BEGIN TRY  
    -- Generate a divide by zero error  
    SELECT 1/0;  
END TRY  
BEGIN CATCH  
    SELECT ERROR_STATE() AS ErrorState;  
END CATCH;  
GO  
```  
  
### <a name="b-using-errorstate-in-a-catch-block-with-other-error-handling-tools"></a>B. Utilizzo di ERROR_STATE in un blocco CATCH con altri strumenti di gestione degli errori  
 Nell'esempio seguente viene illustrata un'istruzione `SELECT` che genera un errore di divisione per zero. Assieme allo stato dell'errore vengono restituite le informazioni relative all'errore stesso.  
  
```  
BEGIN TRY  
    -- Generate a divide-by-zero error.  
    SELECT 1/0;  
END TRY  
BEGIN CATCH  
    SELECT  
        ERROR_NUMBER() AS ErrorNumber,  
        ERROR_SEVERITY() AS ErrorSeverity,  
        ERROR_STATE() AS ErrorState,  
        ERROR_PROCEDURE() AS ErrorProcedure,  
        ERROR_LINE() AS ErrorLine,  
        ERROR_MESSAGE() AS ErrorMessage;  
END CATCH;  
GO  
```  
  
## <a name="examples-includesssdwfullincludessssdwfull-mdmd-and-includesspdwincludessspdw-mdmd"></a>Esempi: [!INCLUDE[ssSDWfull](../../includes/sssdwfull-md.md)] e[!INCLUDE[ssPDW](../../includes/sspdw-md.md)]  
  
### <a name="c-using-errorstate-in-a-catch-block-with-other-error-handling-tools"></a>C. Utilizzo di ERROR_STATE in un blocco CATCH con altri strumenti di gestione degli errori  
 Nell'esempio seguente viene illustrata un'istruzione `SELECT` che genera un errore di divisione per zero. Assieme allo stato dell'errore vengono restituite le informazioni relative all'errore stesso.  
  
```  
BEGIN TRY  
    -- Generate a divide-by-zero error.  
    SELECT 1/0;  
END TRY  
BEGIN CATCH  
    SELECT  
        ERROR_NUMBER() AS ErrorNumber,  
        ERROR_SEVERITY() AS ErrorSeverity,  
        ERROR_STATE() AS ErrorState,  
        ERROR_PROCEDURE() AS ErrorProcedure,  
        ERROR_MESSAGE() AS ErrorMessage;  
END CATCH;  
GO  
```  
  
## <a name="see-also"></a>Vedere anche  
 [sys.messages &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/messages-for-errors-catalog-views-sys-messages.md)   
 [TRY...CATCH &#40;Transact-SQL&#41;](../../t-sql/language-elements/try-catch-transact-sql.md)   
 [ERROR_LINE &#40;Transact-SQL&#41;](../../t-sql/functions/error-line-transact-sql.md)   
 [ERROR_MESSAGE &#40;Transact-SQL&#41;](../../t-sql/functions/error-message-transact-sql.md)   
 [ERROR_NUMBER &#40;Transact-SQL&#41;](../../t-sql/functions/error-number-transact-sql.md)   
 [ERROR_PROCEDURE &#40;Transact-SQL&#41;](../../t-sql/functions/error-procedure-transact-sql.md)   
 [ERROR_SEVERITY &#40;Transact-SQL&#41;](../../t-sql/functions/error-severity-transact-sql.md)   
 [RAISERROR &#40;Transact-SQL&#41;](../../t-sql/language-elements/raiserror-transact-sql.md)   
 [@@ERROR &#40;Transact-SQL&#41;](../../t-sql/functions/error-transact-sql.md)  
  
  

