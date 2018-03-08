---
title: Test della connessione ODBC | Documenti Microsoft
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.service: 
ms.component: odbc
ms.reviewer: 
ms.suite: sql
ms.technology: drivers
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- testing connections [ODBC]
- ODBC driver for Oracle [ODBC], testing connections
ms.assetid: 5e671665-2aba-49a7-8871-70784d8b3cc9
caps.latest.revision: "8"
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: cffb08b48128500b37c6f55e37a848be19c266a8
ms.sourcegitcommit: cc71f1027884462c359effb898390c8d97eaa414
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/21/2017
---
# <a name="testing-the-odbc-connection"></a>Test della connessione ODBC
> [!IMPORTANT]  
>  Questa funzionalità verrà rimossa in una versione futura di Windows. Evitare di usare questa funzionalità in un nuovo progetto di sviluppo e prevedere interventi di modifica nelle applicazioni in cui è attualmente implementata. In alternativa, utilizzare il driver ODBC fornito da Oracle.  
  
 Quando la risoluzione dei problemi di accesso ODBC per Oracle 7. x e server Oracle8 RDBMS, potrebbe essere necessario verificare che il codice sottostante SQL * Net e schede di protocollo Oracle siano installate correttamente. A tale scopo, utilizzare l'utilità Oracle fornito Nettest.exe nella directory Orawin\Bin.  
  
 Nettest è un'utilità semplice che tenta di accedere al server selezionato tramite solo installato SQL * Net software che fa parte del client Oracle. L'utilità richiederà l'immissione di un nome di account di accesso, la password e TNS stringa di connessione. Se il client Oracle sia installato correttamente, l'utilità visualizzerà semplicemente "Ping riuscito". Se l'account di accesso non è riuscita, è necessario rivolgersi a un amministratore del database.
