---
title: Esecuzione di operazioni asincrone | Documenti di Microsoft
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- initialization [SQL Server Native Client]
- database connections [SQL Server Native Client]
- data access [SQL Server Native Client], asynchronous operations
- connections [SQL Server Native Client]
- asynchronous operations [SQL Server Native Client]
- rowsets [SQL Server], initializing
- SQLNCLI, asynchronous operations
- SQL Server Native Client, asynchronous operations
ms.assetid: 8fbd84b4-69cb-4708-9f0f-bbdf69029bcc
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 87d961e9613aa390b3001219f88808c8d4ac6ed7
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/02/2018
ms.locfileid: "48110681"
---
# <a name="performing-asynchronous-operations"></a>Esecuzione di operazioni asincrone
  [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] consente alle applicazioni di eseguire operazioni asincrone sul database. L'elaborazione asincrona consente la restituzione immediata dei metodi senza bloccare il thread chiamante. Questa caratteristica offre molto della potenza e della flessibilità del multithreading, senza richiedere allo sviluppatore la creazione esplicita di thread o la gestione della sincronizzazione. Le applicazioni richiedono l'elaborazione asincrona in caso di inizializzazione di una connessione al database o di inizializzazione del risultato dall'esecuzione di un comando.  
  
## <a name="opening-and-closing-a-database-connection"></a>Apertura e chiusura di una connessione al database  
 Quando si usa la [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] provider OLE DB Native Client, le applicazioni progettate per inizializzare in modo asincrono un oggetto origine dati possono impostare il bit DBPROPVAL_ASYNCH_INITIALIZE nella proprietà DBPROP_INIT_ASYNCH prima di chiamare  **IDBInitialize:: Initialize**. Quando questa proprietà è impostata, il provider restituisce immediatamente dalla chiamata a **Initialize** S_OK, se l'operazione è stata completata immediatamente, o DB_S_ASYNCHRONOUS, se l'inizializzazione continua in modo asincrono. Le applicazioni possono eseguire una query per il **IDBAsynchStatus** o [ISSAsynchStatus](../../native-client-ole-db-interfaces/issasynchstatus-ole-db.md)interfaccia sull'oggetto di origine dati e quindi chiamare **IDBAsynchStatus::GetStatus** o[ ISSAsynchStatus::WaitForAsynchCompletion](../../native-client-ole-db-interfaces/issasynchstatus-waitforasynchcompletion-ole-db.md) per ottenere lo stato dell'inizializzazione.  
  
 È stata inoltre aggiunta la proprietà SSPROP_ISSAsynchStatus al set di proprietà DBPROPSET_SQLSERVERROWSET. I provider che supportano l'interfaccia **ISSAsynchStatus** devono implementare questa proprietà con un valore VARIANT_TRUE.  
  
 È possibile chiamare **IDBAsynchStatus::Abort** o [ISSAsynchStatus::Abort](../../native-client-ole-db-interfaces/issasynchstatus-abort-ole-db.md) per annullare la chiamata a **Initialize** asincrona. Il consumer deve richiedere in modo esplicito l'inizializzazione asincrona dell'origine dati. In caso contrario, **IDBInitialize::Initialize** non restituisce nulla fino a quando l'oggetto origine dati non viene inizializzato completamente.  
  
