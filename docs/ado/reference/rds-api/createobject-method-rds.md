---
title: CreateObject (metodo) (RDS) | Documenti Microsoft
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.service: 
ms.component: ado
ms.technology:
- drivers
ms.custom: 
ms.date: 01/19/2017
ms.reviewer: 
ms.suite: sql
ms.tgt_pltfrm: 
ms.topic: article
apitype: COM
helpviewer_keywords:
- CreateObject method [ADO]
ms.assetid: dec96be6-0b31-4953-9c9a-e962b5afcd18
caps.latest.revision: 
author: MightyPen
ms.author: genemi
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: aeca3cd5d525a3712511a3d7fd59f82210c041e0
ms.sourcegitcommit: acab4bcab1385d645fafe2925130f102e114f122
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/09/2018
---
# <a name="createobject-method-rds"></a>CreateObject (metodo) (RDS)
Crea il proxy per l'oggetto business di destinazione e restituisce un puntatore a esso. I pacchetti ed esegue il marshalling dei dati proxy allo stub sul lato server per le comunicazioni con l'oggetto business per l'invio di richieste e dei dati tramite Internet. Per gli oggetti di componente in-process, non vengono utilizzati proxy, viene fornito solo un puntatore all'oggetto.  
  
> [!IMPORTANT]
>  A partire da Windows 8 e Windows Server 2012, i componenti server di servizi desktop remoto non sono più inclusi nel sistema operativo Windows (vedere Windows 8 e [Guida alla compatibilità tra Windows Server 2012](https://www.microsoft.com/en-us/download/details.aspx?id=27416) per altri dettagli). Componenti client di servizi desktop remoto verranno rimossa in una versione futura di Windows. Evitare di usare questa funzionalità in un nuovo progetto di sviluppo e prevedere interventi di modifica nelle applicazioni in cui è attualmente implementata. Le applicazioni che utilizzano servizi desktop remoto devono eseguire la migrazione a [servizio dati WCF](http://go.microsoft.com/fwlink/?LinkId=199565).  
  
## <a name="syntax"></a>Sintassi  
 Remote Data Service supporta i seguenti protocolli: HTTP, HTTPS (HTTP over Secure Socket Layer), DCOM e in-process.  
  
|Protocollo|Sintassi|  
|--------------|------------|  
|HTTP|Set object = DataSpace.CreateObject("ProgId", "http://awebsrvr")|  
|HTTPS|Set object = DataSpace.CreateObject("ProgId", "https://awebsrvr")|  
|DCOM|Set object = DataSpace.CreateObject("ProgId", "computername")|  
|In-Process|Set object = DataSpace.CreateObject("ProgId", "")|  
  
## <a name="parameters"></a>Parametri  
 *Oggetto*  
 Una variabile oggetto che restituisce un oggetto che rappresenta il tipo specificato in *ProgID*.  
  
 *DataSpace*  
 Una variabile oggetto che rappresenta un [RDS. DataSpace](../../../ado/reference/rds-api/dataspace-object-rds.md) oggetto utilizzato per creare un'istanza del nuovo oggetto.  
  
 *ProgID*  
 Oggetto **stringa** valore che contiene l'identificatore a livello di codice che specifica un oggetto business sul lato server che implementa le regole di business dell'applicazione.  
  
 *awebsrvr* o *computername*  
 Oggetto **stringa** valore che rappresenta un URL di identificazione del server Web Internet Information Services (IIS) in cui viene creata un'istanza dell'oggetto business di server.  
  
## <a name="remarks"></a>Osservazioni  
 Il *protocollo HTTP* è il protocollo Web standard; *HTTPS* è un protocollo Web sicuro. Utilizzare il *protocollo DCOM* durante l'esecuzione di una rete locale senza HTTP. Il *in-process* protocollo è una libreria di collegamento dinamico (DLL) locale, non utilizza una rete.  
  
## <a name="applies-to"></a>Si applica a  
 [Oggetto DataSpace (Servizi Desktop remoto)](../../../ado/reference/rds-api/dataspace-object-rds.md)  
  
## <a name="see-also"></a>Vedere anche  
 [Oggetto DataFactory, metodo di Query ed esempio CreateObject (metodo) (VBScript)](../../../ado/reference/rds-api/datafactory-object-query-method-and-createobject-method-example-vbscript.md)   
 [Oggetto DataSpace e metodo CreateObject (VBScript)](../../../ado/reference/rds-api/dataspace-object-and-createobject-method-example-vbscript.md)   
 [Metodo CreateRecordset (Servizi Desktop remoto)](../../../ado/reference/rds-api/createrecordset-method-rds.md)


