---
title: Creazione di un'applicazione di SQL Server Native Client OLE DB Provider | Documenti Microsoft
ms.custom: 
ms.date: 03/17/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.service: 
ms.component: native-client-ole-db-provider
ms.reviewer: 
ms.suite: sql
ms.technology: 
ms.tgt_pltfrm: 
ms.topic: reference
helpviewer_keywords:
- SQL Server Native Client OLE DB provider, application creation
- applications [SQL Server Native Client]
- OLE DB, creating applications
ms.assetid: f3ae6815-f32d-4913-a1a2-2ba2f20cfd88
caps.latest.revision: "31"
author: MightyPen
ms.author: genemi
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 68fb2398633deb91e596e46170e87606345ca236
ms.sourcegitcommit: 9e6a029456f4a8daddb396bc45d7874a43a47b45
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/25/2018
---
# <a name="creating-a-sql-server-native-client-ole-db-provider-application"></a>Creazione di un'applicazione del provider OLE DB di SQL Server Native Client
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]
[!INCLUDE[SNAC_Deprecated](../../includes/snac-deprecated.md)]

  Creazione di un [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] applicazione del provider OLE DB Native Client implica questi passaggi:  
  
1.  Avvio di una connessione a un'origine dati.  
  
2.  Esecuzione di un comando.  
  
3.  Elaborazione dei risultati.  
  
> [!NOTE]  
>  Se possibile, usare l'autenticazione di Windows. Se non è disponibile, agli utenti verrà richiesto di immettere le credenziali in fase di esecuzione. Evitare di archiviare le credenziali in un file. Se è necessario rendere persistenti le credenziali, è consigliabile crittografarle utilizzando [cryptoAPI Win32](http://go.microsoft.com/fwlink/?LinkId=9504).  
  
## <a name="in-this-section"></a>Argomenti della sezione  
  
-   [Stabilire una connessione a un'origine dati](../../relational-databases/native-client-ole-db-provider/establishing-a-connection-to-a-data-source.md)  
  
-   [Esegue un comando](../../relational-databases/native-client-ole-db-provider/executing-a-command.md)  
  
-   [Elaborazione dei risultati](../../relational-databases/native-client-ole-db-provider/processing-results.md)  
  
-   [Sulle proprietà OLE DB](../../relational-databases/native-client-ole-db-provider/about-ole-db-properties.md)  
  
-   [Utilizzo della clausola OUTPUT con OLE DB in SQL Server Native Client](../../relational-databases/native-client-ole-db-provider/using-the-output-clause-with-ole-db-in-sql-server-native-client.md)  
  
## <a name="see-also"></a>Vedere anche  
 [SQL Server Native Client &#40;OLE DB&#41;](../../relational-databases/native-client/ole-db/sql-server-native-client-ole-db.md)  
  
  
