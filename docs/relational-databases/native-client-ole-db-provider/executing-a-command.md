---
title: Esegue un comando | Documenti Microsoft
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
- commands [SQL Server Native Client]
- OLE DB, executing commands
- sessions [SQL Server Native Client]
- OLE DB extensions for XML
- SQL Server Native Client OLE DB provider, command execution
ms.assetid: bb0b3cbf-fe45-46ba-b2ec-c5a39e3c7081
caps.latest.revision: "40"
author: MightyPen
ms.author: genemi
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 495f632181ec7697c08002684e2f6e77f272d39a
ms.sourcegitcommit: 9e6a029456f4a8daddb396bc45d7874a43a47b45
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/25/2018
---
# <a name="executing-a-command"></a>Esecuzione di un comando
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]
[!INCLUDE[SNAC_Deprecated](../../includes/snac-deprecated.md)]

  Dopo aver stabilita la connessione a un'origine dati, il consumer chiama il **IDBCreateSession::CreateSession** metodo per creare una sessione. La sessione funge da comando, set di righe o factory di transazioni.  
  
 Per lavorare direttamente con le singole tabelle o indici, il consumer richiede il **IOpenRowset** interfaccia. Il **IOpenRowset::OPENROWSET** metodo apre e restituisce un set di righe che include tutte le righe da una singola tabella di base o un indice.  
  
 Per eseguire un comando (ad esempio SELECT \* FROM Authors), il consumer richiede il **IDBCreateCommand** interfaccia. Il consumer può eseguire il **IDBCreateCommand::CreateCommand** metodo per creare un oggetto comando e richiedere il **ICommandText** interfaccia. Il **ICommandText::SetCommandText** consente di specificare il comando che deve essere eseguito.  
  
 Il **Execute** comando viene utilizzato per eseguire il comando. Il comando può essere qualsiasi nome di istruzione o di procedura SQL. Non tutti i comandi producono un oggetto set di risultati (set di righe). Comandi come SELECT * FROM Authors producono un set di risultati.  
  
## <a name="see-also"></a>Vedere anche  
 [Creazione di un'applicazione del Provider SQL Server Native Client OLE DB](../../relational-databases/native-client-ole-db-provider/creating-a-sql-server-native-client-ole-db-provider-application.md)  
  
  
