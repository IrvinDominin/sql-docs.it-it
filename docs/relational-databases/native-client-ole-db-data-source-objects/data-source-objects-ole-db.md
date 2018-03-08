---
title: Oggetti (OLE DB) dell'origine dati | Documenti Microsoft
ms.custom: 
ms.date: 03/16/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.service: 
ms.component: native-client-ole-db-data-source-objects
ms.reviewer: 
ms.suite: sql
ms.technology: 
ms.tgt_pltfrm: 
ms.topic: reference
helpviewer_keywords:
- data access [SQL Server Native Client], data source objects
- SQL Server Native Client, data source objects
- SQLNCLI, data source objects
- SQL Server Native Client OLE DB provider, data source objects
- OLE DB data source objects [SQL Server Native Client]
- data source objects [OLE DB]
- CLSID
ms.assetid: c1d4ed20-ad3b-4e33-a26b-38d7517237b7
caps.latest.revision: "33"
author: MightyPen
ms.author: genemi
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 7f20bf4aee0befa6fb3439da84eef1a04e8ac04a
ms.sourcegitcommit: 9e6a029456f4a8daddb396bc45d7874a43a47b45
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/25/2018
---
# <a name="data-source-objects-ole-db"></a>Oggetti origine dati (OLE DB)
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]
[!INCLUDE[SNAC_Deprecated](../../includes/snac-deprecated.md)]

  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]Native Client utilizza il termine origine dati per il set di interfacce di OLE DB utilizzato per stabilire un collegamento a un archivio dati, ad esempio [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Creazione di un'istanza dell'oggetto di origine dati del provider è la prima attività di un [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] consumer Native Client.  
  
 Ogni provider OLE DB dichiara un identificatore di classe (CLSID) per se stesso. Il CLSID per il [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] provider OLE DB Native Client è il CLSID_SQLNCLI10 GUID C/C++ (il simbolo SQLNCLI_CLSID risolverà il corretto progid nel file che si fa riferimento a SQLNCLI. h). Con il CLSID, il consumer utilizza OLE **CoCreateInstance** funzione per produrre un'istanza dell'oggetto di origine dati.  
  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]Native Client è un server in-process. Le istanze di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] gli oggetti di provider OLE DB Native Client vengono creati utilizzando la macro CLSCTX_INPROC_SERVER per indicare che il contesto eseguibile.  
  
 Il [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] oggetto origine dati del provider OLE DB Native Client espone le interfacce di inizializzazione OLE DB che consentono al consumer di connettersi a esistente [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] database.  
  
 Ogni connessione eseguita tramite il [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] provider OLE DB Native Client imposta automaticamente queste opzioni:  
  
-   SET ANSI_WARNINGS ON  
  
-   SET ANSI_NULLS ON  
  
-   SET ANSI_PADDING ON  
  
-   SET ANSI_NULL_DFLT_ON ON  
  
-   SET QUOTED_IDENTIFIER ON  
  
-   SET CONCAT_OF_NULL_YIELDS_NULL ON  
  
 Nell'esempio viene utilizzata la macro dell'identificatore di classe per creare un [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] oggetto origine di dati del provider OLE DB Native Client e ottenere un riferimento al relativo **IDBInitialize** interfaccia.  
  
```  
IDBInitialize*   pIDBInitialize;  
HRESULT          hr;  
  
hr = CoCreateInstance(CLSID_SQLNCLI10, NULL, CLSCTX_INPROC_SERVER,  
    IID_IDBInitialize, (void**) &pIDBInitialize);  
  
if (SUCCEEDED(hr))  
{  
    //  Perform necessary processing with the interface.  
    pIDBInitialize->Uninitialize();  
    pIDBInitialize->Release();  
}  
else  
{  
    // Display error from CoCreateInstance.  
}  
```  
  
 Seguito alla creazione di un'istanza di un [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] oggetto origine dati del provider OLE DB Native Client, l'applicazione consumer può proseguire inizializzando l'origine dati e creando sessioni. Le sessioni OLE DB presentano le interfacce che consentono l'accesso ai dati e la relativa modifica.  
  
 Il [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] provider OLE DB Native Client crea la prima connessione a un'istanza specificata di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] come parte di un'inizializzazione dell'origine dati ha esito positivo. La connessione viene mantenuta, purché venga mantenuto un riferimento in alcuna interfaccia di inizializzazione di origine dati o fino a quando il **IDBInitialize:: UnInitialize** metodo viene chiamato.  
  
## <a name="in-this-section"></a>Argomenti della sezione  
  
-   [Proprietà dell'origine dati &#40; OLE DB &#41;](../../relational-databases/native-client-ole-db-data-source-objects/data-source-properties-ole-db.md)  
  
-   [Proprietà delle informazioni di origine dati](../../relational-databases/native-client-ole-db-data-source-objects/data-source-information-properties.md)  
  
-   [Proprietà di inizializzazione e autorizzazione](../../relational-databases/native-client-ole-db-data-source-objects/initialization-and-authorization-properties.md)  
  
-   [Sessioni](../../relational-databases/native-client-ole-db-data-source-objects/sessions.md)  
  
-   [Proprietà della sessione - Provider OLE DB di SQL Server Native Client](../../relational-databases/native-client-ole-db-data-source-objects/session-properties-sql-server-native-client-ole-db-provider.md)  
  
-   [Oggetti origine dati persistenti](../../relational-databases/native-client-ole-db-data-source-objects/persisted-data-source-objects.md)  
  
## <a name="see-also"></a>Vedere anche  
 [SQL Server Native Client &#40;OLE DB&#41;](../../relational-databases/native-client/ole-db/sql-server-native-client-ole-db.md)  
  
  
