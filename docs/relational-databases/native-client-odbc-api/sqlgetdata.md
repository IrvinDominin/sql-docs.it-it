---
title: SQLGetData | Microsoft Docs
ms.custom: 
ms.date: 03/17/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.service: 
ms.component: native-client-odbc-api
ms.reviewer: 
ms.suite: sql
ms.technology: 
ms.tgt_pltfrm: 
ms.topic: reference
apitype: DLLExport
helpviewer_keywords: SQLGetData function
ms.assetid: 204848be-8787-45b4-816f-a60ac9d56fcf
caps.latest.revision: "42"
author: MightyPen
ms.author: genemi
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 4e738c8b3f4c2200287a7c4dc9578951e90c8dd8
ms.sourcegitcommit: a0aa5e611a0e6ebb74ac1e2f613e8916dc7a7617
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/24/2018
---
# <a name="sqlgetdata"></a>SQLGetData
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]
[!INCLUDE[SNAC_Deprecated](../../includes/snac-deprecated.md)]

  **SQLGetData** viene utilizzato per recuperare i dati del set di risultati senza associare valori della colonna. **SQLGetData** può essere successivamente chiamato sulla stessa colonna per recuperare grandi quantità di dati da una colonna con un **testo**, **ntext**, o **immagine** tipo di dati .  
  
 Non è necessario che un'applicazione associ le variabili per recuperare i dati del set di risultati. I dati di qualsiasi colonna possono essere recuperati dal [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] driver ODBC Native Client utilizzando **SQLGetData**.  
  
 Il [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] driver ODBC Native Client non supporta l'utilizzo **SQLGetData** per recuperare i dati in ordine di colonne casuale. Tutte le colonne non associate elaborate con **SQLGetData** deve avere gli ordinali di colonna maggiore rispetto alle colonne associate nel set di risultati. L'applicazione deve elaborare i dati dal valore della colonna dell'ordinale non associato più basso al più elevato. Il tentativo di recuperare dati dalla colonna con una numerazione di ordinali più bassa genera un errore. Se l'applicazione sta utilizzando i cursori del server per indicare le righe del set di risultati, può recuperare nuovamente la riga corrente e quindi recuperare il valore di una colonna. Se un'istruzione viene eseguita sul cursore forward-only in sola lettura predefinito, sarà necessario eseguire nuovamente l'istruzione backup **SQLGetData**.  
  
 Il [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] driver ODBC Native Client riporta in maniera accurata la lunghezza di **testo**, **ntext**, e **immagine** dati recuperati tramite **SQLGetData** . L'applicazione può sfruttare il *StrLen_or_IndPtr* parametro restituito per recuperare rapidamente i dati di tipo long.  
  
> [!NOTE]  
>  Per i tipi di valori di grandi dimensioni, *StrLen_or_IndPtr* restituirà SQL_NO_TOTAL nei casi di troncamento dei dati.  
  
## <a name="sqlgetdata-support-for-enhanced-date-and-time-features"></a>Supporto di SQLGetData per le caratteristiche avanzate di data e ora  
 Valori di colonna di risultati dei tipi di data/ora vengono convertiti come descritto in [le conversioni da SQL a C](../../relational-databases/native-client-odbc-date-time/datetime-data-type-conversions-from-sql-to-c.md).  
  
 Per ulteriori informazioni, vedere [data e ora miglioramenti &#40; ODBC &#41;](../../relational-databases/native-client-odbc-date-time/date-and-time-improvements-odbc.md).  
  
## <a name="sqlgetdata-support-for-large-clr-udts"></a>Supporto di SQLGetData per tipi definiti dall'utente CLR di grandi dimensioni  
 **SQLGetData** supporta i tipi CLR grandi dimensioni definito dall'utente (UDT). Per ulteriori informazioni, vedere [Large CLR User-Defined tipi &#40; ODBC &#41;](../../relational-databases/native-client/odbc/large-clr-user-defined-types-odbc.md).  
  
## <a name="example"></a>Esempio  
  
```  
SQLHDBC     hDbc = NULL;  
SQLHSTMT    hStmt = NULL;  
long        lEmpID;  
PBYTE       pPicture;  
SQLINTEGER  pIndicators[2];  
  
// Get an environment, connection, and so on.  
...  
  
// Get a statement handle and execute a command.  
SQLAllocHandle(SQL_HANDLE_STMT, hDbc, &hStmt);  
  
if (SQLExecDirect(hStmt,  
    (SQLCHAR*) "SELECT EmployeeID, Photo FROM Employees",  
    SQL_NTS) == SQL_ERROR)  
    {  
    // Handle error and return.  
    }  
  
// Retrieve data from row set.  
SQLBindCol(hStmt, 1, SQL_C_LONG, (SQLPOINTER) &lEmpID, sizeof(long),  
    &pIndicators[0]);  
  
while (SQLFetch(hStmt) == SQL_SUCCESS)  
    {  
    cout << "EmployeeID: " << lEmpID << "\n";  
  
    // Call SQLGetData to determine the amount of data that's waiting.  
    if (SQLGetData(hStmt, 2, SQL_C_BINARY, pPicture, 0, &pIndicators[1])  
        == SQL_SUCCESS_WITH_INFO)  
        {  
        cout << "Photo size: " pIndicators[1] << "\n\n";  
  
        // Get all the data at once.  
        pPicture = new BYTE[pIndicators[1]];  
        if (SQLGetData(hStmt, 2, SQL_C_DEFAULT, pPicture,  
            pIndicators[1], &pIndicators[1]) != SQL_SUCCESS)  
            {  
            // Handle error and continue.  
            }  
  
        delete [] pPicture;  
        }  
    else  
        {  
        // Handle error on attempt to get data length.  
        }  
    }  
```  
  
## <a name="see-also"></a>Vedere anche  
 [Funzione SQLGetData](http://go.microsoft.com/fwlink/?LinkId=59350)   
 [Dettagli di implementazione di API ODBC](../../relational-databases/native-client-odbc-api/odbc-api-implementation-details.md)  
  
  
