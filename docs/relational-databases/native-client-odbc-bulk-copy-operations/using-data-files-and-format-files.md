---
title: Utilizzo di file di dati e i file di formato | Documenti Microsoft
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.service: 
ms.component: native-client-odbc-bulk-copy-operations
ms.reviewer: 
ms.suite: sql
ms.technology: 
ms.tgt_pltfrm: 
ms.topic: reference
helpviewer_keywords:
- bulk copy [ODBC], file formats
- ODBC, functions
- SQL Server Native Client ODBC driver, bulk copy
- bulk copy [SQL Server Native Client]
- ODBC, bulk copy operations
- bulk copy [ODBC], data files
ms.assetid: c01b7155-3f0a-473d-90b7-87a97bc56ca5
caps.latest.revision: "30"
author: MightyPen
ms.author: genemi
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 423619a7d1a9a7b80cfab796f5c4a85969b3e167
ms.sourcegitcommit: 9e6a029456f4a8daddb396bc45d7874a43a47b45
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/25/2018
---
# <a name="using-data-files-and-format-files"></a>Utilizzo di file di dati e file di formato
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]
[!INCLUDE[SNAC_Deprecated](../../includes/snac-deprecated.md)]

  Il programma per la copia bulk più semplice effettua le operazioni seguenti:  
  
1.  Chiamate [bcp_init](../../relational-databases/native-client-odbc-extensions-bulk-copy-functions/bcp-init.md) per specificare la copia di massa (impostare BCP_OUT) da una tabella o vista in un file di dati.  
  
2.  Chiamate [bcp_exec](../../relational-databases/native-client-odbc-extensions-bulk-copy-functions/bcp-exec.md) per eseguire l'operazione di copia bulk.  
  
 Poiché il file di dati viene creato in modalità nativa, i dati di tutte le colonne nella tabella o nella vista vengono archiviati nel file di dati con lo stesso formato utilizzato nel database. Il file può essere quindi oggetto di copia bulk in un server utilizzando questi stessi passaggi e impostando DB_IN anziché DB_OUT. È possibile procedere in questo modo solo se le tabelle di origine e di destinazione hanno una struttura identica. Il file di dati risultante può essere immesso anche il **bcp** utilità utilizzando il  **/n**  switch (modalità nativa).  
  
 Per eseguire la copia bulk dal set di risultati di un'istruzione [!INCLUDE[tsql](../../includes/tsql-md.md)] anziché direttamente da una tabella o una vista:  
  
1.  Chiamare **bcp_init** per specificare la copia di massa, ma specificare NULL per il nome della tabella.  
  
2.  Chiamare [bcp_control](../../relational-databases/native-client-odbc-extensions-bulk-copy-functions/bcp-control.md) con *eOption* impostato su BCPHINTS e *iValue* impostato su un puntatore a una stringa SQLTCHAR contenente l'istruzione Transact-SQL.  
  
3.  Chiamare **bcp_exec** per eseguire l'operazione di copia bulk.  
  
 L'istruzione [!INCLUDE[tsql](../../includes/tsql-md.md)] può essere qualsiasi istruzione che genera un set di risultati. Il file di dati creato contiene il primo set di risultati dell'istruzione [!INCLUDE[tsql](../../includes/tsql-md.md)]. Nella copia bulk viene ignorato qualsiasi set di risultati successivo al primo se tramite l'istruzione [!INCLUDE[tsql](../../includes/tsql-md.md)] vengono generati più set di risultati.  
  
 Per creare un file di dati nella colonna da cui i dati vengono archiviati in un formato diverso da quello della tabella, chiamare [bcp_columns](../../relational-databases/native-client-odbc-extensions-bulk-copy-functions/bcp-columns.md) per specificare quante colonne verranno modificate, quindi chiamare [bcp_colfmt](../../relational-databases/native-client-odbc-extensions-bulk-copy-functions/bcp-colfmt.md) per ogni colonna il cui formato si desidera modificare. Questa operazione viene eseguita dopo la chiamata **bcp_init** ma prima di chiamare **bcp_exec**. **bcp_colfmt** specifica il formato in cui i dati della colonna sono archiviati nel file di dati. e può essere utilizzato quando esegue una copia bulk interna o esterna. È inoltre possibile utilizzare **bcp_colfmt** per impostare i caratteri di terminazione di riga e colonna. Ad esempio, se i dati non contengono caratteri di tabulazione, è possibile creare un file delimitato da tabulazioni utilizzando **bcp_colfmt** per impostare il carattere di tabulazione come carattere di terminazione per ogni colonna.  
  
 Quando si esegue bulk copia e l'utilizzo **bcp_colfmt**, è possibile creare facilmente un file di formato che descriva il file di dati creato chiamando [bcp_writefmt](../../relational-databases/native-client-odbc-extensions-bulk-copy-functions/bcp-writefmt.md) dopo l'ultima chiamata a **bcp_colfmt**.  
  
 Quando si esegue la copia bulk da un file di dati descritto da un file di formato, leggere il file di formato chiamando [bcp_readfmt](../../relational-databases/native-client-odbc-extensions-bulk-copy-functions/bcp-readfmt.md) dopo **bcp_init** ma prima **bcp_exec**.  
  
 Il **bcp_control** funzione controlla diverse opzioni durante la copia bulk in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] da un file di dati. **bcp_control** imposta le opzioni, ad esempio il numero massimo di errori prima della chiusura, la riga nel file in cui iniziare la copia di massa, la riga di arresto in e le dimensioni del batch.  
  
## <a name="see-also"></a>Vedere anche  
 [Esecuzione di operazioni di copia Bulk &#40; ODBC &#41;](../../relational-databases/native-client-odbc-bulk-copy-operations/performing-bulk-copy-operations-odbc.md)  
  
  
