---
title: Risultati dei messaggi di SQL Server | Documenti Microsoft
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.service: 
ms.component: native-client-ole-db-errors
ms.reviewer: 
ms.suite: sql
ms.technology: 
ms.tgt_pltfrm: 
ms.topic: reference
helpviewer_keywords:
- SQL Server Native Client OLE DB provider, errors
- errors [OLE DB], SQL Server message results
- OLE DB error handling, SQL Server message results
ms.assetid: 6663c6f9-def1-4d9e-845b-2085e5efc401
caps.latest.revision: "29"
author: MightyPen
ms.author: genemi
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: f5a8aa363b7a60da6dbc67fdf6cdc7ef8059ec88
ms.sourcegitcommit: 9e6a029456f4a8daddb396bc45d7874a43a47b45
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/25/2018
---
# <a name="sql-server-message-results"></a>Risultati dei messaggi di SQL Server
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]
[!INCLUDE[SNAC_Deprecated](../../includes/snac-deprecated.md)]

  Nell'esempio [!INCLUDE[tsql](../../includes/tsql-md.md)] non generano istruzioni [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] set di righe del provider OLE DB Native Client o un conteggio delle righe interessate durante l'esecuzione:  
  
-   PRINT  
  
-   RAISERROR con gravità minore o uguale a 10  
  
-   DBCC  
  
-   SET SHOWPLAN  
  
-   SET STATISTICS  
  
 Queste istruzioni restituiscono uno o più messaggi informativi o determinano la restituzione da parte di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] di messaggi informativi in sostituzione dei risultati del conteggio o del set di righe. Al completamento dell'esecuzione, il [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] provider OLE DB Native Client restituisce S_OK e i messaggi sono disponibili per il [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] consumer del provider OLE DB Native Client.  
  
 Il [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] provider OLE DB Native Client restituisce S_OK e include uno o più messaggi informativi disponibili dopo l'esecuzione di molte [!INCLUDE[tsql](../../includes/tsql-md.md)] istruzioni o l'esecuzione del consumer di un [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] funzione membro del provider OLE DB Native Client.  
  
 Il [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] consumer del provider OLE DB Native Client che consente la specifica dinamica del testo della query deve verificare le interfacce di errore dopo ogni esecuzione della funzione membro indipendentemente dal valore del codice restituito, la presenza o assenza di un tipo restituito **IRowset** o **IMultipleResults** riferimento all'interfaccia o un numero di righe interessate.  
  
## <a name="see-also"></a>Vedere anche  
 [errori](../../relational-databases/native-client-ole-db-errors/errors.md)  
  
  
