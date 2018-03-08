---
title: Errors | Microsoft Docs
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
- OLE/COM errors
- errors [OLE DB]
- OLE DB error handling, about error handling
- OLE DB error handling
ms.assetid: bd0612f4-96ef-4919-b0f9-b5447210fe93
caps.latest.revision: "37"
author: MightyPen
ms.author: genemi
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: fd82c09514ebcfe70c3ea295cc8f9c5236756a49
ms.sourcegitcommit: 9e6a029456f4a8daddb396bc45d7874a43a47b45
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/25/2018
---
# <a name="errors"></a>Errori
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]
[!INCLUDE[SNAC_Deprecated](../../includes/snac-deprecated.md)]

  Gli oggetti OLE/COM segnalano gli errori tramite il codice restituito HRESULT delle funzioni membro oggetto. Un HRESULT OLE/COM è una struttura costituita da pacchetti di byte. OLE fornisce macro che risolvono i riferimenti dei membri di struttura.  
  
 OLE/COM specifica il **IErrorInfo** interfaccia. L'interfaccia espone i metodi, ad esempio **GetDescription**. In questo modo, i client possono estrarre i dettagli relativi agli errori dai server OLE/COM. OLE DB estende **IErrorInfo** da supportare la restituzione di più pacchetti di informazioni di errore nell'esecuzione di una funzione con singolo membro.  
  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] può restituire più errori. Un'applicazione può recuperare gli errori del server uno alla volta chiamando [IMultipleResults:: GetResult](http://go.microsoft.com/fwlink/?LinkId=129630) combinato con ISQLErrorInfo e IErrorRecords.  
  
 Il [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] provider OLE DB Native Client espone OLE DB ottimizzata per i record **IErrorInfo**, personalizzata **ISQLErrorInfo**, specifico del provider e [ISQLServerErrorInfo ](http://msdn.microsoft.com/library/a8323b5c-686a-4235-a8d2-bda43617b3a1) interfacce per oggetti error.  
  
 Per informazioni sulla traccia degli errori, vedere [traccia di accesso ai dati](http://go.microsoft.com/fwlink/?LinkId=125805). Per informazioni sui miglioramenti apportati alla traccia di errori aggiunta in [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)], vedere [l'accesso a informazioni di diagnostica nel Log degli eventi estesi](../../relational-databases/native-client/features/accessing-diagnostic-information-in-the-extended-events-log.md).  
  
## <a name="in-this-section"></a>Contenuto della sezione  
  
-   [Codici restituiti](../../relational-databases/native-client-ole-db-errors/return-codes.md)  
  
-   [Informazioni nelle interfacce di errore](../../relational-databases/native-client-ole-db-errors/information-in-error-interfaces.md)  
  
-   [Dettagli errore SQL Server](../../relational-databases/native-client-ole-db-errors/sql-server-error-detail.md)  
  
-   [Il recupero delle informazioni di errore](../../relational-databases/native-client-ole-db-errors/retrieving-error-information.md)  
  
-   [Risultati dei messaggi di SQL Server](../../relational-databases/native-client-ole-db-errors/sql-server-message-results.md)  
  
## <a name="see-also"></a>Vedere anche  
 [SQL Server Native Client &#40;OLE DB&#41;](../../relational-databases/native-client/ole-db/sql-server-native-client-ole-db.md)  
  
  
