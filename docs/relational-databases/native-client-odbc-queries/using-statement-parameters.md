---
title: Utilizzando i parametri dell'istruzione | Documenti Microsoft
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.service: 
ms.component: native-client-odbc-queries
ms.reviewer: 
ms.suite: sql
ms.technology: 
ms.tgt_pltfrm: 
ms.topic: reference
helpviewer_keywords:
- SQL Server Native Client ODBC driver, parameters
- parameters [SQL Server Native Client], ODBC
- ODBC, parameters
- statements [ODBC], parameters
- parameter markers [ODBC]
- SQL Server Native Client ODBC driver, statements
- ODBC applications, statements
ms.assetid: 2427d886-ec6c-49d7-b0b6-0d998b64cdb9
caps.latest.revision: "33"
author: MightyPen
ms.author: genemi
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 7e1edf1334f8691cfb6edb3251bb2e3c5ac8737e
ms.sourcegitcommit: 9e6a029456f4a8daddb396bc45d7874a43a47b45
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/25/2018
---
# <a name="using-statement-parameters"></a>Utilizzo dei parametri delle istruzioni
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]
[!INCLUDE[SNAC_Deprecated](../../includes/snac-deprecated.md)]

  Un parametro è una variabile in un'istruzione SQL che consente a un'applicazione ODBC di:  
  
-   Fornire in modo efficiente valori per le colonne di una tabella.  
  
-   Migliorare l'interazione dell'utente nella costruzione di criteri di query.  
  
-   Gestire **testo**, **ntext**, e **immagine** dati e [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-tipi di dati C specifici.  
  
 Ad esempio, un **parti** tabella include colonne denominate **PartID**, **descrizione**, e **prezzo**. Per aggiungere una parte senza parametri, è necessario costruire un'istruzione SQL come:  
  
```  
INSERT INTO Parts (PartID, Description, Price) VALUES (2100, 'Drive shaft', 50.00)  
```  
  
 Sebbene questa istruzione sia accettabile per l'inserimento di una riga con un set di valori noto, non risulta particolarmente efficace quando un'applicazione richiede l'inserimento di diverse righe. In ODBC il problema viene risolto consentendo a un'applicazione di sostituire qualsiasi valore dei dati in un'istruzione SQL con un marcatore di parametro, rappresentato da un punto interrogativo (?). Nell'esempio seguente tre valori di dati vengono sostituiti con marcatori di parametro:  
  
```  
INSERT INTO Parts (PartID, Description, Price) VALUES (?, ?, ?)  
```  
  
 Gli indicatori di parametro vengono quindi associati a variabili dell'applicazione. Per inserire una nuova riga, l'applicazione deve solo impostare i valori delle variabili ed eseguire l'istruzione. Il driver recupera quindi i valori correnti delle variabili e li invia all'origine dati. Se l'istruzione viene eseguita più volte, l'applicazione può rendere ancora più efficiente il processo preparando l'istruzione.  
  
 A ogni marcatore di parametro è associato il numero ordinale assegnato ai parametri, da sinistra verso destra. Il marcatore di parametro all'estrema sinistra in un'istruzione SQL presenta un valore ordinale pari a 1, il successivo è l'ordinale 2 e così via.  
  
## <a name="in-this-section"></a>Contenuto della sezione  
  
-   [Parametri di associazione](../../relational-databases/native-client-odbc-queries/using-statement-parameters-binding-parameters.md)  
  
## <a name="see-also"></a>Vedere anche  
 [L'esecuzione di query &#40; ODBC &#41;](../../relational-databases/native-client-odbc-queries/executing-queries-odbc.md)  
  
  
