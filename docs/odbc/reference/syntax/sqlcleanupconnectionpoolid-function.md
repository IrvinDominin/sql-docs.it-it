---
title: Funzione SQLCleanupConnectionPoolID | Documenti Microsoft
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: drivers
ms.service: ''
ms.component: odbc
ms.reviewer: ''
ms.suite: sql
ms.technology:
- drivers
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- SQLCleanupConnectionPoolID function [ODBC]
ms.assetid: 1fc61908-e003-4587-b91a-32f40569fb99
caps.latest.revision: 11
author: MightyPen
ms.author: genemi
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: f825395406e4dcdedc9bf0577d32823afc9e7a46
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
---
# <a name="sqlcleanupconnectionpoolid-function"></a>SQLCleanupConnectionPoolID (funzione)
**Conformità**  
 Introdotta: versione ODBC standard 3,81 conformità: ODBC  
  
 **Riepilogo**  
 **SQLCleanupConnectionPoolID** indica un driver che un ID del pool è stato verificato il timeout. Timeout di un pool di ID possibile timeout ogni volta che sono state tutte le connessioni in un pool associata a tale ID pool di applicazioni. Vedere [pool in Microsoft Data Access Components](http://msdn.microsoft.com/library/ms810829.aspx) per ulteriori informazioni sui timeout di connessione.  
  
## <a name="syntax"></a>Sintassi  
  
```  
SQLRETURN  SQLCleanupConnectionPoolID (  
                SQLHENV    EnvironmentHandle  
                SQLPOOLID  PoolID );  
```  
  
## <a name="arguments"></a>Argomenti  
 *EnvironmentHandle*  
 [Input] L'handle di ambiente del pool.  
  
 *PoolID*  
 [Input] Il pool associato l'ID del pool che è stato verificato il timeout.  
  
## <a name="returns"></a>Valori di codice restituiti  
 SQL_SUCCESS, SQL_SUCCESS_WITH_INFO, SQL_ERROR o SQL_INVALID_HANDLE.  
  
## <a name="diagnostics"></a>Diagnostica  
 Gestione Driver non elaborerà le informazioni di diagnostica restituite da **SQLCleanupConnectionPoolID**.  
  
 Un'applicazione non può ricevere il messaggio di errore restituito dal driver.  
  
## <a name="remarks"></a>Osservazioni  
 **SQLCleanupConnectionPoolID** può essere chiamato in qualsiasi momento, ma gestione Driver garantisce che nessun altro thread consiste nel chiamare contemporaneamente **SQLGetPoolID** e nessun altro thread viene eseguita la chiamata contemporaneamente  **SQLRateConnection** e **SQLPoolConnect** con un token di informazioni di connessione assegnato con tale ID del pool. Pertanto, il driver deve assicurarsi che questa funzione è thread-safe.  
  
 Un driver possibile pulire le risorse associate all'ID del pool.  
  
 Le applicazioni non devono chiamare direttamente questa funzione. Un driver ODBC che supporta il pool di connessioni compatibile con il driver deve implementare questa funzione.  
  
 Includere sqlspi.h per lo sviluppo di driver ODBC.  
  
## <a name="see-also"></a>Vedere anche  
 [Sviluppo di un Driver ODBC](../../../odbc/reference/develop-driver/developing-an-odbc-driver.md)   
 [Pool di connessioni compatibile con il driver](../../../odbc/reference/develop-app/driver-aware-connection-pooling.md)   
 [Sviluppo del rilevamento di pool di connessioni in un driver ODBC](../../../odbc/reference/develop-driver/developing-connection-pool-awareness-in-an-odbc-driver.md)
