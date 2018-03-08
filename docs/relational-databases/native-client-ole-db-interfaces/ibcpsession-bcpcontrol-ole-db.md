---
title: 'Ibcpsession:: Bcpcontrol (OLE DB) | Documenti Microsoft'
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.service: 
ms.component: native-client-ole-db-interfaces
ms.reviewer: 
ms.suite: sql
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: reference
apiname: IBCPSession::BCPControl (OLE DB)
apitype: COM
helpviewer_keywords: BCPControl method
ms.assetid: d58f3fe1-45e3-4e46-8e9c-000971829d99
caps.latest.revision: "50"
author: MightyPen
ms.author: genemi
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 123232c2815dcb2e7086a58e363a0003d747f80d
ms.sourcegitcommit: a0aa5e611a0e6ebb74ac1e2f613e8916dc7a7617
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/24/2018
---
# <a name="ibcpsessionbcpcontrol-ole-db"></a>IBCPSession::BCPControl (OLE DB)
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]
[!INCLUDE[SNAC_Deprecated](../../includes/snac-deprecated.md)]

  Imposta le opzioni per un'operazione di copia bulk.  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
HRESULT BCPControl(   
      int eOption,  
      void *iValue);  
```  
  
## <a name="remarks"></a>Osservazioni  
 Il **BCPControl** metodo imposta vari parametri di controllo per le operazioni di copia bulk incluso il numero di errori consentiti prima dell'annullamento di una copia di massa, i numeri delle righe e il cognome da copiare da un file di dati e le dimensioni del batch.  
  
 Questo metodo viene inoltre utilizzato per specificare l'istruzione SELECT da utilizzare durante la copia bulk di dati da [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. È possibile impostare il **eOption** argomento BCP_OPTION_HINTS e **iValue** argomento a un puntatore a una stringa di caratteri wide contenente l'istruzione SELECT.  
  
 I valori possibili per *eOption* sono:  
  
|Opzione|Description|  
|------------|-----------------|  
|BCP_OPTION_ABORT|Arresta un'operazione di copia bulk già in corso. È possibile chiamare il **BCPControl** metodo con un *eOption* argomento di BCP_OPTION_ABORT da un altro thread per arrestare un'operazione di copia bulk in esecuzione. Il *iValue* argomento viene ignorato.|  
|BCP_OPTION_BATCH|Numero di righe per batch. L'impostazione predefinita è 0 e indica tutte le righe di una tabella quando i dati vengono estratti oppure tutte le righe nel file di dati dell'utente quando i dati vengono copiati in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Un valore minore di 1 consente di reimpostare BCP_OPTION_BATCH sul valore predefinito.|  
|BCP_OPTION_DELAYREADFMT|Un valore booleano, se impostato su true, causerà [ibcpsession:: Bcpreadfmt](../../relational-databases/native-client-ole-db-interfaces/ibcpsession-bcpreadfmt-ole-db.md) per leggere in esecuzione. Se false (impostazione predefinita), ibcpsession:: Bcpreadfmt verrà immediatamente la lettura del file di formato. Se si verificherà un errore nella sequenza **BCP_OPTION_DELAYREADFMT** è true e si chiama ibcpsession:: BCPColumns o ibcpsession:: BCPColFmt.<br /><br /> Sequenza verificherà un errore anche se si chiama `IBCPSession::BCPControl(BCPDELAYREADFMT, (void *)FALSE))` dopo la chiamata `IBCPSession::BCPControl(BCPDELAYREADFMT, (void *)TRUE)` e ibcpsession:: Bcpwritefmt.<br /><br /> Per ulteriori informazioni, vedere [Metadata Discovery](../../relational-databases/native-client/features/metadata-discovery.md).|  
|BCP_OPTION_FILECP|Il *iValue* argomento contiene il numero della tabella codici per il file di dati. È possibile specificare il numero della tabella codici, ad esempio 1252 o 850, o uno dei valori seguenti:<br /><br /> BCP_FILECP_ACP: i dati contenuti nel file sono inclusi nella tabella codici di Microsoft Windows® del client.<br /><br /> BCP_FILECP_OEMCP: i dati contenuti nel file sono inclusi nella tabella codici OEM del client (impostazione predefinita).<br /><br /> BCP_FILECP_RAW: i dati contenuti nel file sono inclusi nella tabella codici di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].|  
|BCP_OPTION_FILEFMT|Numero di versione del formato del file di dati. Il valore può essere 80 ([!INCLUDE[ssVersion2000](../../includes/ssversion2000-md.md)]), 90 ([!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)]), 100 ([!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] o [!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)]), 110 ([!INCLUDE[ssSQL11](../../includes/sssql11-md.md)]) o 120 ([!INCLUDE[ssSQL14](../../includes/sssql14-md.md)]). 120 è il valore predefinito. Questo valore è utile per l'esportazione e l'importazione di dati in formati supportati da una versione precedente del server.  Ad esempio, per importare i dati ottenuti da una colonna di testo in un [!INCLUDE[ssVersion2000](../../includes/ssversion2000-md.md)] server in un **varchar (max)** colonna in un [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] server o versione successiva, è necessario specificare 80. Analogamente, se si specifica 80 durante l'esportazione di dati da un **varchar (max)** colonna, verrà salvata come colonne di testo vengono salvate nel [!INCLUDE[ssVersion2000](../../includes/ssversion2000-md.md)] formattare e possono essere importati in una colonna di testo di un [!INCLUDE[ssVersion2000](../../includes/ssversion2000-md.md)] server.|  
|BCP_OPTION_FIRST|Prima riga di dati del file o della tabella da copiare. Il valore predefinito è 1. Un valore minore di 1 reimposta l'opzione sul valore predefinito.|  
|BCP_OPTION_FIRSTEX|Per le operazioni BCP out, specifica la prima riga della tabella di database da copiare nel file di dati.<br /><br /> Per le operazioni BCP in, specifica la prima riga del file di dati da copiare nella tabella di database.<br /><br /> Il *iValue* parametro deve essere l'indirizzo di un intero con segno a 64 bit che contiene il valore. Il valore massimo che è possibile passare a BCPFIRSTEX è 2^63-1.|  
|BCP_OPTION_FMTXML|Specifica che il file di formato generato deve essere in formato XML. L'opzione è disattivata per impostazione predefinita e per impostazione predefinita i file di formato vengono salvati come file di testo. I file di formato XML offrono una maggiore flessibilità ma comportano alcuni vincoli aggiuntivi. Diversamente dai file nei formati precedenti, non è ad esempio possibile specificare contemporaneamente il prefisso e il carattere di terminazione per un campo.<br /><br /> Nota: Il file di formato XML sono supportati quando [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] gli strumenti vengono installati insieme a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client.|  
|BCP_OPTION_HINTS|Il *iValue* argomento contiene un puntatore di stringa di caratteri "wide". La stringa a cui viene fatto riferimento specifica hint di elaborazione della copia bulk [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] o un'istruzione [!INCLUDE[tsql](../../includes/tsql-md.md)] che restituisce un set di risultati. Se viene specificata un'istruzione [!INCLUDE[tsql](../../includes/tsql-md.md)] che restituisce più set di risultati, vengono ignorati tutti i set di risultati successivi al primo.|  
|BCP_OPTION_KEEPIDENTITY|Quando il *iValue* argomento è impostato su TRUE, questa opzione specifica che i metodi di copia bulk inseriscono i valori di dati specificati per [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] colonne definite con un vincolo di identità. Il file di input deve fornire valori per le colonne di identità. Se questa impostazione non è disponibile, per le righe inserite vengono generati nuovi valori Identity. Eventuali dati presenti nel file per le colonne di identità vengono ignorati.|  
|BCP_OPTION_KEEPNULLS|Specifica se i valori di dati vuoti nel file verranno convertiti in valori NULL nella tabella di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Quando il *iValue* argomento è impostato su TRUE, i valori vuoti verranno convertiti in valori NULL nella [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] tabella. L'impostazione predefinita prevede che i valori vuoti vengano convertiti in un valore predefinito, se presente, per la colonna nella tabella di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].|  
|BCP_OPTION_LAST|Ultima riga da copiare. L'impostazione predefinita consiste nella copia di tutte le righe. Un valore minore di 1 reimposta l'opzione sul valore predefinito.|  
|BCP_OPTION_LASTEX|Per le operazioni BCP out, specifica l'ultima riga della tabella di database da copiare nel file di dati.<br /><br /> Per le operazioni BCP in, specifica l'ultima riga del file di dati da copiare nella tabella di database.<br /><br /> Il *iValue* parametro deve essere l'indirizzo di un intero con segno a 64 bit che contiene il valore. Il valore massimo che è possibile passare a BCPLASTEX è 2^63-1.|  
|BCP_OPTION_MAXERRS|Numero massimo di errori consentiti prima che l'operazione di copia bulk non riesca. Il valore predefinito è 10. Un valore minore di 1 reimposta l'opzione sul valore predefinito. La copia bulk impone un massimo di 65.535 errori. Il tentativo di impostare questa opzione su un valore maggiore di 65.535 comporta l'impostazione dell'opzione su 65.535.|  
|BCP_OPTION_ROWCOUNT|Restituisce il numero di righe interessate dall'ultima operazione BCP o da quella corrente.|  
|BCP_OPTION_TEXTFILE|Il file di dati non è un file binario, ma è un file di testo. BCP rileva se il file sia o meno Unicode controllando il marcatore di byte Unicode nei primi due byte del file di dati.|  
|BCP_OPTION_UNICODEFILE|Se impostata su TRUE, questa opzione specifica che il file di input utilizza un formato di file Unicode.|  
  
## <a name="arguments"></a>Argomenti  
 *eOption*[in]  
 Impostare questo argomento su una delle opzioni elencate nella sezione precedente contenente le osservazioni.  
  
 *iValue*[in]  
 Il valore per l'oggetto specificato *eOption*. Il *iValue* argomento è un valore integer con cast a un puntatore void per consentire l'espansione futura a valori a 64 bit.  
  
## <a name="return-code-values"></a>Valori restituiti  
 S_OK  
 Il metodo è riuscito.  
  
 E_FAIL  
 Si è verificato un errore specifico del provider; Per informazioni dettagliate, utilizzare il [ISQLServerErrorInfo](http://msdn.microsoft.com/library/a8323b5c-686a-4235-a8d2-bda43617b3a1) interfaccia.  
  
 E_UNEXPECTED  
 La chiamata al metodo non era prevista. Ad esempio, il [ibcpsession:: BCPInit](../../relational-databases/native-client-ole-db-interfaces/ibcpsession-bcpinit-ole-db.md) (metodo) non è stato chiamato prima di chiamare questa funzione.  
  
 E_OUTOFMEMORY  
 Errore di memoria insufficiente.  
  
## <a name="see-also"></a>Vedere anche  
 [OLE DB IBCPSession &#40; &#41;](../../relational-databases/native-client-ole-db-interfaces/ibcpsession-ole-db.md)   
 [Esecuzione di operazioni di copia bulk](../../relational-databases/native-client/features/performing-bulk-copy-operations.md)  
  
  
