---
title: Catalog.cleanup_server_log | Documenti Microsoft
ms.custom: 
ms.date: 03/03/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- integration-services
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 0dedb685-d3a6-4bd6-8afd-58d98853deee
caps.latest.revision: 5
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: 2edcce51c6822a89151c3c3c76fbaacb5edd54f4
ms.openlocfilehash: 1195bbfcc77cb6b96ea5a68cd1a95c2b2126a81e
ms.contentlocale: it-it
ms.lasthandoff: 09/26/2017

---
# <a name="catalogcleanupserverlog"></a>Catalog.cleanup_server_log
[!INCLUDE[tsql-appliesto-ss2012-xxxx-xxxx-xxx_md](../../includes/tsql-appliesto-ss2012-xxxx-xxxx-xxx-md.md)]

  Pulisce i log operazioni per portare il database SSISDB in uno stato che permette di modificare il valore della proprietà SERVER_OPERATION_ENCRYPTION_LEVEL.  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
cleanup_server_log  
  
```  
  
## <a name="arguments"></a>Argomenti  
 nessuna.  
  
## <a name="return-code-values"></a>Valori restituiti  
 0 per esito positivo e 1 per errore.  
  
## <a name="result-sets"></a>Set di risultati  
 nessuna.  
  
## <a name="permissions"></a>Permissions  
 Per questa stored procedure è necessaria una delle autorizzazioni seguenti:  
  
-   Autorizzazioni READ ed EXECUTE sul progetto e, se applicabile, le autorizzazioni di lettura per l'ambiente di riferimento.  
  
-   L'appartenenza di **ssis_admin** ruolo del database.  
  
-   L'appartenenza al **sysadmin** ruolo del server.  
  
## <a name="errors-and-warnings"></a>Errori e avvisi  
 Questa stored procedure genera errori negli scenari seguenti:  
  
-   Sono presenti uno o più operazioni attive nel database SSISDB.  
  
-   Il database SSISDB non è in modalità utente singolo.  
  
## <a name="remarks"></a>Osservazioni  
 SQL Server 2012 Service Pack 2 aggiunta la proprietà SERVER_OPERATION_ENCRYPTION_LEVEL il **internal.catalog_properties** tabella. Questa proprietà è possibili due valori:  
  
-   **(1) PER_EXECUTION** : il certificato e una chiave simmetrica utilizzata per la protezione dei parametri di esecuzione riservate e vengono creati i log di esecuzione per ogni esecuzione. Si tratta del valore predefinito. Poiché i certificati o chiavi vengono generate per ogni esecuzione, è possibile eseguire in problemi di prestazioni (i deadlock, manutenzione non riusciti processi e così via) in un ambiente di produzione. Tuttavia, questa impostazione fornisce un livello superiore di sicurezza rispetto a altro valore (2).  
  
-   **(2) PER_PROJECT** : il certificato e una chiave simmetrica utilizzata per la protezione dei parametri sensibili vengono creati per ogni progetto. Questo offre prestazioni migliori rispetto al livello PER_EXECUTION perché la chiave e il certificato vengono generati una volta per un progetto, anziché per ogni esecuzione.  
  
 È necessario eseguire il [catalog.cleanup_server_log](../../integration-services/system-stored-procedures/catalog-cleanup-server-log.md) stored procedure prima di poter impostare il SERVER_OPERATION_ENCRYPTION_LEVEL compreso tra 1 e 2 (o) da 2 a 1. Prima di eseguire questa stored procedure, eseguire le operazioni seguenti:  
  
1.  Verificare che il valore della proprietà OPERATION_CLEANUP_ENABLED sia impostato su TRUE nel [Catalog. catalog_properties &#40; Database SSISDB &#41; ](../../integration-services/system-views/catalog-catalog-properties-ssisdb-database.md) tabella.  
  
2.  Impostare il database di Integration Services (SSISDB) in modalità utente singolo. In SQL Server Management Studio, avviare la finestra di dialogo proprietà Database per SSISDB, passare alla scheda Opzioni e impostare la proprietà limita l'accesso in modalità utente singolo (SINGLE_USER). Dopo aver eseguito la cleanup_server_log stored procedure, impostare il valore della proprietà il valore originale.  
  
3.  Eseguire la stored procedure [catalog.cleanup_server_log](../../integration-services/system-stored-procedures/catalog-cleanup-server-log.md).  
  
4.  A questo punto, proseguire e modificare il valore della proprietà SERVER_OPERATION_ENCRYPTION_LEVEL nella [Catalog. catalog_properties &#40; Database SSISDB &#41; ](../../integration-services/system-views/catalog-catalog-properties-ssisdb-database.md) tabella.  
  
5.  Eseguire la stored procedure [catalog.cleanup_server_execution_keys](../../integration-services/system-stored-procedures/catalog-cleanup-server-execution-keys.md) per pulire le chiavi di certificati dal database SSISDB. Eliminazione di certificati e chiavi dal database SSISDB potrebbe richiedere molto tempo, in modo che deve essere eseguito periodicamente durante i periodi.  
  
     È possibile specificare l'ambito o un livello (esecuzione rispetto al progetto) e un numero di chiavi da eliminare. La dimensione di batch predefinito per l'eliminazione è 1000. Quando si imposta il livello su 2, le chiavi e certificati vengono eliminati solo se i progetti associati sono stati eliminati.  
  
 Per altre informazioni, vedere l'articolo della Knowledge Base. [Correzione: Problemi di prestazioni quando si utilizza SSISDB come la distribuzione di memorizzare in SQL Server 2012](http://support.microsoft.com/kb/2972285)  
  
## <a name="example"></a>Esempio  
 Nell'esempio seguente chiama la routine cleanup_server_log archiviati.  
  
```tsql  
USE [SSISDB]  
GO  
  
DECLARE@return_value int  
EXEC@return_value = [internal].[cleanup_server_log]  
SELECT'Return Value' = @return_value  
GO  
  
```  
  
  