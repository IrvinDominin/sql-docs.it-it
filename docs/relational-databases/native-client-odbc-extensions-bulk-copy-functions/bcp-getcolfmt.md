---
title: bcp_getcolfmt | Microsoft Docs
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.service: 
ms.component: native-client-odbc-extensions-bulk-copy-functions
ms.reviewer: 
ms.suite: sql
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: reference
apiname: bcp_getcolfmt
apilocation: sqlncli11.dll
apitype: DLLExport
helpviewer_keywords: bcp_getcolfmt function
ms.assetid: f8bdada5-7b2d-4475-8c98-f93e9d77b130
caps.latest.revision: "36"
author: MightyPen
ms.author: genemi
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 642290f1093c1f0730417e4bcbed259322c3e630
ms.sourcegitcommit: a0aa5e611a0e6ebb74ac1e2f613e8916dc7a7617
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/24/2018
---
# <a name="bcpgetcolfmt"></a>bcp_getcolfmt
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]
[!INCLUDE[SNAC_Deprecated](../../includes/snac-deprecated.md)]

  Utilizzato per trovare il valore della proprietà di formato di colonna.  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
RETCODE bcp_getcolfmt (  
        HDBC hdbc,  
        INT field,  
        INT property,  
        void* pValue,  
        INT cbvalue,  
        INT* pcbLen);  
```  
  
## <a name="arguments"></a>Argomenti  
 *HDBC*  
 Handle di connessione ODBC abilitato per la copia bulk.  
  
 *field*  
 Numero di colonna per cui viene recuperata la proprietà.  
  
 *proprietà*  
 Una delle costanti di proprietà.  
  
 *pValue*  
 Puntatore al buffer dal quale recuperare il valore della proprietà.  
  
 *cbValue*  
 Lunghezza in byte del buffer delle proprietà.  
  
 *pcbLen*  
 IIndicatore di misura relativo alla lunghezza dei dati restituiti nel buffer delle proprietà.  
  
## <a name="returns"></a>Valori di codice restituiti  
 SUCCEED o FAIL.  
  
## <a name="remarks"></a>Osservazioni  
 Valori di proprietà di formato di colonna sono elencati nel [bcp_setcolfmt](../../relational-databases/native-client-odbc-extensions-bulk-copy-functions/bcp-setcolfmt.md) argomento. I valori di proprietà formato di colonna vengono impostati chiamando la **bcp_setcolfmt** funzione e **bcp_getcolfmt** funzione viene utilizzata per trovare il valore di proprietà di formato di colonna.  
  
 Modifiche di comportamento possono essere osservate durante la connessione a un [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] (o versione successiva) il computer server, rispetto alle versioni [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] versioni. Per ulteriori informazioni, vedere [Metadata Discovery](../../relational-databases/native-client/features/metadata-discovery.md).  
  
## <a name="bcpgetcolfmt-support-for-enhanced-date-and-time-features"></a>Supporto di bcp_getcolfmt per le caratteristiche avanzate di data e ora  
 I tipi utilizzati con il **BCP_FMT_TYPE** sono di proprietà per i tipi di data/ora come specificato in [modifiche di copia Bulk per avanzate di data e ora tipi &#40; OLE DB e ODBC &#41;](../../relational-databases/native-client-odbc-date-time/bulk-copy-changes-for-enhanced-date-and-time-types-ole-db-and-odbc.md).  
  
 Per ulteriori informazioni, vedere [data e ora miglioramenti &#40; ODBC &#41;](../../relational-databases/native-client-odbc-date-time/date-and-time-improvements-odbc.md).  
  
## <a name="see-also"></a>Vedere anche  
 [Funzioni di copia bulk](../../relational-databases/native-client-odbc-extensions-bulk-copy-functions/sql-server-driver-extensions-bulk-copy-functions.md)  
  
  
