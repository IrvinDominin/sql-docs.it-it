---
title: bcp_readfmt | Microsoft Docs
ms.custom: 
ms.date: 03/06/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.service: 
ms.component: native-client-odbc-extensions-bulk-copy-functions
ms.reviewer: 
ms.suite: sql
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: reference
apiname: bcp_readfmt
apilocation: sqlncli11.dll
apitype: DLLExport
helpviewer_keywords: bcp_readfmt function
ms.assetid: 654001c8-ae9f-425c-b820-f0191bf89367
caps.latest.revision: "35"
author: MightyPen
ms.author: genemi
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: a41672417cc9c7b34c23f4edceb9d404c0162147
ms.sourcegitcommit: a0aa5e611a0e6ebb74ac1e2f613e8916dc7a7617
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/24/2018
---
# <a name="bcpreadfmt"></a>bcp_readfmt
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]
[!INCLUDE[SNAC_Deprecated](../../includes/snac-deprecated.md)]

  Legge una definizione di formato di file di dati dal file di formato specificato.  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
RETCODE bcp_readfmt (  
        HDBC hdbc,  
        LPCTSTR szFormatFile);  
```  
  
## <a name="arguments"></a>Argomenti  
 *HDBC*  
 Handle di connessione ODBC abilitato per la copia bulk.  
  
 *szFormatFile*  
 Percorso e nome del file contenente i valori di formato per il file di dati.  
  
## <a name="returns"></a>Valori di codice restituiti  
 SUCCEED o FAIL.  
  
## <a name="remarks"></a>Osservazioni  
 Dopo aver **bcp_readfmt** legge i valori di formato, effettua le chiamate appropriate a [bcp_columns](../../relational-databases/native-client-odbc-extensions-bulk-copy-functions/bcp-columns.md) e [bcp_colfmt](../../relational-databases/native-client-odbc-extensions-bulk-copy-functions/bcp-colfmt.md). L'utente può evitare di analizzare un file di formato ed effettuare queste chiamate.  
  
 Per rendere persistente un file di formato, chiamare [bcp_writefmt](../../relational-databases/native-client-odbc-extensions-bulk-copy-functions/bcp-writefmt.md). Le chiamate a **bcp_readfmt** può fare riferimento a formati salvati. Per ulteriori informazioni, vedere [bcp_init](../../relational-databases/native-client-odbc-extensions-bulk-copy-functions/bcp-init.md).  
  
 In alternativa, l'utilità di copia bulk (**bcp**) può salvare i formati di dati definito dall'utente nei file che possono fare riferimento **bcp_readfmt**. Per ulteriori informazioni sul **bcp** utilità e la struttura di **bcp** i file di formato di dati, vedere [importazione in blocco e l'esportazione di dati &#40; SQL Server &#41; ](../../relational-databases/import-export/bulk-import-and-export-of-data-sql-server.md).  
  
 Il **BCPDELAYREADFMT** valore il *eOption* parametro di [bcp_control](../../relational-databases/native-client-odbc-extensions-bulk-copy-functions/bcp-control.md) modifica il comportamento di bcp_readfmt.  
  
> [!NOTE]  
>  Il file di formato è stato prodotto dalla versione 4.2 o versioni successive del componente di **bcp** utilità.  
  
## <a name="example"></a>Esempio  
  
```  
// Variables like henv not specified.  
HDBC      hdbc;  
DBINT      nRowsProcessed;  
  
// Application initiation, get an ODBC environment handle, allocate the  
// hdbc, and so on.  
...   
  
// Enable bulk copy prior to connecting on allocated hdbc.  
SQLSetConnectAttr(hdbc, SQL_COPT_SS_BCP, (SQLPOINTER) SQL_BCP_ON,  
   SQL_IS_INTEGER);  
  
// Connect to the data source, return on error.  
if (!SQL_SUCCEEDED(SQLConnect(hdbc, _T("myDSN"), SQL_NTS,  
   _T("myUser"), SQL_NTS, _T("myPwd"), SQL_NTS)))  
   {  
   // Raise error and return.  
   return;  
   }  
  
// Initialize bulk copy.   
if (bcp_init(hdbc, _T("myTable"), _T("myData.csv"),  
   _T("myErrors"),    DB_IN) == FAIL)  
   {  
   // Raise error and return.  
   return;  
   }  
  
if (bcp_readfmt(hdbc, _T("myFmtFile.fmt")) == FAIL)  
   {  
   // Raise error and return.  
   return;  
   }  
  
if (bcp_exec(hdbc, &nRowsProcessed) == SUCCEED)  
   {  
   cout << nRowsProcessed << " rows copied to SQL Server\n";  
   }  
  
// Carry on.  
```  
  
## <a name="see-also"></a>Vedere anche  
 [Funzioni di copia bulk](../../relational-databases/native-client-odbc-extensions-bulk-copy-functions/sql-server-driver-extensions-bulk-copy-functions.md)  
  
  