> [!NOTE]  
>  Gli oggetti origine dati utilizzati per il pool di connessioni è possono chiamare il **ISSAsynchStatus** interfaccia nel [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client OLE DB provider. L'interfaccia **ISSAsynchStatus** non è esposta per gli oggetti di origine dati inseriti in pool.  
>   
>  Se un'applicazione forza in modo esplicito l'uso del motore del cursore, **IOpenRowset::OpenRowset** e **IMultipleResults::GetResult** non supporteranno l'elaborazione asincrona.  
>   
>  Inoltre, è possibile chiamare la dll proxy/stub remoto (in MDAC 2.8) di **ISSAsynchStatus** interfaccia nelle [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client. L'interfaccia **ISSAsynchStatus** non è esposta attraverso i servizi remoti.  
>   
>  I componenti del servizio non supportano **ISSAsynchStatus**.  
  
## <a name="execution-and-rowset-initialization"></a>Esecuzione e inizializzazione del set di righe  
 Le applicazioni progettate per aprire in modo asincrono il risultato dall'esecuzione di un comando possono impostare il bit DBPROPVAL_ASYNCH_INITIALIZE nella proprietà DBPROP_ROWSET_ASYNCH. Quando questo bit viene impostato prima di chiamare **IDBInitialize::Initialize**, **ICommand::Execute**, **IOpenRowset::OpenRowset** o **IMultipleResults::GetResult**, l'argomento *riid* deve essere impostato su IID_IDBAsynchStatus, IID_ISSAsynchStatus o IID_IUnknown.  
  
 Il metodo restituisce immediatamente S_OK se l'inizializzazione del set di righe viene completata immediatamente oppure DB_S_ASYNCHRONOUS se il set di righe continua a essere inizializzato in modo asincrono, con *ppRowset* impostato sull'interfaccia richiesta nel set di righe. Per la [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] il provider Client OLE DB nativo, questa interfaccia può essere solo **IDBAsynchStatus** o **ISSAsynchStatus**. Finché il set di righe non è completamente inizializzato, l'interfaccia si comporta come se fosse in stato sospeso e la chiamata a **QueryInterface** per le interfacce diverse da **IID_IDBAsynchStatus** o **IID_ISSAsynchStatus**  può restituire E_NOINTERFACE. A meno che il consumer non richieda in modo esplicito l'elaborazione asincrona, il set di righe viene inizializzato in modo sincrono. Tutte le interfacce richieste sono disponibili quando **IDBAsynchStaus::GetStatus** o **ISSAsynchStatus::WaitForAsynchCompletion** restituisce l'indicazione che l'operazione asincrona è completa. Ciò non significa necessariamente che il set di righe è completamente popolato, ma che è completo e del tutto funzionale.  
  
 Se il comando eseguito non restituisce un set di righe, restituisce comunque immediatamente un oggetto che supporta **IDBAsynchStatus**.  
  
 Se è necessario ottenere più risultati dall'esecuzione di comandi asincrona, effettuare le operazioni seguenti:  
  
-   Impostare il bit DBPROPVAL_ASYNCH_INITIALIZE della proprietà DBPROP_ROWSET_ASYNCH prima di eseguire il comando.  
  
-   Chiamare **ICommand::Execute** e richiedere **IMultipleResults**.  
  
 Le interfacce **IDBAsynchStatus** e **ISSAsynchStatus** possono quindi essere ottenute eseguendo una query sull'interfaccia con più risultati con **QueryInterface**.  
  
 Al termine dell'esecuzione del comando, è possibile usare **IMultipleResults** normalmente, con un'eccezione dal caso sincrono: può essere restituito DB_S_ASYNCHRONOUS. In tal caso, è possibile usare **IDBAsynchStatus** o **ISSAsynchStatus** per determinare il momento in cui l'operazione è completata.  
  
## <a name="examples"></a>Esempi  
 Nell'esempio seguente l'applicazione chiama un metodo non bloccante, esegue altre attività di elaborazione e quindi torna a elaborare i risultati. **ISSAsynchStatus::WaitForAsynchCompletion** resta in attesa dell'oggetto evento interno fino al completamento dell'operazione di esecuzione asincrona o allo scadere della quantità di tempo specificata da *dwMilisecTimeOut*.  
  
```  
// Set the DBPROPVAL_ASYNCH_INITIALIZE bit in the   
// DBPROP_ROWSET_ASYNCH property before calling Execute().  
  
DBPROPSET CmdPropset[1];  
DBPROP CmdProperties[1];  
  
CmdPropset[0].rgProperties = CmdProperties;  
CmdPropset[0].cProperties = 1;  
CmdPropset[0].guidPropertySet = DBPROPSET_ROWSET;  
  
// Set asynch mode for command.  
CmdProperties[0].dwPropertyID = DBPROP_ROWSET_ASYNCH;  
CmdProperties[0].vValue.vt = VT_I4;  
CmdProperties[0].vValue.lVal = DBPROPVAL_ASYNCH_INITIALIZE;  
CmdProperties[0].dwOptions = DBPROPOPTIONS_REQUIRED;  
  
hr = pICommandProps->SetProperties(1, CmdPropset);  
  
hr = pICommand->Execute(  
   pUnkOuter,  
   IID_ISSAsynchStatus,  
   pParams,  
   pcRowsAffected,  
   (IUnknown**)&pISSAsynchStatus);  
  
if (hr == DB_S_ASYNCHRONOUS)  
{  
   // Do some work here...  
  
   hr = pISSAsynchStatus->WaitForAsynchCompletion(dwMilisecTimeOut);  
   if ( hr == S_OK)  
   {  
      hr = pISSAsynchStatus->QueryInterface(IID_IRowset, (void**)&pRowset);  
      pISSAsynchStatus->Release();  
   }  
}  
```  
  
 **ISSAsynchStatus::WaitForAsynchCompletion** resta in attesa dell'oggetto evento interno fino al completamento dell'operazione di esecuzione asincrona o al passaggio del valore *dwMilisecTimeOut*.  
  
 Nell'esempio seguente viene illustrata l'elaborazione asincrona con più set di risultati:  
  
```  
DBPROP CmdProperties[1];  
  
// Set asynch mode for command.  
CmdProperties[0].dwPropertyID = DBPROP_ROWSET_ASYNCH;  
CmdProperties[0].vValue.vt = VT_I4;  
CmdProperties[0].vValue.lVal = DBPROPVAL_ASYNCH_INITIALIZE;  
  
hr = pICommand->Execute(  
   pUnkOuter,  
   IID_IMultipleResults,  
   pParams,  
   pcRowsAffected,  
   (IUnknown**)&pIMultipleResults);  
  
// Use GetResults for ISSAsynchStatus.  
hr = pIMultipleResults->GetResult(IID_ISSAsynchStatus, (void **) &pISSAsynchStatus);  
  
if (hr == DB_S_ASYNCHRONOUS)  
{  
   // Do some work here...  
  
   hr = pISSAsynchStatus->WaitForAsynchCompletion(dwMilisecTimeOut);  
   if (hr == S_OK)  
   {  
      hr = pISSAsynchStatus->QueryInterface(IID_IRowset, (void**)&pRowset);  
      pISSAsynchStatus->Release();  
   }  
}  
```  
  
 Per impedire il blocco, il client può controllare lo stato di un'operazione asincrona in esecuzione, come nell'esempio seguente:  
  
```  
// Set the DBPROPVAL_ASYNCH_INITIALIZE bit in the   
// DBPROP_ROWSET_ASYNCH property before calling Execute().  
hr = pICommand->Execute(  
   pUnkOuter,  
   IID_ISSAsynchStatus,  
   pParams,  
   pcRowsAffected,  
   (IUnknown**)&pISSAsynchStatus);   
  
if (hr == DB_S_ASYNCHRONOUS)  
{  
   do{  
      // Do some work...  
      hr = pISSAsynchStatus->GetStatus(DB_NULL_HCHAPTER, DBASYNCHOP_OPEN, NULL, NULL, &ulAsynchPhase, NULL);  
   }while (DBASYNCHPHASE_COMPLETE != ulAsynchPhase)  
   if SUCCEEDED(hr)  
   {  
      hr = pISSAsynchStatus->QueryInterface(IID_IRowset, (void**)&pRowset);  
   }  
   pIDBAsynchStatus->Release();  
}  
```  
  
 Nell'esempio seguente viene illustrato come annullare l'operazione asincrona attualmente in esecuzione:  
  
```  
// Set the DBPROPVAL_ASYNCH_INITIALIZE bit in the   
// DBPROP_ROWSET_ASYNCH property before calling Execute().  
hr = pICommand->Execute(  
   pUnkOuter,  
   IID_ISSAsynchStatus,  
   pParams,  
   pcRowsAffected,  
   (IUnknown**)&pISSAsynchStatus);  
  
if (hr == DB_S_ASYNCHRONOUS)  
{  
   // Do some work...  
   hr = pISSAsynchStatus->Abort(DB_NULL_HCHAPTER, DBASYNCHOP_OPEN);  
}  
```  
  
## <a name="see-also"></a>Vedere anche  
 [Funzionalità di SQL Server Native Client](sql-server-native-client-features.md)   
 [Proprietà e comportamenti dei set di righe](../../native-client-ole-db-rowsets/rowset-properties-and-behaviors.md)   
 [ISSAsynchStatus &#40;OLE DB&#41;](../../native-client-ole-db-interfaces/issasynchstatus-ole-db.md)  
  
  
