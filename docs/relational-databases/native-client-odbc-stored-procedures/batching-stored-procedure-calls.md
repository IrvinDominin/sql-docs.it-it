---
title: L'invio in batch chiamate alle Stored Procedure | Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- stored procedures [ODBC], batching
- ODBC, stored procedures
- SQL Server Native Client ODBC driver, stored procedures
- batches [ODBC]
- ODBC CALL escape sequence
ms.assetid: b7f53e11-15f0-4602-8134-b166160888f0
author: MightyPen
ms.author: genemi
manager: craigg
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: a19baf0d76c34e58e9cb4c9f73a0f77bbb47e7c6
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/01/2018
ms.locfileid: "47633226"
---
# <a name="batching-stored-procedure-calls"></a>Invio in batch di chiamate a stored procedure
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]
[!INCLUDE[SNAC_Deprecated](../../includes/snac-deprecated.md)]

  Il [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] driver ODBC Native Client invia automaticamente in batch chiamate a stored procedure nel server quando appropriato. Il driver effettua questa operazione solo quando viene utilizzata la sequenza di escape e non per l'istruzione [!INCLUDE[tsql](../../includes/tsql-md.md)] EXECUTE. L'invio in batch di chiamate a stored procedure può ridurre il numero di round trip al server e migliorare significativamente le prestazioni.  
  
 Il driver invia in batch al server le chiamate alle procedure quando si esegue un batch che contiene più sequenze di escape ODBC CALL. Invia inoltre in batch chiamate alle procedure quando si utilizzano matrici di parametri associati con una sequenza di escape ODBC CALL. Ad esempio, se si usa l'associazione di parametri per riga o per associare una matrice con cinque elementi ai parametri di un'istruzione SQL ODBC CALL, quando **SQLExecute** oppure **SQLExecDirect** viene chiamato, il driver invia un singolo batch con cinque chiamate di procedura al server.  
  
## <a name="see-also"></a>Vedere anche  
 [Esecuzione delle stored procedure](../../relational-databases/native-client-odbc-stored-procedures/running-stored-procedures.md)  
  
  
